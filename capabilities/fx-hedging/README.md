# FX Hedging

This capability models foreign exchange risk for a company with a future foreign-currency receivable or payable. It compares different hedging strategies to show how exchange-rate movements can affect the final U.S. dollar outcome.

## Engagements

| Scenario | Engagement | Exposure |
|---|---|---|
| 32 | seed-genetics | EUR 7.3 million receivable in 273 days |

## Model

The model compares:

- An unhedged position
- A forward hedge
- A money-market hedge
- A protective put option
- Call option participation for comparison and validation

The model includes named inputs, sensitivity analysis, a comparison chart, summary results, and validation checks.

## Project Deliverables

- [Model Specification](spec.md)
- [Excel Workbook](model.xlsx)
- [Build and Audit Analysis](../../analysis/2026-11-11-seed-genetics-build-audit-analysis.md)
- [Market-Data Memo](../../data/2026-11-16-seed-genetics-market-data-memo.md)
- [Independent AI Output](../../analysis/2026-11-25-seed-genetics-independent-llm-output.md)
- [Validation Analysis and Specification Retrospective](../../analysis/2026-11-25-seed-genetics-validation-analysis.md)
- [CFO Decision Memo](../../docs/decisions/2026-11-25-seed-genetics-hedge-decision-memo.md)
- [AI Prompt Log](../../prompt-log.md)

## Key Findings

| Strategy | USD proceeds at base spot |
|---|---:|
| Unhedged | $8,040,220 |
| Forward hedge | $8,581,880 |
| Money-market hedge | $8,123,527 |
| Protective put | $7,871,952 |

The forward hedge provides the highest modeled proceeds across all eleven sensitivity scenarios. However, the assigned forward rate differs from the rate implied by covered interest rate parity.

The recommendation is to pursue the forward hedge subject to confirmation of an executable bank quote and comparable financing rates.

## Current Status

- Stage 1: Executive brief completed.
- Stage 2: Model specification completed.
- Stage 3: Excel model built and audited.
- Stage 4: Market inputs updated and results cross-checked.
- Stage 5: Independent AI validation, manual calculation checks, specification retrospective, and CFO decision memo completed.

The model retains the parity flags to communicate the limitations of the assigned forward quote and interest rate proxies.
