Independent FX Hedging Analysis: Seed Genetics
Scenario 32 | Market data as of November 16, 2026

This analysis uses only the two attached documents:
- FX Hedging Model Specification (spec.md)
- Stage 4 Market Data Memo (2026-11-16-seed-genetics-market-data-memo.md)
The calculations use the updated market inputs from the Stage 4 memo and the formulas, assumptions, and validation rules established in the model specification. The reported hedge results in the memo are used only for comparison after independently calculating the outcomes.
1. Inputs and assumptions
The company expects to receive EUR 7.3 million from a French grain cooperative in 273 days. Since the company reports in U.S. dollars, its primary exposure is the risk of the euro depreciating against the dollar before settlement.
Input	Variable	Value
EUR receivable	FC_AMT	€7,300,000
Current EUR/USD spot rate	S₀	1.1014
Assigned forward rate	F₀	1.1756
Annual USD interest rate	R_USD	3.82858%
Annual EUR interest rate	R_FC	2.437%
Put strike price	K_PUT	1.1014
Call strike price	K_CALL	1.1014
Put premium per EUR	PREM_PUT	$0.0224
Call premium per EUR	PREM_CALL	$0.0376
Days until settlement	T_DAYS	273
Day-count convention	ACT/360	360 days

The updated spot and interest rates come from the market-data memo. The exposure, forward rate, option premiums, and calculation conventions come from the original specification. spec.md
2026-11-16-seed-genetics-market-data-memo.md


Important assumption: The updated option strike prices are not explicitly listed in the Stage 4 memo. I assume both strikes are reset to the updated spot rate of 1.1014, consistent with the specification's at-the-money option design. This assumption should be confirmed against the actual workbook.
Preliminary calculations
Time to settlement:
\[
t=\frac{273}{360}=0.758333333
\]

USD interest accumulation factor:
\[
1+R_{USD}t
\]

\[
=1+0.0382858\left(\frac{273}{360}\right)
\]

\[
=1.0290333983
\]

EUR interest accumulation factor:
\[
1+R_{FC}t
\]

\[
=1+0.02437\left(\frac{273}{360}\right)
\]

\[
=1.0184805833
\]

All intermediate calculations retain full precision before rounding final USD amounts to two decimal places.
2. Unhedged position
Under the unhedged strategy, the company waits until settlement and converts the entire EUR receivable into USD at the prevailing exchange rate.

Formula:
\[
U=FC_{AMT}\times S_T
\]

Since the actual future settlement rate is unknown, the base case assumes the settlement rate equals the current spot rate of 1.1014.

Calculation:
\[
U=7,300,000\times1.1014
\]

\[
\boxed{U=\$8,040,220.00}
\]

The company remains fully exposed to exchange-rate fluctuations. Every 1% change in the euro relative to the current spot rate changes the USD proceeds by $80,402.20.
3. Forward hedge
The company enters a forward contract to sell EUR 7.3 million in 273 days at the assigned forward rate of 1.1756 USD per EUR.

Formula:
\[
F=FC_{AMT}\times F_0
\]

Calculation:
\[
F=7,300,000\times1.1756
\]

\[
\boxed{F=\$8,581,880.00}
\]

Additional proceeds compared with the unhedged base case:
\[
8,581,880-8,040,220
\]

\[
=\$541,660.00
\]

The forward hedge eliminates exchange-rate uncertainty but prevents the company from benefiting if the euro appreciates beyond the contracted forward rate.

The assigned forward rate is retained from the original scenario rather than obtained from a current executable market quote.
4. Money-market hedge
The money-market hedge involves borrowing EUR today, converting the borrowed funds into USD, and investing the USD until the receivable is collected.
Step 1: Calculate the present value of the EUR receivable
Formula:
\[
PV_{EUR}=\frac{FC_{AMT}}{1+R_{FC}t}
\]

Calculation:
\[
PV_{EUR}=
\frac{7,300,000}
{1+0.02437(273/360)}
\]

\[
=\frac{7,300,000}{1.0184805833}
\]

\[
=\text{€}7,167,539.69
\]

