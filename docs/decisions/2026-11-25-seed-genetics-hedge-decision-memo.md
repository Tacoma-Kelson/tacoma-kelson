# FX Hedging Decision Memo: Seed Genetics

**To:** Chief Financial Officer  
**From:** Tacoma Kelson, Financial Analyst  
**Date:** November 25, 2026  
**Subject:** Foreign Exchange Hedging Recommendation

## A. Exposure Summary

Our company expects to receive EUR 7.3 million from a French grain cooperative in 273 days. Since the company reports its financial results in U.S. dollars, we are exposed to the risk of the euro depreciating before the payment is received. A weaker euro would reduce the amount of U.S. dollars we receive and could negatively affect our cash flow and financial planning.

Using the November 16 market inputs in my model, the current EUR/USD spot rate is 1.1014. At this rate, the receivable is worth approximately $8.04 million. However, this amount is not guaranteed unless the company takes steps to hedge its exposure.

The objective of this analysis is to determine which hedging strategy provides the best balance between financial protection, cash-flow stability, cost, and flexibility.

## B. Hedge Outcomes

The model compares four primary strategies for managing the company's foreign exchange exposure. A call option is also evaluated separately to demonstrate when it would be appropriate.

| Strategy | USD proceeds at base spot |
|---|---:|
| Unhedged | $8,040,220 |
| Forward hedge | $8,581,880 |
| Money-market hedge | $8,123,527 |
| Protective put | $7,871,952 |

### Unhedged Position

Remaining unhedged would allow the company to benefit fully if the euro appreciates. There would be no hedging premium or borrowing requirement. However, the company would also be exposed to the full downside of euro depreciation.

At the base spot rate, the company would receive approximately $8.04 million. A 5% depreciation of the euro would reduce proceeds by $402,011. This level of uncertainty could make it difficult for management to budget for future expenses.

### Forward Hedge

The forward hedge provides the highest modeled proceeds at $8,581,880 using the assigned forward rate of 1.1756. It allows the company to lock in an exchange rate today and eliminates uncertainty surrounding the dollar value of the receivable.

The primary disadvantage is that the company would give up the opportunity to benefit from euro appreciation beyond the contracted forward rate. However, the certainty provided by the forward is valuable for a company that needs to plan its future cash flows.

The assigned forward rate must be reconfirmed because it differs significantly from the rate implied by interest rate parity.

### Money-Market Hedge

The money-market hedge provides approximately $8,123,527 at settlement. This strategy involves borrowing euros today, converting them into U.S. dollars, and investing the dollars until settlement. The future euro receivable is then used to repay the loan.

Like the forward hedge, this strategy provides a predictable financial outcome. However, it requires additional financing arrangements and may affect the company's borrowing capacity. The actual proceeds would also depend on the borrowing and investment rates available to the company.

### Protective Put Option

The protective put allows the company to establish a minimum level of proceeds while maintaining the ability to benefit from euro appreciation.

The option premium costs $163,520 today. After accounting for the time value of money, the premium has a settlement value of approximately $168,268. This results in minimum net proceeds of approximately $7,871,952.

The put provides more flexibility than the forward or money-market hedge, but that flexibility comes at a cost. Unless management expects significant euro appreciation or places a high value on retaining upside potential, the premium may be difficult to justify.

### Call Option

A call option on the euro is not an appropriate protective hedge for this receivable. The company is already exposed to the benefits of euro appreciation. Purchasing a call would increase exposure in that same direction rather than protect against depreciation.

A call would be more appropriate if the company had a future euro payable. In that situation, the company would need protection against an increase in the cost of purchasing euros.

## C. Sensitivity Interpretation

The sensitivity analysis evaluates eleven possible ending exchange rates ranging from a 5% depreciation to a 5% appreciation of the euro.

| Strategy | EUR -5% | Base spot | EUR +5% |
|---|---:|---:|---:|
| Unhedged | $7,638,209 | $8,040,220 | $8,442,231 |
| Forward | $8,581,880 | $8,581,880 | $8,581,880 |
| Money market | $8,123,527 | $8,123,527 | $8,123,527 |
| Protective put | $7,871,952 | $7,871,952 | $8,273,963 |

