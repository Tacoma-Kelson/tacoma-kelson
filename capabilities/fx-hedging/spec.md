# FX Hedging Model Specification: Seed Genetics

## 1. Problem Statement
The company expects to receive EUR 7.3 million from a French grain cooperative in 273 days. Because the company reports in U.S. dollars, it is exposed to the risk that the euro could weaken before the payment is received. The model will compare an unhedged position with three hedge alternatives: a forward hedge, a money-market hedge, and a put option on EUR. The goal is to compare the USD proceeds under each strategy and determine how each hedge performs under different EURUSD exchange-rate scenarios.

## 2. Inputs: Named-Range Contract

All inputs below are indicative placeholders and will be replaced with live market data at Stage 4.

| Named Range | Placeholder Value | Unit | Stage 4 Source |
|---|---:|---|---|
| `FC_AMT` | 7,300,000 | EUR | Assigned scenario / confirmed receivable |
| `S0_in` | TBD | USD per EUR | Current EURUSD spot market quote |
| `F0_in` | 1.1756 | USD per EUR | Assigned scenario / updated market quote |
| `R_USD` | TBD | Annual % | Current USD market interest rate |
| `R_FC` | TBD | Annual % | Current EUR market interest rate |
| `K_PUT` | Equal to `S0_in` | USD per EUR | Set at the Stage 4 EURUSD spot rate |
| `K_CALL` | Equal to `S0_in` | USD per EUR | Set at the Stage 4 EURUSD spot rate |
| `PREM_PUT` | 0.0224 | USD per EUR | Assigned scenario / updated option quote |
| `PREM_CALL` | 0.0376 | USD per EUR | Assigned scenario / updated option quote |
| `T_DAYS` | 273 | Days | Assigned scenario / settlement date |

## 3. Tab Architecture

The workbook will use the following tabs:

### Cover
Identifies the FX hedging model, the seed-genetics scenario, the purpose of the workbook, and the date of the analysis.

### Legend / Key
Explains the workbook formatting and identifies which cells are inputs, formulas, outputs, assumptions, and validation checks.

### Inputs
Contains all 10 required named ranges and their values, units, and sources. Scenario and market inputs will be clearly identified. Market-based placeholders will be labeled as indicative and replaced with live market data in Stage 4.

### Forward Hedge
Calculates the locked USD proceeds from selling the EUR 7.3 million receivable forward using `F0_in`.

### Money-Market Hedge
Shows the three-step borrow-convert-invest process. It will calculate the EUR borrowing amount, convert it to USD using `S0_in`, and invest the USD amount through settlement using `R_USD`.

### Option Hedge
Calculates the put option floor and option payoff across settlement exchange rates. It will show the premium separately and calculate net USD proceeds after the premium.

### Sensitivity
Tests the hedge alternatives across different EURUSD settlement spot rates and includes a comparison chart showing how USD proceeds change under each strategy.

### Summary
Presents the key USD proceeds and trade-offs of the unhedged position and each hedge strategy in one place.

### Notes & Assumptions
Documents the model assumptions, ACT/360 rate basis, treatment of option premiums and transaction costs, placeholder market data, and other modeling limitations.

## 4. Assumptions & Constraints

- The company will receive the full EUR 7.3 million in 273 days.
- The exposure is a EUR receivable, so the primary currency risk is the euro weakening against the U.S. dollar.
- USD and EUR interest rates will use an ACT/360 basis. The 273-day period will therefore be calculated as `T_DAYS / 360`.
- The forward hedge will cover the full EUR 7.3 million receivable.
- The money-market hedge assumes the company can borrow EUR and invest USD at the rates entered in the model.
- Covered interest rate parity is expected to make the forward hedge and money-market hedge produce approximately the same USD proceeds, subject to rounding and market quote differences.
- The put option will cover the full EUR 7.3 million exposure and use a strike at the EURUSD spot rate.
- Put and call premiums are paid upfront. The model will show the premiums separately and include the put premium when calculating net proceeds from the protective option hedge.
- Transaction costs, taxes, bid-ask spreads, and counterparty risk are excluded from the model.
- Market-based inputs are indicative placeholders during the model design and build stages and will be replaced with sourced and timestamped live market data in Stage 4.

## 5. Calculation Flow

The model will calculate the USD outcome for the unhedged position and each hedge alternative using the same EUR 7.3 million exposure.

### Unhedged Position
1. Enter a possible EURUSD spot rate at the 273-day settlement date.
2. Multiply `FC_AMT` by the settlement spot rate.
3. The result is the USD value of the receivable with no hedge.

**Formula:**  
`Unhedged USD Proceeds = FC_AMT × Settlement Spot Rate`

### Forward Hedge
1. Use the forward rate `F0_in`.
2. Multiply `FC_AMT` by `F0_in`.
3. The resulting USD proceeds are fixed regardless of the settlement spot rate.

**Formula:**  
`Forward USD Proceeds = FC_AMT × F0_in`

### Money-Market Hedge
1. Calculate the present value of the EUR 7.3 million receivable using `R_FC` and `T_DAYS`.
2. Borrow that amount of EUR today.
3. Convert the borrowed EUR to USD using `S0_in`.
4. Invest the USD proceeds using `R_USD` for the remaining `T_DAYS`.
5. At maturity, use the EUR 7.3 million receivable to repay the EUR borrowing.
6. The future value of the USD investment is the USD proceeds from the money-market hedge.