The company borrows approximately €7,167,539.69 today.
Step 2: Convert the borrowed EUR into USD
Formula:
\[
USD_{Today}=PV_{EUR}\times S_0
\]

Calculation:
\[
=7,167,539.685546\times1.1014
\]

\[
=\$7,894,328.21
\]

Step 3: Invest the USD proceeds for 273 days
Formula:
\[
MM=USD_{Today}(1+R_{USD}t)
\]

Calculation:
\[
=7,894,328.209661
\left(1+0.0382858\frac{273}{360}\right)
\]

\[
=7,894,328.209661\times1.0290333983
\]

\[
\boxed{MM=\$8,123,527.39}
\]

Step 4: Verify repayment of the EUR loan
\[
7,167,539.685546\times1.0184805833
\]

\[
=\text{€}7,300,000.00
\]

The EUR receivable exactly covers the principal and accrued interest on the EUR loan at settlement.
Money-market hedge cash flowToday

In 273 days

Borrow EUR€7,167,539.69


Convert and invest USD$7,894,328.21


Receive EUR payment€7,300,000.00


Repay EUR loan€7,300,000.00




Final USD investment value at settlement$8,123,527.39

Additional proceeds compared with the unhedged base case:
\[
8,123,527.39-8,040,220
\]

\[
=\$83,307.39
\]

This hedge eliminates exchange-rate risk under the assumption that the company can borrow and invest at the specified interest rates. The calculation follows the borrow-convert-invest process established in the model specification. spec.md

5. Protective put option
A put option gives the company the right, but not the obligation, to sell EUR at the strike price of 1.1014 USD per EUR.

This protects the company against euro depreciation while allowing it to benefit from euro appreciation.
Step 1: Calculate the upfront put premium
Formula:
\[
P_{Put,0}=FC_{AMT}\times PREM_{PUT}
\]

Calculation:
\[
=7,300,000\times0.0224
\]

\[
=\$163,520.00
\]

Step 2: Carry the premium forward to settlement
Formula:
\[
P_{Put,T}=P_{Put,0}(1+R_{USD}t)
\]

Calculation:
\[
=163,520\times1.0290333983
\]

\[
=\$168,267.54
\]

The opportunity cost of paying the premium upfront is:
\[
168,267.54-163,520
=\$4,747.54
\]

Step 3: Calculate the protective put proceeds
Formula:
\[
Put=FC_{AMT}\times\max(S_T,K_{PUT})-P_{Put,T}
\]

At the base-case settlement rate of 1.1014:
\[
=7,300,000\times\max(1.1014,1.1014)
\]

\[
-168,267.541295
\]

\[
=8,040,220-168,267.541295
\]

\[
\boxed{Put=\$7,871,952.46}
\]

Step 4: Determine the minimum protected proceeds
The minimum net USD proceeds are:
\[
7,300,000\times1.1014-168,267.54
\]

\[
=\$7,871,952.46
\]

The effective protected exchange rate after accounting for the premium is:
\[
\frac{7,871,952.46}{7,300,000}
\]

\[
=1.07834965\text{ USD/EUR}
\]

The company receives at least $7,871,952.46 regardless of how far the euro depreciates, assuming the option contract is honored and the full receivable is collected.

The premium is carried forward because the specification requires all costs and proceeds to be compared at settlement. spec.md

6. Call option participation
A purchased call option on EUR gives the company the right to buy EUR at the strike price. Unlike a protective put, a purchased call does not directly protect a EUR receivable against depreciation.

The specification includes the call for participation analysis and validation rather than as a primary hedging strategy. spec.md

Step 1: Calculate the upfront call premium
Formula:
\[
P_{Call,0}=FC_{AMT}\times PREM_{CALL}
\]

Calculation:
\[
=7,300,000\times0.0376
\]

\[
=\$274,480.00
\]

Step 2: Carry the call premium forward to settlement
\[
P_{Call,T}=P_{Call,0}(1+R_{USD}t)
\]

\[
=274,480\times1.0290333983
\]

\[
=\$282,449.09
\]

Step 3: Calculate the gross call payoff
Formula:
\[
Call_{Gross}=FC_{AMT}\times\max(S_T-K_{CALL},0)
\]

