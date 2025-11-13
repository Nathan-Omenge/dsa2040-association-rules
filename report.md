# Report: Association Rule Mining with Online Retail Dataset

## 1. Introduction
The goal of this project is to apply association rule mining techniques to a large-scale real-world dataset from the UCI Online Retail dataset. The objective is to understand product co-occurrence patterns, generate association rules, and derive actionable insights using Apriori and FP-Growth algorithms.

Association rule mining is a key technique in data mining used to uncover hidden relationships between items in transactional datasets. These rules can support marketing decisions such as product bundling, recommendations, and store layout optimisation.

---

## 2. Data Preparation

### 2.1 Raw Data Overview
- 541,909 transaction rows  
- 8 columns  
- Covers Dec 2010 to Dec 2011  
- Gift retail company based in the UK  

### 2.2 Cleaning Steps
1. Removed cancelled invoices (InvoiceNo starting with 'C')  
2. Removed missing CustomerID and Description  
3. Filtered dataset to **United Kingdom** only  
4. Kept only positive quantities and prices  
5. Standardised product descriptions (lowercase, stripped spaces)  
6. Removed duplicates  
7. Converted transactions to a **basket format** for mining  

### 2.3 Resulting Dataset
- 349,203 cleaned rows  
- 16,646 invoices  
- 3,833 products  
- 3,920 customers  

This dataset was then used to compute frequent itemsets and association rules.

---

## 3. Frequent Itemset Mining

### 3.1 Apriori Algorithm
Apriori was run with two support thresholds:

- **2% Support** → 236 itemsets  
- **5% Support** → 19 itemsets  

The most frequent items include:

- white hanging heart t-light holder (11.3%)  
- jumbo bag red retrospot (8.6%)  
- regency cakestand 3 tier (8.4%)  

### 3.2 FP-Growth Algorithm
FP-Growth was used to validate Apriori results.

- Provides identical frequent itemsets  
- Finishes extremely quickly  
- More scalable and efficient  

FP-Growth is recommended for real-world large retail datasets.

---

## 4. Association Rule Generation (Apriori Only)

Rules were generated using **support**, **confidence**, and **lift** metrics.  
Filtering applied:

- **Confidence ≥ 0.6**
- **Lift ≥ 1.2**

### 4.1 Key Rules & Insights

#### Rule 1  
**pink regency teacup + roses regency teacup → green regency teacup**  
- Confidence: 0.89  
- Lift: 24.21  

**Insight:** Customers collect the full colour set. Promote bundling.

---

#### Rule 2  
**pink regency teacup → green + roses regency teacups**  
- Confidence: 0.69  
- Lift: 24.19  

**Insight:** Pink is the entry point. Cross-sell green and roses variants.

---

#### Rule 3  
**green + roses regency teacups → pink regency teacup**  
- Confidence: 0.72  
- Lift: 24.19  

**Insight:** Customers complete the trilogy set. Offer “complete your set” suggestions.

---

## 5. Conclusion

This project successfully demonstrated association rule mining using Apriori and FP-Growth. The Online Retail dataset shows strong product co-purchase patterns, particularly among thematic decorative items.

Key outcomes:

- Identified the most popular products  
- Discovered high-lift association rules  
- Compared Apriori and FP-Growth performance  
- Produced business insights enabling bundling, recommendations, and product placement strategies  

The approach and insights can be extended to recommendation systems, market segmentation, or retail inventory optimisation.

---