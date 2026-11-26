# Stage 5 Validation Report: Seed Genetics

Date: November 25, 2026  
Scenario: 32  
Exposure: EUR 7,300,000 receivable in 273 days

## 1. Independent AI Test

I started a separate ChatGPT conversation and provided only my Stage 2 model specification and Stage 4 market-data memo. I asked the AI to calculate the hedging outcomes, sensitivity analysis, interest rate parity check, and recommended strategy without providing my Excel workbook.

The original response is available [here](2026-11-25-seed-genetics-independent-llm-output.md).

## 2. Comparison of Results

All amounts are rounded to the nearest dollar.

| Scenario | Strategy | Excel | Independent AI | Difference |
|---|---|---:|---:|---:|
| -5% | Unhedged | $7,638,209 | $7,638,209 | $0 |
| -5% | Forward | $8,581,880 | $8,581,880 | $0 |
| -5% | Money market | $8,123,527 | $8,123,527 | $0 |
| -5% | Protective put | $7,871,952 | $7,871,952 | $0 |
| -5% | Call net payoff | -$282,449 | -$282,449 | $0 |
| 0% | Unhedged | $8,040,220 | $8,040,220 | $0 |
| 0% | Forward | $8,581,880 | $8,581,880 | $0 |
| 0% | Money market | $8,123,527 | $8,123,527 | $0 |
| 0% | Protective put | $7,871,952 | $7,871,952 | $0 |
| 0% | Call net payoff | -$282,449 | -$282,449 | $0 |
| +5% | Unhedged | $8,442,231 | $8,442,231 | $0 |
| +5% | Forward | $8,581,880 | $8,581,880 | $0 |
| +5% | Money market | $8,123,527 | $8,123,527 | $0 |
| +5% | Protective put | $8,273,963 | $8,273,963 | $0 |
| +5% | Call net payoff | $119,562 | $119,562 | $0 |

The independent AI reproduced the workbook results at the displayed precision. Both analyses showed that the forward hedge provided the highest proceeds across all 11 sensitivity scenarios. The call payoff is shown separately because it is not a protective hedge for a EUR receivable.

## 3. Manual Calculation Checks

### Forward Hedge

7,300,000 × 1.1756 = $8,581,880.00

This matches the workbook.

### Money-Market Hedge: Hand Verification

**Step 1: Borrow EUR today**

FC_AMT / (1 + R_FC × T_DAYS / 360)

= 7,300,000 / (1 + 0.02437 × 273 / 360)

≈ EUR 7,167,540

**Step 2: Convert EUR to USD at the spot rate**

EUR borrowed × S0_in

= 7,167,540 × 1.1014

≈ $7,894,328

**Step 3: Invest USD until settlement**

USD converted × (1 + R_USD × T_DAYS / 360)

= 7,894,328 × (1 + 0.0382858 × 273 / 360)

≈ $8,123,527

The result matches the workbook's money-market hedge proceeds of $8,123,527.39 when rounded to the nearest dollar. Intermediate calculations are rounded for presentation.

### Protective Put

Premium paid today = 7,300,000 × 0.0224 = $163,520.00

Premium at settlement = 163,520 × (1 + 0.0382858 × 273/360)

Premium at settlement = approximately $168,267.54

Net proceeds at the base spot = 7,300,000 × 1.1014 − 168,267.54

Final proceeds = $7,871,952.46

This matches the workbook.

## 4. Discrepancies and Validation Findings

The assigned forward rate of 1.1756 does not match the implied forward rate of approximately 1.11281. The difference is approximately 0.06279 USD per EUR. This creates a difference of approximately $458,353 between the forward and money-market hedge proceeds.

I kept the parity flags visible because changing the inputs just to make the validation pass would hide an important limitation.

The independent AI also confirmed the $4,747.54 difference between my workbook's protective put calculation and the professor's FX Hedging Lab. My workbook accounts for the future value of the premium while the lab appears to subtract the original premium. I retained my workbook's calculation because it compares proceeds at settlement.

## 5. Specification Retrospective

My Stage 2 specification was detailed enough for the independent AI to reproduce the main calculations without accessing my Excel workbook. The named inputs, formulas, and calculation assumptions helped make the model easier to understand.

One issue was that my Stage 4 memo did not explicitly list the updated option strike prices. The AI had to assume that both strikes were equal to the updated spot rate of 1.1014. This assumption was consistent with my workbook, but I should have made it clearer in the memo.

Another limitation was that the Stage 4 memo already contained some of the expected results. Although I asked the AI to calculate the results independently, I cannot confirm that it did not rely on those figures.

If I were to repeat this project, I would include every updated input in one table and separate the market inputs from the expected results. I would also try to obtain borrowing rates, investment rates, and forward quotes that match the actual settlement period.

## 6. Conclusion

The independent AI results and manual calculation checks agree with my Excel workbook at the reported precision. The main remaining concern is the consistency of the market inputs rather than the calculated hedge outcomes.

The forward hedge provides the highest modeled proceeds, but the assigned rate must be confirmed before making an actual financial decision. The interest rate proxies and assigned option premiums also limit how accurately the model represents executable market prices.

Overall, this project helped me understand that a financial model can calculate results correctly while still producing a misleading recommendation if its inputs are not realistic.