At the base-case settlement rate:
\[
=7,300,000\times\max(1.1014-1.1014,0)
\]

\[
=\$0.00
\]

Step 4: Calculate the net call payoff
Formula:
\[
Call_{Net}=Call_{Gross}-P_{Call,T}
\]

\[
=0-282,449.09
\]

\[
\boxed{Call_{Net}=-\$282,449.09}
\]

If the company holds both the unhedged receivable and the purchased call, its combined base-case proceeds would be:
\[
8,040,220-282,449.09
\]

\[
=\$7,757,770.91
\]

However, this combined position increases exposure to euro appreciation rather than protecting against depreciation.
Call option break-even exchange rate
\[
S_{BE}=K_{CALL}+\frac{P_{Call,T}}{FC_{AMT}}
\]

\[
=1.1014+\frac{282,449.087175}{7,300,000}
\]

\[
=\boxed{1.14009166}
\]

The euro must appreciate approximately 3.51% from the current spot rate for the standalone call option to generate a positive net payoff.
7. Base-case results comparison
Assuming the settlement exchange rate remains at 1.1014:
USD proceeds at settlementForward hedge

$8,581,880.00




Money-market hedge

$8,123,527.39




Unhedged

$8,040,220.00




Protective put

$7,871,952.46




Receivable + purchased call

$7,757,770.91





Strategy	USD proceeds	Difference vs. unhedged
Unhedged	$8,040,220.00	$0.00
Forward hedge	$8,581,880.00	+$541,660.00
Money-market hedge	$8,123,527.39	+$83,307.39
Protective put	$7,871,952.46	−$168,267.54
Receivable + purchased call	$7,757,770.91	−$282,449.09

The forward hedge produces the highest base-case proceeds using the assigned inputs.
8. Sensitivity analysis: −5% to +5%
The settlement exchange rates are calculated using:
\[
S_T=S_0(1+\Delta)
\]

Where \(\Delta\) represents the percentage change in EUR/USD from the current spot rate.

For example, under the −5% scenario:
\[
S_T=1.1014(1-0.05)=1.046330
\]

Under the +5% scenario:
\[
S_T=1.1014(1+0.05)=1.156470
\]

The forward and money-market hedge proceeds remain constant because their exchange-rate exposure has been eliminated under the model assumptions.
Primary hedging strategies
All proceeds are expressed in USD.
Change	Settlement rate	Unhedged	Forward	Money market	Protective put
−5%	1.046330	7,638,209.00	8,581,880.00	8,123,527.39	7,871,952.46
−4%	1.057344	7,718,611.20	8,581,880.00	8,123,527.39	7,871,952.46
−3%	1.068358	7,799,013.40	8,581,880.00	8,123,527.39	7,871,952.46
−2%	1.079372	7,879,415.60	8,581,880.00	8,123,527.39	7,871,952.46
−1%	1.090386	7,959,817.80	8,581,880.00	8,123,527.39	7,871,952.46
0%	1.101400	8,040,220.00	8,581,880.00	8,123,527.39	7,871,952.46
+1%	1.112414	8,120,622.20	8,581,880.00	8,123,527.39	7,952,354.66
+2%	1.123428	8,201,024.40	8,581,880.00	8,123,527.39	8,032,756.86
+3%	1.134442	8,281,426.60	8,581,880.00	8,123,527.39	8,113,159.06
+4%	1.145456	8,361,828.80	8,581,880.00	8,123,527.39	8,193,561.26
+5%	1.156470	8,442,231.00	8,581,880.00	8,123,527.39	8,273,963.46

Sensitivity comparison chart

UnhedgedForwardMoney marketProtective put

$7.5M$7.8M$8.1M$8.4M$8.7M−5%−4%−3%−2%−1%0%+1%+2%+3%+4%+5%















