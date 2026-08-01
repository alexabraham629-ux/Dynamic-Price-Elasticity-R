# Dynamic-Price-Elasticity-R
R-based Decision Support System (DSS) using Interrupted Time-Series design to quantify cross-price cannibalization in consumer electronics.
# Dynamic Price Elasticity & Cannibalization Framework (R)

## 📌 Business Challenge
In the consumer electronics sector, promotional events are frequently used to clear base-model inventory. However, discounting a base model (e.g., iPhone 15) often competes directly with the premium flagship (e.g., iPhone 16 Pro). Retail managers lack a quantitative method to distinguish between true **"Growth Sales"** and **"Cannibalized Sales"**—where discounts merely encourage existing premium-tier customers to downgrade, resulting in severe **Margin Erosion**.

## 🎯 Project Objective
This project implements an **Interrupted Time-Series design** in R to provide a data-driven Decision Support System (DSS) for retail managers. It evaluates whether spikes in discounted model sales represent new growth or stolen demand from high-margin premium models.

## ⚙️ Analytical Framework & Methodology
The system calculates the percentage changes in price and quantity across defined "Baseline" (full price) and "Sale" (discounted) periods.
* **Cross-Price Elasticity of Demand (XED):** Quantifies substitution effects. 
  $$XED = \frac{\% \Delta Q_{premium}}{\% \Delta P_{base}}$$
* **Object-Oriented R:** Utilized custom S3 classes (`PromotionEvent`) and method dispatch to cleanly encapsulate promotional date boundaries and automate risk analysis across multiple events.
* **Interactive DSS Simulation:** Includes a console-based simulation module (`simulate_scenario`) allowing managers to input proposed discount percentages and immediately forecast premium volume loss.

## 📊 Key Findings
The framework identified a consistent pattern of cross-price cannibalization across both the **Valentine's** and **Summer** promotional events. 
* **XED > 0.5** confirmed high cannibalization risk, proving the two models function as substitute goods within the same ecosystem. 
* Time-series visualization validated a clear sales divergence pattern: promotional periods for the base model correspond with a measurable decline in premium sales.

## 💡 Strategic Recommendations
1. **Price Floor Optimization:** Establish a strict minimum price threshold (~10-12% maximum discount) for the base model to prevent it from becoming disproportionately attractive to premium-segment customers.
2. **Value-Based Positioning:** Replace aggressive discounting with value-added bundling (e.g., AppleCare+, premium accessories) for the flagship to protect price integrity.
3. **Promotion De-Confliction:** Stagger promotional timing to ensure base-model clearance campaigns do not overlap with key marketing periods for premium models.

## 💻 Tech Stack
* **Language:** R
* **Libraries:** `dplyr` (data manipulation), `ggplot2` (time-series visualization), `readxl` (data ingestion)
* **Outputs:** RMarkdown, HTML, PDF
