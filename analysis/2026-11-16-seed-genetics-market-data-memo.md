# Stage 4 Market Data Memo: Seed Genetics FX Hedging

**Date:** November 16, 2026  
**Scenario:** 32, Seed Genetics  
**Exposure:** EUR 7,300,000 receivable in 273 days

## 1. Market Data

For Stage 4, I updated my Excel model using published market reference rates instead of the placeholder values from Stage 3.

| Input | Value | Source |
|---|---|---|
| EUR/USD spot rate | 1.1014 | European Central Bank, November 16, 2026 |
| USD interest rate | 3.82858% | NY Fed 90-day average SOFR, November 16, 2026 |
| EUR interest rate | 2.437% | ECB €STR, November 13, 2026 reference date, published November 16 |

The interest rates are proxies because they are not actual 273-day borrowing or investment quotes. The ECB spot rate is a published reference rate rather than an executable exchange rate.

I kept the assigned forward rate of 1.1756 and the option premiums from my original scenario so I could compare the hedging strategies using the updated market inputs.

## 2. Updated Hedge Results

After entering the new market data, I checked how the results changed in my Excel model.

| Hedging Strategy | USD Proceeds |
|---|---:|
| Unhedged | $8,040,220.00 |
| Forward hedge | $8,581,880.00 |
| Money-market hedge | $8,123,527.39 |
| Protective put | $7,871,952.46 |

The forward hedge provides the highest USD proceeds at the current spot rate. The money-market hedge provides a lower guaranteed amount based on the interest rates I used. The protective put has the lowest proceeds in this comparison because of the option premium, but it still provides downside protection if the euro weakens.

The put premium carried forward to settlement is $168,267.54.

## 3. Validation Results and Limitations

After updating the market inputs, I checked the Validation tab to make sure my formulas were still working correctly.

The model passed nine validation checks but showed two covered interest parity (CIP) flags.

- **Implied forward rate:** 1.11281
- **Assigned forward rate:** 1.1756
- **Difference:** 0.06279

The difference occurs because the assigned forward rate does not match the forward rate implied by the updated spot rate and interest rate proxies. This does not necessarily mean my Excel formulas are incorrect.

The main limitation is that the SOFR and €STR benchmarks are not actual 273-day borrowing and lending rates. The forward rate is also assigned by the scenario rather than taken from a current market quote.

Because of these differences, the results are useful for comparing the hedging strategies in my assignment but should not be treated as executable market prices.

## 4. Conclusion

Based on my updated model, the forward hedge provides the highest USD proceeds at the current spot rate. However, the assigned forward rate is higher than the rate implied by the market inputs, so this advantage may not reflect actual market conditions.

The money-market hedge offers a way to lock in USD proceeds using borrowing and investment rates. The protective put provides downside protection while allowing the company to benefit if the euro strengthens.

Overall, this stage helped me understand how important accurate market data is when comparing hedging strategies. Even when the formulas are correct, the results depend on the quality and consistency of the inputs.
