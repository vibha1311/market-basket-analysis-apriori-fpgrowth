# Market Basket Analysis - Grocery Dataset

## Overview
This project performs **Market Basket Analysis** on a grocery transaction dataset using **Apriori** and **FP-Growth** algorithms to uncover patterns in customer purchases. The goal is to identify frequently bought items and generate association rules to provide actionable insights for retail strategies such as promotions, product placement, and cross-selling.

---

## Dataset
- The dataset contains grocery transactions.  
- Each row represents a single transaction and each column contains an item purchased in that transaction.  
- Missing values (`NaN`) indicate no item in that column for the transaction.  
- Source: https://www.kaggle.com/datasets/irfanasrullah/groceries/data?select=groceries+-+groceries.csv

---

## Methodology

1. **Data Preprocessing**
   - Removed the first row (column headers from CSV) and the transaction count column.
   - Converted each row into a list of items purchased.
   - Handled missing values and converted data into a format suitable for frequent pattern mining.

2. **Transaction Encoding**
   - Used **TransactionEncoder** from `mlxtend` to convert transactions into a one-hot encoded dataframe for Apriori and FP-Growth.

3. **Frequent Itemset Mining**
   - Applied **Apriori** and **FP-Growth** algorithms to find frequent itemsets.
   - Minimum support threshold: `0.01` (1%)
   - Top items include: `whole milk`, `other vegetables`, `rolls/buns`, `soda`, `yogurt`.

4. **Association Rules Generation**
   - Generated association rules from frequent itemsets.
   - Evaluated rules using:
     - **Support**: How often the rule occurs in transactions
     - **Confidence**: Probability of consequent given antecedent
     - **Lift**: Strength of association relative to random chance
   - Example rules:
     - `{curd} → {whole milk, yogurt}` (lift: 3.37)
     - `{other vegetables, citrus fruit} → {root vegetables}` (lift: 3.29)

5. **Visualization**
   - **Bar charts** for top frequent items
   - **Network graphs** to visualize association rules
   - **Scatter plots** of support vs confidence for insights

---

## Key Insights

- `Whole milk` is the most purchased item (25.5% of transactions).  
- Items frequently bought together:
  - `{curd} → {whole milk, yogurt}`  
  - `{other vegetables, citrus fruit} → {root vegetables}`  
  - `{beef} ↔ {root vegetables}`  
- Retail recommendations:
  - Place frequently bought items together for cross-selling.
  - Consider bundle promotions for associated items.
  - Prioritize stocking high-support items like milk, vegetables, and rolls/buns.

---

## Libraries Used

- `pandas` – Data manipulation  
- `mlxtend` – Apriori, FP-Growth, association rules  
- `matplotlib` – Plotting charts  
- `seaborn` – Scatter plots  
- `networkx` – Visualizing rules as network graphs  

---

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/yourusername/market-basket-analysis.git
cd market-basket-analysis