Call option sensitivity
The call option is presented separately because its standalone payoff is not directly comparable to the total receivable proceeds from the other strategies.
Change	Settlement rate	Gross call payoff	Net call payoff
−5%	1.046330	$0.00	−$282,449.09
−4%	1.057344	$0.00	−$282,449.09
−3%	1.068358	$0.00	−$282,449.09
−2%	1.079372	$0.00	−$282,449.09
−1%	1.090386	$0.00	−$282,449.09
0%	1.101400	$0.00	−$282,449.09
+1%	1.112414	$80,402.20	−$202,046.89
+2%	1.123428	$160,804.40	−$121,644.69
+3%	1.134442	$241,206.60	−$41,242.49
+4%	1.145456	$321,608.80	$39,159.71
+5%	1.156470	$402,011.00	$119,561.91

Sensitivity findings
- Forward hedge: Produces the highest proceeds among the four primary strategies in all 11 scenarios.
- Money-market hedge: Maintains fixed proceeds of $8,123,527.39 regardless of the settlement exchange rate.
- Protective put: Establishes a minimum net value of $7,871,952.46 while allowing upside participation above the strike price.
- Unhedged position: Has the greatest downside exposure among the four primary strategies, with proceeds ranging from $7,638,209.00 to $8,442,231.00.
- Call option: Generates a positive standalone net payoff only in the +4% and +5% scenarios within the tested range.
Interactive sensitivity calculator
The following calculator uses the independently calculated formulas and allows additional exchange-rate scenarios to be tested beyond the required range.
Change in EUR/USD
0.0%

−15%
−5%
0%
+5%
+15%




Settlement exchange rate (USD/EUR)1.101400


Unhedged

$8,040,220.00




Forward hedge

$8,581,880.00




Money-market hedge

$8,123,527.39




Protective put

$7,871,952.46





Gross call payoff

$0.00

Net call payoff

-$282,449.09

Reset to base case
9. Covered interest rate parity check
Covered interest rate parity (CIP) establishes the theoretical relationship between the spot exchange rate, forward exchange rate, and interest rates in the two currencies.

Under consistent market inputs, the forward hedge and money-market hedge should produce approximately equal proceeds.
Step 1: Calculate the implied forward rate
Formula:
\[
F_{CIP}=S_0
\frac{1+R_{USD}t}{1+R_{FC}t}
\]

Calculation:
\[
F_{CIP}=1.1014
\frac{1+0.0382858(273/360)}
{1+0.02437(273/360)}
\]

\[
=1.1014
\frac{1.0290333983}{1.0184805833}
\]

\[
\boxed{F_{CIP}=1.11281197}
\]

Step 2: Compare the implied and assigned forward rates
\[
Difference=|F_0-F_{CIP}|
\]

\[
=|1.1756-1.1128119706|
\]

\[
=\boxed{0.06278803}
\]

The difference in pips is:
\[
\frac{0.06278803}{0.0001}
=627.88\text{ pips}
\]

The model specification establishes a maximum tolerance of 0.0010 USD per EUR, equivalent to 10 pips. spec.md

Covered interest rate parity

FAIL

Assigned forward rate1.175600

Implied forward rate1.112812

Actual difference627.88 pips

Permitted difference10 pips


Difference relative to permitted tolerance

10-pip tolerance
627.88-pip difference

The difference is approximately 62.79 times the permitted tolerance.
Step 3: Compare forward and money-market proceeds
\[
Difference=F-MM
\]

\[
=8,581,880-8,123,527.385146
\]

\[
=\boxed{\$458,352.61}
\]

This difference is too large to be attributed to ordinary rounding.
Step 4: Recalculate forward proceeds using the parity-implied rate
\[
F_{Adjusted}=FC_{AMT}\times F_{CIP}
\]

\[
=7,300,000\times1.112811970568
\]

\[
=\boxed{\$8,123,527.39}
\]

This exactly matches the money-market hedge proceeds when calculated using full precision.
Parity validation	Result	Status
Assigned vs. implied forward rate	0.06278803 difference	FAIL
Assigned forward vs. money-market proceeds	$458,352.61 difference	FAIL
Implied forward vs. money-market proceeds	$0.00 difference	PASS

Interpretation
The parity failure is caused by inconsistent market inputs within the model. The assigned forward rate is substantially higher than the theoretical rate implied by the updated spot and interest rates.