**Formulas:**  
`EUR Present Value = FC_AMT / (1 + R_FC × T_DAYS / 360)`  
`USD Invested Today = EUR Present Value × S0_in`  
`Money-Market USD Proceeds = USD Invested Today × (1 + R_USD × T_DAYS / 360)`

### Put Option Hedge
1. Calculate the total put premium as `FC_AMT × PREM_PUT`.
2. At settlement, compare the EURUSD spot rate with `K_PUT`.
3. If the settlement spot rate is below `K_PUT`, exercise the put and value the receivable at `K_PUT`.
4. If the settlement spot rate is above `K_PUT`, allow the put to expire and convert the receivable at the stronger market spot rate.
5. Subtract the cost of the put premium when comparing the option with the other strategies.

### Call Option Participation
The model will also calculate the payoff of a call option on EUR for comparison and validation purposes.

1. Calculate the total call premium as `FC_AMT × PREM_CALL`.
2. At settlement, compare the EURUSD settlement spot rate with `K_CALL`.
3. The call payoff per EUR is the greater of the settlement spot rate minus `K_CALL` or zero.
4. Multiply the payoff per EUR by `FC_AMT` to calculate the total call payoff.
5. Show the call premium separately so the cost of participation can be compared with the payoff.

**Formulas:**  
`Call Premium = FC_AMT × PREM_CALL`  
`Call Payoff = FC_AMT × MAX(Settlement Spot Rate - K_CALL, 0)`

## 6. Sensitivity Plan

The model will test how each strategy performs as the EURUSD settlement spot rate changes. The sensitivity analysis will range from 5% below `S0_in` to 5% above `S0_in` in 1% increments.

The settlement spot-rate scenarios will be:

- 5% below `S0_in`
- 4% below `S0_in`
- 3% below `S0_in`
- 2% below `S0_in`
- 1% below `S0_in`
- Equal to `S0_in`
- 1% above `S0_in`
- 2% above `S0_in`
- 3% above `S0_in`
- 4% above `S0_in`
- 5% above `S0_in`

For each settlement rate, the model will calculate the USD proceeds for the unhedged position, forward hedge, money-market hedge, and option hedge. The Sensitivity tab will also include a chart comparing the strategies across the full range of settlement rates. This will show the downside protection and upside participation provided by each strategy.

## 7. Validation Rules

The completed workbook must pass the following checks before the results are used:

1. **Exposure check:** `FC_AMT` must equal EUR 7,300,000 and `T_DAYS` must equal 273 days.
2. **Forward check:** Forward USD proceeds must equal `FC_AMT × F0_in`. Using the assigned indicative forward rate of 1.1756, the placeholder result should equal $8,581,880.
3. **Option premium check:** The put premium must equal `FC_AMT × PREM_PUT`. Using the assigned premium of $0.0224 per EUR, the total premium should equal $163,520.
4. **Put floor check:** When the settlement spot rate falls below `K_PUT`, the put hedge must use `K_PUT` rather than the lower settlement spot rate.
5. **Put upside check:** When the settlement spot rate rises above `K_PUT`, the option must expire unexercised and the model must use the higher settlement spot rate.
6. **Forward stability check:** Forward USD proceeds must remain unchanged across all settlement spot-rate sensitivity scenarios.
7. **Money-market repayment check:** The EUR amount borrowed today plus the interest accrued over `T_DAYS` must equal the EUR 7,300,000 receivable at maturity.
8. **Sensitivity check:** A weaker euro must reduce unhedged USD proceeds, while a stronger euro must increase unhedged USD proceeds.
9. **Input check:** Market inputs must be linked to the named ranges rather than hard-coded inside calculation formulas.
10. **Error check:** The workbook must contain no formula errors such as `#REF!`, `#VALUE!`, `#DIV/0!`, or `#NAME?`.
11. **Parity check:** Compare the assigned forward rate `F0_in` with the forward rate implied by the spot rate and the USD and EUR interest rates. The model will calculate the implied forward rate using covered interest parity and flag any meaningful difference between the implied rate and `F0_in`.
12. **Forward vs. money-market parity check:** When the forward rate is consistent with covered interest rate parity, the forward hedge and money-market hedge should produce approximately the same USD proceeds. Any difference beyond normal rounding should be flagged for review.

**Formula:**  
`Implied Forward Rate = S0_in × (1 + R_USD × T_DAYS / 360) / (1 + R_FC × T_DAYS / 360)`

## 8. Outputs

The model will produce a clear comparison of the unhedged position, forward hedge, money-market hedge, and put option hedge. It will also report the call option participation payoff for comparison and validation.

The Summary tab will display:

- USD proceeds for each strategy
- Total put option premium
- Difference in USD proceeds between each hedge and the unhedged position
- Put and call option premiums and option payoff results
- Results across the settlement spot-rate sensitivity scenarios
- Downside protection provided by each hedge
- Upside participation available under each strategy

The final outputs should make it easy to compare the certainty, cost, downside protection, and upside potential of each strategy. These results will support the independent validation and final hedging recommendation in Stage 5.
