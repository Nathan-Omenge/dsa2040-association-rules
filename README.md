# Association Rule Mining with Online Retail Dataset  
DSA 2040A – Data Warehousing and Mining  
**Author:** Nathan Orang'o Omenge 

---

##  Project Overview

This project applies **association rule mining** to a real-world retail dataset to identify frequently purchased items and uncover meaningful product relationships. The project demonstrates:

- Data cleaning and preparation  
- Market basket creation  
- Frequent itemset mining using **Apriori** and **FP-Growth**  
- Association rule generation (Apriori)  
- Interpretation of results using support, confidence, and lift  
- Visualisations of frequent itemsets  

All code was implemented in VS Code and mirrored in Google Colab as required.

---

## Repository Structure
/data/                      # Raw and cleaned dataset
/notebooks/                # Jupyter/Colab notebooks
/visuals/                  # Saved charts (PNG)
README.md                  # This file
report.md or report.pdf    # Final summary report

---

## Dataset Description

**Dataset:** Online Retail (UCI Machine Learning Repository)  
**Transactions:** 541,909 rows  
**Time period:** Dec 2010 – Dec 2011  
**Columns:** InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country

This dataset contains real purchase histories from an online gift retailer and is widely used for association rule mining and market basket analysis.

---

## Tools & Libraries Used

- Python  
- pandas  
- mlxtend.frequent_patterns  
- matplotlib  
- Google Colab (for sharing notebook)

---

## Data Preparation

Key steps:

1. Removed cancelled invoices  
2. Removed missing CustomerID and Description  
3. Restricted to **United Kingdom** for dense patterns  
4. Kept only positive Quantity and UnitPrice  
5. Standardised product descriptions  
6. Generated **basket format (Invoice × Item binary matrix)**

Final cleaned dataset:

- **349,203 rows**
- **16,646 invoices**
- **3,833 unique products**
- **3,920 customers**

---

## Frequent Itemset Mining

### ✔ Apriori  
Run using min_support values: **0.02** and **0.05**  
- 236 frequent itemsets at 2%  
- 19 frequent itemsets at 5%

### ✔ FP-Growth  
Run using min_support values: **0.02** and **0.05**  
- Same itemsets as Apriori  
- Completed almost instantly (faster algorithm)

### Top Frequent Items (Support Values)
- white hanging heart t-light holder — **0.113**
- jumbo bag red retrospot — **0.086**
- regency cakestand 3 tier — **0.084**
- assorted colour bird ornament — **0.078**

(Full graphs in `/visuals`)

---

## Association Rules (Apriori)

Association rules were generated from the Apriori 2% support itemsets.  
We filtered rules using:

- **Confidence ≥ 0.60**
- **Lift ≥ 1.20**

### Highlighted Patterns (with business meaning)

#### Rule 1:
If a customer buys **pink regency teacup and saucer** *AND* **roses regency teacup**,  
they almost always buy the **green regency teacup**.

- Confidence: 0.89  
- Lift: 24.21  

➡ Customers intentionally collect multiple colours.  
➡ Recommend the missing colour automatically.

---

#### Rule 2:
Buying the **pink regency teacup and saucer** strongly predicts buying both  
**green** and **roses** variants.

- Confidence: 0.69  
- Lift: 24.19  

➡ Pink is a “gateway” product into the regency product line.

---

#### Rule 3:
Buying **green** and **roses** regency teacups leads to buying the **pink** version.

- Confidence: 0.72  
- Lift: 24.19  

➡ Customers complete the set → bundle opportunities.

---

##  Apriori vs FP-Growth (Comparison)

| Aspect | Apriori | FP-Growth |
|--------|---------|-----------|
| Speed | Slower | Much faster |
| Method | Candidate generation | FP-tree compression |
| Scalability | Moderate | High |
| Itemsets Found | Same | Same |

FP-Growth is preferable for large-scale retail analytics.

---

## ▶ Notebook Link (Google Colab)

 https://colab.research.google.com/drive/10WEBzZmznqpaPXDyvw1BD-l--ShQu52U?authuser=0#scrollTo=QaR9IEvvFJNl

---

## Report

See **report.md** for the full written summary.