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