The independent calculations demonstrate that the money-market and forward formulas are mathematically consistent when the parity-implied forward rate is used.

However, this does not establish that a real-world arbitrage opportunity exists because the forward rate is assigned and the interest rates are benchmark proxies rather than executable quotes.
10. Additional break-even analysis
Unhedged position versus forward hedge
The unhedged position produces the same proceeds as the forward hedge when:
\[
7,300,000S_T=8,581,880
\]

\[
S_T=1.1756
\]

Required euro appreciation:
\[
\left(\frac{1.1756}{1.1014}-1\right)\times100
\]

\[
=6.74\%
\]

Protective put versus forward hedge
Above the put strike, the protective put matches the forward hedge when:
\[
7,300,000S_T-168,267.54=8,581,880
\]

\[
S_T=\frac{8,581,880+168,267.54}{7,300,000}
\]

\[
S_T=1.19865035
\]

Required euro appreciation:
\[
\left(\frac{1.19865035}{1.1014}-1\right)\times100
\]

\[
=8.83\%
\]

Break-even summary
Comparison	Settlement rate	Change from current spot
Protective put equals unhedged proceeds on downside	1.078350	−2.09%
Unhedged equals money-market hedge	1.112812	+1.04%
Protective put equals money-market hedge	1.135862	+3.13%
Call option earns zero net profit	1.140092	+3.51%
Unhedged equals assigned forward hedge	1.175600	+6.74%
Protective put equals assigned forward hedge	1.198650	+8.83%

These break-even calculations explain why the assigned forward hedge outperforms the other three primary strategies throughout the required sensitivity range.
11. Independent comparison with the market-data memo
After completing the calculations independently, the results can be compared with the reported figures in the Stage 4 memo. 2026-11-16-seed-genetics-market-data-memo.md

Calculation	Independent result	Memo result	Difference
Unhedged	$8,040,220.00	$8,040,220.00	$0.00
Forward hedge	$8,581,880.00	$8,581,880.00	$0.00
Money-market hedge	$8,123,527.39	$8,123,527.39	$0.00
Protective put	$7,871,952.46	$7,871,952.46	$0.00
Put premium at settlement	$168,267.54	$168,267.54	$0.00
Implied forward rate	1.11281	1.11281	0.00000
Forward rate difference	0.06279	0.06279	0.00000

All reported numerical hedge outcomes match the independent calculations at the precision presented in the memo.
Protective put premium discrepancy with the FX Hedging Lab
The memo identifies a difference between the workbook and the professor's FX Hedging Lab regarding the treatment of the option premium.

If the upfront premium is subtracted without adjusting for the time value of money:
\[
8,040,220-163,520=\$7,876,700.00
\]

If the premium is carried forward to settlement:
\[
8,040,220-168,267.54=\$7,871,952.46
\]

Difference:
\[
7,876,700-7,871,952.46
\]

\[
=\boxed{\$4,747.54}
\]

The discrepancy is independently reproduced and is consistent with the explanation provided in the memo. The settlement-value approach is appropriate under the model specification because all proceeds and costs are evaluated at the same point in time.

The actual FX Hedging Lab was not accessed because this analysis is restricted to the two attached documents.
12. Independent validation results
Validation check	Status
Exposure amount and settlement period	PASS
Forward proceeds calculation	PASS
Upfront put premium calculation	PASS
Put downside floor	PASS
Put upside participation	PASS
Forward stability across scenarios	PASS
Money-market loan repayment	PASS
Sensitivity analysis behavior	PASS
Workbook named-range references	Not verifiable
Workbook formula errors	Not verifiable
Covered interest rate parity	FAIL
Forward vs. money-market parity	FAIL

Passed8


Failed2


Not verifiable2



The specification lists 12 validation rules, while the memo reports nine passed checks and two parity flags. The documents do not explain the difference in the number of checks.