The forward hedge produces the highest proceeds across all eleven scenarios. Even when the euro appreciates by 5%, the unhedged position produces approximately $139,649 less than the assigned forward hedge.

The money-market hedge also remains constant across the sensitivity analysis. Although it provides lower proceeds than the assigned forward, it still offers protection against unfavorable exchange-rate movements.

The protective put performs differently because it establishes a floor while allowing participation in euro appreciation. When the euro depreciates, the company can exercise the option and receive the strike rate. When the euro appreciates above the strike, the company can allow the option to expire and convert the receivable at the higher market rate.

The unhedged position would outperform the assigned forward if the ending spot rate exceeded 1.1756. The protective put would need an ending spot rate of approximately 1.1987 to outperform the assigned forward after accounting for the premium.

These exchange rates are outside the sensitivity range tested in the model. However, the sensitivity analysis is not a forecast and does not guarantee that exchange rates will remain within this range.

## D. Recommendation

I recommend pursuing a forward hedge for the full EUR 7.3 million receivable, provided that the bank confirms the assigned forward quote is available for the required settlement date.

At the assigned rate of 1.1756, the forward would secure approximately $8.58 million. This is $541,660 more than the unhedged position at the base spot rate and approximately $458,353 more than the modeled money-market hedge.

However, an important concern identified during validation is the difference between the assigned forward rate and the forward rate implied by covered interest rate parity.

| Parity comparison | Value |
|---|---:|
| Assigned forward rate | 1.17560 |
| CIP-implied forward rate | 1.11281 |
| Forward rate gap | 0.06279 USD/EUR |
| Dollar value of gap | Approximately $458,353 |

The assigned forward rate is approximately 5.64% higher than the implied forward rate. This is a significant difference and should not be ignored when making a financial decision.

One possible explanation is that the assigned forward quote and the market interest rates were obtained under different market conditions. The interest rates used in the model are also proxies rather than actual borrowing and investment rates for the full 273-day period. These differences limit the accuracy of the parity comparison.

The independent AI analysis and manual verification reproduced the main calculations in the workbook. The professor's FX Hedging Lab also produced the same forward and money-market results. Therefore, the parity discrepancy appears to come from the inputs rather than the hedge formulas.

The discrepancy changes how I would execute the recommendation. I would not commit to the forward hedge without obtaining a current and executable bank quote. If the assigned rate is confirmed, I would proceed with the forward hedge. If the bank provides a lower rate, I would compare the revised forward proceeds against the money-market hedge using actual financing rates before making a final commitment.

## E. Executive Justification

My recommendation prioritizes cash-flow stability and budget certainty. Since the company expects to receive a large payment in approximately nine months, knowing the dollar value in advance would allow management to make more informed financial decisions.

A forward hedge would typically avoid the upfront premium required by an option. It would also avoid the separate borrowing and investment transactions required by a money-market hedge. This makes the forward an attractive strategy for preserving liquidity, although the company should review any collateral or credit requirements imposed by the bank.

The protective put offers valuable flexibility, but its upfront premium of $163,520 represents a significant use of company funds. Based on the modeled sensitivity range, the additional flexibility does not generate enough proceeds to outperform the assigned forward.

To implement the recommendation, management should request an updated forward quote that matches the receivable amount and settlement date. The company should also obtain comparable borrowing and investment rates and repeat the parity check. Any transaction fees, credit requirements, and counterparty risks should be reviewed before executing the hedge.

Ultimately, the purpose of hedging is not necessarily to maximize profits from exchange-rate movements. It is to reduce financial uncertainty and protect the value of the company's business transactions.

Based on the current model, the forward hedge provides the strongest combination of predictable proceeds, liquidity management, and downside protection. Subject to confirmation of the bank's quote, I believe it is the most appropriate strategy for the company's foreign exchange exposure.

## Supporting Analysis

- [FX Hedging Model](../../capabilities/fx-hedging/model.xlsx)
- [Model Specification](../../capabilities/fx-hedging/spec.md)
- [Market-Data Memo](../../data/2026-11-16-seed-genetics-market-data-memo.md)
- [Stage 5 Validation Analysis](../../analysis/2026-11-25-seed-genetics-validation-analysis.md)
