# Dynamic Price Elasticity & Cannibalization Framework (R)

An R decision-support tool that uses an interrupted time-series design and cross-price elasticity to tell real growth from cannibalised sales when a base-model smartphone is discounted.

## Business challenge
Discounting a base model (iPhone 15) to clear inventory can pull customers away from the premium flagship (iPhone 16 Pro). Retail managers need a way to separate **growth sales** from **cannibalised sales**, where the discount simply moves premium buyers down-tier and erodes margin.

## Approach
- **Interrupted time-series design:** compares *Baseline* (full price) and *Sale* (discounted) windows for each promotional event.
- **Cross-price elasticity of demand (XED):**

  $$XED = \frac{\% \Delta Q_{premium}}{\% \Delta P_{base}}$$

  XED above 0.5 is treated as high cannibalisation risk.
- **Object-oriented R:** an S3 class (`PromotionEvent`) with an `analyze_risk()` method, so new promotions are analysed with one call.
- **What-if simulation:** `simulate_scenario()` lets a manager enter a proposed discount and see the expected premium volume loss.

## Key findings
- Both the **Valentine's** and **Summer** promotions showed **XED > 0.5**, so the two models behave as substitutes.
- The time series shows premium sales falling during base-model promotions.

## Recommendations
1. **Price floor:** cap base-model discounts at roughly 10–12%.
2. **Add value instead of cutting price:** bundle accessories or AppleCare+ with the flagship.
3. **De-conflict promotions:** avoid running base-model clearance during key flagship marketing periods.

## Repository structure
```
├── price_elasticity_dss.Rmd        # Main framework: S3 class, XED, simulation
├── price_elasticity_dss.html       # Knitted output
├── cannibalization_eda.Rmd         # Earlier exploratory analysis of the same data
├── price_elasticity_report.pdf     # Written report
└── data/
    └── smartphone_sales.xlsx       # Daily sales and prices, iPhone 15 and 16 Pro
```

## How to run
Open the folder in RStudio (working directory = repository root):
```r
install.packages(c("readxl", "dplyr", "ggplot2", "rmarkdown"))
rmarkdown::render("price_elasticity_dss.Rmd")
```
Result files (elasticity table, log, saved arrays) are written to `outputs/`.

## Tech stack
R · dplyr · ggplot2 · readxl · R Markdown
