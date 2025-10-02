#  Market Basket Analysis: Apriori Algorithm

## Project Overview
This repository contains the results of a Market Basket Analysis (MBA) performed on retail transaction data (7,501 transactions) using the Apriori Algorithm. The primary goal was to discover strong, non-trivial Association Rules between products to optimize store layout, implement effective cross-selling strategies, and ultimately maximize profitability.

## Project Objectives
- **Pattern Discovery:** Identify frequent item combinations that customers tend to purchase together.  
- **Parameter Justification:** Define and justify key algorithm parameters based on specific business criteria.  
- **Actionable Insights:** Translate statistical rules into concrete, measurable business recommendations.  
- **Methodology Review:** Compare the performance and scalability of the Apriori algorithm against alternatives like FP-Growth.  

## Key Concepts & Parameter Justification
The analysis focused on filtering rules based on three core metrics. We prioritized rules with a high Lift to ensure the discovered associations were significantly stronger than random chance.

| Metric | Definition | Value Used in Project | Rationale |
|--------|------------|--------------------|-----------|
| Support | Frequency of an itemset relative to all transactions. | 0.003 (0.3%) | Filters for itemsets occurring frequently enough (approx. 21 times total over the week). |
| Confidence | The probability of buying B, given A has been purchased. | 0.2 (20%) | Ensures a reasonable level of predictive reliability for promotions. |
| Lift | The actual strength of the association. Lift > 1 indicates a positive correlation. | 3 | Filters for the strongest, most non-obvious rules, ensuring the association is at least 3 times stronger than random chance. |

## Core Results: Top 5 Association Rules
The final rules were filtered by **Lift ≥ 3**, yielding the most impactful purchasing patterns:

| Rule (Antecedent → Consequent) | Support | Confidence | Lift |
|--------------------------------|---------|------------|------|
| {light cream} → {chicken} | 0.0045 | 0.2906 | 4.844 |
| {mushroom cream sauce} → {escalope} | 0.0032 | 0.3000 | 3.791 |
| {pasta} → {escalope} | 0.0051 | 0.3729 | 3.751 |
| {fromage blanc} → {honey} | 0.0033 | 0.2451 | 3.692 |
| {herb & pepper} → {ground beef} | 0.0160 | 0.3239 | 3.292 |

## Actionable Business Insights
- **High-Leverage Cross-Sell (Lift: 4.84):** Customers purchasing Light Cream are nearly 5 times more likely to buy Chicken.  
  **Recommendation:** Implement strategic placement, moving Light Cream closer to the Chicken section, and offer "Dinner Kit" bundling promotions.

- **Optimizing Gourmet Meal Kits:** Strong correlations between Escalope and complementary items like Pasta and Mushroom Cream Sauce suggest a clear demand for premium meal solutions.  
  **Recommendation:** Create a dedicated "Gourmet Dinner Station" displaying all three high-Lift items together to encourage complete meal purchases.

- **Boosting High-Volume Sales:** The frequently occurring rule {Herb & Pepper} → {Ground Beef} (high Support) should be facilitated by placing the seasoning directly next to the chilled meat display for customer convenience.

## Methodological Review: Scalability
While Apriori was effective and highly interpretable for this medium-sized dataset, a review of its scalability is crucial for future development.

| Metric | Apriori Algorithm (Current) | FP-Growth Algorithm (Recommended for Scale) |
|--------|----------------------------|--------------------------------------------|
| Database Scans | Multiple passes required, leading to high I/O overhead. | Only two passes are needed to build the FP-Tree. |
| Scalability | Slow and memory-intensive due to massive candidate generation. | Fast and memory-efficient as it avoids generating intermediate candidate sets. |

**Conclusion:** Apriori was appropriate for the initial scope, but FP-Growth is the recommended algorithm for scaling this analysis to large, production-level transaction volumes to maintain efficiency.

## Dataset Source
[Market_Basket_Optimisation](https://www.kaggle.com/datasets/devchauhan1/market-basket-optimisationcsv?utm_source=chatgpt.com)
## Visual Results
The following image shows the **Top Association Rules** extracted using the Apriori Algorithm:

[Top 10 lift](./images/top10_lift)

[support confidence](./images/support_confidence)

[lift distribution](./images/lift_distribution)
