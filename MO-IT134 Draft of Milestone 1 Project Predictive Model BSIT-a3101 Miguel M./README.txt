# Milestone 1 – Predictive Model: Customer Purchase Likelihood
**FinMark Corporation | BSIT-A3101**

---

**Goal:** Build a machine learning model that estimates whether a company is likely to make a purchase from FinMark Corporation.

**Datasets used:**
- `customers_data.csv` (raw) — to identify non-purchasers (companies with no valid ID)
- `clean_customers.csv` — 90 verified purchaser companies
- `clean_transactions.csv` — 4,780 valid transaction records
- `clean_products.csv` — 18 verified products (peso prices cleaned in Step 3)

**How we define the target label:**
- `purchased = 1` → company appears in clean transactions (they bought something)
- `purchased = 0` → company had no valid ID in raw data and never appears in any transaction

**Notebook flow:**
1. Import libraries
2. Load all data files
3. Clean the product prices (remove peso sign)
4. Fix data types
5. Merge transactions with product info
6. Build the full customer table (purchasers + non-purchasers)
7. Feature engineering
8. Exploratory Data Analysis (EDA)
9. Train/test split
10. Train the model
11. Evaluate the model
12. Feature importance
13. Score all customers
14. Save outputs



---
## Summary

| Step | What was done|
|------|-------------|
| Load | 4 files: clean_transactions, clean_customers, clean_products, raw_customers |
| Clean products | Removed peso sign and comma from Product_Price -> real number |
| Fix types | Fixed ID and date types after CSV reload |
| Merge | Joined transactions with product names and cleaned prices |
| Build table | 90 purchasers (label=1) + 10 non-purchasers (label=0) = 100 companies |
| Feature engineering | 12 features from all 3 datasets |
| EDA | Charts: label balance, product prices, feature distributions |
| Train/test split | 80 training / 20 test, stratified |
| Model | Logistic Regression inside StandardScaler Pipeline |
| Evaluate | Classification report, ROC AUC, Confusion Matrix |
| Score | All 100 companies scored with a purchase likelihood probability |
| Save | 2 output files in milestone1_output/ |

**All 3 datasets were used:**
- **Customers** -> who the companies are + Company_Profit feature
- **Transactions** -> how many orders, total spend, product variety
- **Products** -> avg/max/min product price tier per company (after cleaning peso sign)