Because the actual Excel workbook was not provided, named-range references and spreadsheet formula errors cannot be independently verified. It would therefore be inappropriate to certify that all workbook formulas are functioning correctly.
13. Missing information and assumptions
The following limitations should be considered before implementing a hedging strategy.
Missing information or assumption	Impact on the analysis
Executable 273-day forward quote	The assigned forward rate of 1.1756 may not be available in the actual market.
Actual 273-day EUR borrowing rate	The €STR benchmark does not necessarily represent the company's borrowing cost.
Actual 273-day USD investment rate	The 90-day average SOFR does not guarantee the return available over 273 days.
Executable spot exchange rate	The ECB reference rate excludes actual dealer pricing and spreads.
Updated option strike prices	Both strikes are assumed to equal the updated spot rate of 1.1014.
Updated option premiums	The assigned premiums are retained without confirmation that they reflect current market conditions or updated strikes.
Transaction costs and taxes	Excluded from all calculations. Actual net proceeds could be lower.
Counterparty and credit risk	The analysis assumes all parties fulfill their contractual obligations.
Borrowing capacity	The money-market hedge assumes the company can borrow approximately €7.17 million at the specified rate.
Receivable certainty	The full €7.3 million is assumed to arrive on schedule.
Future settlement spot rate	Unknown. The current spot rate is used only as the base-case assumption.
Option contract terms	Exact exercise style, expiration terms, and settlement mechanics are not provided.
Company risk tolerance	The documents do not specify how much exchange-rate risk the company is willing to retain.

An additional assumption is that simple interest using ACT/360 applies consistently to both currencies and to the future value of the option premiums.

The model specification explicitly excludes transaction costs, taxes, bid-ask spreads, and counterparty risk. The market-data memo also acknowledges that the interest rates and spot rate are reference inputs rather than executable prices. spec.md
2026-11-16-seed-genetics-market-data-memo.md

14. Recommended hedging strategy
I recommend the forward hedge for the seed-genetics scenario, conditional on verifying the availability of the assigned forward rate.

Based on the independent calculations, the forward hedge provides:
- Guaranteed modeled proceeds of $8,581,880.00.
- $541,660.00 more than the unhedged base-case proceeds.
- $458,352.61 more than the money-market hedge.
- The highest proceeds among the four primary strategies across all 11 sensitivity scenarios.
- Full protection against euro depreciation without the upfront option premium.
However, the covered interest rate parity failure is a significant limitation. The assigned forward rate of 1.1756 exceeds the parity-implied rate of 1.11281197 by approximately 627.88 pips.

If the company can actually secure the assigned forward rate, the forward hedge would be the preferred strategy under the tested scenarios. If that rate is unavailable and executable forward pricing is closer to the parity-implied rate, the forward hedge and money-market hedge would provide approximately equal proceeds before transaction costs.

In that situation, the forward hedge may still be preferable because it avoids the borrowing, currency conversion, and investment requirements of the money-market hedge.

The protective put would be an appropriate alternative if management prioritizes maintaining upside participation and is willing to pay the option premium. The purchased call option is not recommended as a standalone hedge because it does not protect the company's EUR receivable against depreciation.
15. Conclusion
The independent analysis successfully reproduces all reported numerical hedge outcomes in the Stage 4 market-data memo. It also confirms the protective put premium discrepancy and both covered interest rate parity flags.

The final independently calculated results are:
Output	Final result
Unhedged base-case proceeds	$8,040,220.00
Forward hedge proceeds	$8,581,880.00
Money-market hedge proceeds	$8,123,527.39
Protective put proceeds	$7,871,952.46
Upfront put premium	$163,520.00
Put premium at settlement	$168,267.54
Upfront call premium	$274,480.00
Call premium at settlement	$282,449.09
Base-case gross call payoff	$0.00
Base-case net call payoff	−$282,449.09
Parity-implied forward rate	1.11281197
Forward rate discrepancy	0.06278803
Forward vs. money-market discrepancy	$458,352.61
Interest rate parity check	FAIL
Recommended strategy	Forward hedge, subject to quote verification

The calculations support the forward hedge as the strongest strategy under the assigned scenario inputs. Nevertheless, the recommendation remains conditional because the assigned forward rate and benchmark interest rates do not represent a consistent set of executable market prices.

No outside sources were used. The numerical results were independently calculated from the two supplied documents rather than copied from the market-data memo.
