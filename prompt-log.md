# Prompt Log

## 2026-10-09

**What I asked:**  
Help me set up the required files and structure for Stage 0 of my GitHub portfolio repository.

**What was produced:**  
Created and reviewed the initial portfolio files, including README.md, RESUME.md, AGENTS.md, CLAUDE.md, and prompt-log.md, with guidance for setting up the repository.

**What was wrong and how it was caught:**  
The first README bio did not meet the required 200–400 word length. This was caught by reviewing the Stage 0 requirements, so I expanded my bio to meet the required length before continuing.

## 2026-10-27

**What I asked:**  
Help me review my Stage 2 FX hedging model specification for the seed-genetics scenario and identify anything missing from the assignment requirements.

**What was produced:**  
Reviewed the model specification for the EUR 7.3 million receivable and helped refine the inputs, workbook architecture, calculation flow, assumptions, sensitivity analysis, validation rules, and outputs. I also created the FX hedging capability README.

**What was wrong and how it was caught:**  
The first draft did not fully match the Stage 2 requirements. The workbook architecture was missing required areas, the sensitivity analysis used the wrong range and increments, and the specification did not include the call option participation logic or all required parity checks. These issues were caught by comparing the draft against the Stage 2 requirements. I revised the specification to include the missing workbook areas, changed the sensitivity range to ±5% in 1% increments, added the call option payoff, clarified the ACT/360 assumptions, and added covered interest parity validation checks.

## 2026-11-02

**What I asked:**  
Help me work through my professor's feedback on my Stage 2 FX hedging model specification and fix each issue in the repository.

**What was produced:**  
Revised the FX hedging specification and capability README based on the professor's review. I added dated placeholder market inputs and strike values, clarified the timing and settlement-date value of the put and call premiums, added `S_T` and the put net-proceeds formula, added a numeric parity tolerance, specified the sensitivity chart type and axes, added author and data-source information for the Cover, and added the Scenario 32 `seed-genetics` engagement to the capability README.

**What was wrong and how it was caught:**  
The professor's review identified several details that were still missing or unclear in the Stage 2 specification. The market inputs did not have dated values, the option premiums were being compared at face value even though they are paid upfront, the put calculation did not define `S_T` or show the full net-proceeds formula, and the parity check did not have a numeric tolerance. The review also identified missing chart details, Cover information, and an engagement row in the capability README. I used the professor's feedback to revise each of these areas before moving on to Stage 3.

## 2026-11-11

**What I asked:**  
Help me build and audit my Stage 3 FX hedging Excel model using my Stage 2 specification for the seed-genetics scenario.

**What was produced:**  
Created an Excel workbook comparing the unhedged position, forward hedge, money-market hedge, and protective EUR put option. The workbook includes named inputs, calculation tabs, a sensitivity chart, summary results, and validation checks. I also created a separate audit report documenting the model review.

**What was wrong and how it was caught:**  
During the audit, I found that some sensitivity results displayed as ####### because the columns were too narrow. I widened the columns so the values were visible. I also checked the put option formula to confirm that it used the settlement spot rate, strike price, and future value of the premium correctly. The validation tab flagged a difference between the assigned forward rate and the rate implied by interest rate parity. I kept this flag visible because the market inputs are still unverified placeholders that will need to be reviewed in Stage 4.

**Additional changes:** 
I needed to change the cell colors to match the assignment requirements. I also struggled a little with formatting the Excel workbook, but I was able to fix the colors and update the legend.

## 2026-11-16

**What I asked:**
Help me complete Stage 4 of my FX hedging project by updating my Excel workbook with market data, checking my formulas, comparing my results with the professor's FX Hedging Lab, and documenting my findings.

**What was produced:**
I updated my Excel workbook using a EUR/USD spot rate of 1.1014, a USD interest rate of 3.82858%, and a EUR interest rate of 2.437%. I also created a market-data memo documenting the sources, assumptions, and updated hedging results. I compared my calculations against the professor's FX Hedging Lab.

**What was wrong and how it was caught:**
The validation tab showed that the assigned forward rate of 1.1756 did not match the implied forward rate of approximately 1.1128. I kept the flag visible and documented the difference instead of changing the inputs just to make the check pass.

I also found a $4,747.54 difference between my protective put calculation and the professor's lab. My workbook includes the future value of the option premium while the lab appears to subtract the premium paid today. I checked my Excel formulas and documented the difference in my memo.

**Additional changes:**
I updated the source information and assumptions in my workbook. I also moved my market-data memo into the correct `data` folder on GitHub. The forward and money-market results matched the professor's lab, and the sensitivity analysis showed that the forward hedge had the highest proceeds across all 11 scenarios.

