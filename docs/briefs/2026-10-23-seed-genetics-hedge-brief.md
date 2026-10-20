---
type: brief
engagement: fx-hedging
capability: fx-hedging
date: 2026-10-23
status: committed
hypothesis: "I expect the option hedge to provide the best balance of downside protection and upside potential because it protects the EUR 7.3 million receivable while allowing the company to benefit if the euro strengthens."
---

# FX Hedging Executive Brief: Seed Genetics

## Exposure
A U.S. seed-genetics company has invoiced a French grain cooperative and expects to receive EUR 7.3 million in 273 days. Because the payment is in euros, the amount we receive is fixed in EUR, but its value in U.S. dollars is not. If the euro weakens against the dollar before the payment is received, the company will receive fewer dollars when the EUR 7.3 million is converted. As an illustration, a 10% decline from 1.1756 would reduce the dollar value of the EUR 7.3 million receivable by about $858,000. This shows how an adverse currency move could create a significant gap in expected cash flow.

## Hedge Alternatives
**Forward / futures:** We could lock in an exchange rate today for the EUR 7.3 million we will receive in 273 days. Our indicative forward rate is 1.1756 EURUSD, which would give us certainty about the dollar value of the receivable and protect our budget if the euro weakens. The trade-off is that we would also give up the benefit if the euro strengthens before settlement.

**Money-market hedge:** We could borrow euros today, convert them to U.S. dollars at the current spot rate, and invest those dollars until the receivable arrives. This would also give us certainty about the dollar value of the payment. However, it requires borrowing capacity and involves more steps than simply using a forward contract.

**Options:** We could buy a put option on EUR, which would give us the right to sell our euros at the strike rate if the euro weakens. The assigned premium is $0.0224 per EUR, so protecting the full EUR 7.3 million receivable would require an upfront premium of $163,520. Unlike the forward and money-market hedges, the option would still allow us to benefit if the euro strengthens. The trade-off is paying the premium even if we never need to exercise the option.

## What I Am Assuming
I am assuming the company will receive the full EUR 7.3 million in 273 days and that the indicative forward rate of 1.1756 will be available for the full exposure. I am also assuming the company can access the borrowing and investing needed for a money-market hedge. The current EURUSD spot rate and USD and EUR interest rates will be collected using market-close data when Stage 2 begins. These market inputs will need to be tested before comparing the hedge alternatives.

## Hypothesis
I expect the option hedge to provide the best balance of protection and flexibility for the EUR 7.3 million receivable. The put creates a floor if the euro weakens while still allowing the company to benefit if the euro strengthens. I expect that flexibility to be valuable enough to justify the $163,520 premium when compared with the certainty provided by the forward and money-market hedges.

## How I Would Know I Was Wrong
I would know this hypothesis was wrong if the model shows that the cost of the option premium outweighs the value of keeping the upside potential. If the forward or money-market hedge provides a meaningfully better dollar outcome across the scenarios we test, then the option would not provide the best balance of protection and flexibility.

## Next Steps
In Stage 2, I will design the model and define the inputs, formulas, and validation checks needed to compare the three hedge alternatives. In Stage 3, the workbook will be built with AI assistance and then audited for errors. Stage 4 will replace the placeholder inputs with sourced and timestamped market data. Finally, Stage 5 will independently validate the results, include hand verification, and use the completed analysis to make a final hedging recommendation in a decision memo.
