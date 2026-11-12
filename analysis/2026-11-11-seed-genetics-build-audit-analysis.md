# Stage 3 Build and Audit Analysis: Seed Genetics

**Author:** Tacoma Kelson  
**Date:** 2026-11-11  
**Scenario:** 32 – seed-genetics  
**Workbook:** `model.xlsx`

## 1. Model Build

I used AI assistance to build an Excel model based on my Stage 2 specification. The model compares an unhedged EUR 7.3 million receivable with a forward hedge, money-market hedge, and protective EUR put option over 273 days.

The workbook includes 10 tabs covering the inputs, calculations, sensitivity analysis, summary, assumptions, and validation checks.

## 2. Formula and Calculation Checks

I reviewed the workbook results and tested the put option formula in Excel.

- **Forward hedge:** The model calculated $8,581,880 using the assigned forward rate of 1.1756.
- **Put premium:** The upfront premium was $163,520. Its settlement-date value was $168,418.11 using the placeholder USD interest rate.
- **Put downside test:** I changed the settlement exchange rate to 1.05. The put net proceeds stayed at $7,971,081.89, confirming the downside floor.
- **Put upside test:** I changed the settlement exchange rate to 1.20. The put net proceeds increased to $8,591,581.89, confirming upside participation.

After testing, I restored the original settlement-rate formula.

## 3. Issues Found

The sensitivity table initially displayed `#######` in several cells because the columns were too narrow. I widened the columns so the values could be read.

The Validation tab also identified two parity flags. The assigned forward rate was 1.1756, while the forward rate implied by the placeholder spot and interest rates was approximately 1.12754. The difference was about 0.04806 USD per EUR, which exceeded the model's 0.0010 tolerance.

These flags show that the indicative market inputs are not consistent with covered interest parity. They do not automatically mean the spreadsheet formulas are incorrect.

## 4. Sensitivity Analysis

The workbook tests 11 settlement exchange rates from 5% below to 5% above the placeholder spot rate in 1% increments.

The chart compares the unhedged position, forward hedge, money-market hedge, and protective put option. The forward and money-market hedges remain fixed across settlement rates. The unhedged position changes with the euro, while the put protects against downside
