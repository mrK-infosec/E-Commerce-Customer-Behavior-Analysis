Brazilian Olist Dataset — 118,307 Orders

Why I Built This
I wanted to work on a real business problem — not just clean data and make charts.
Every e-commerce company has the same headache: customers buy once and disappear. I wanted to understand why that happens and whether you can predict it before it does.
So I took the Olist dataset — a real Brazilian e-commerce platform with 100K+ orders — and tried to answer one question:

"Which customers are about to leave, and what do they have in common?"


What I Found
A few things surprised me:

60.8% of customers never came back after their first purchase. That's not a retention problem — that's a structural issue.
Champions (16% of customers) spend 6x more than lost customers on average ($315 vs $54). A small group is carrying most of the revenue.
How much someone spends predicts churn better than how often they buy. Frequency barely mattered — Monetary value was almost everything (99.5% feature importance).
Sales grew steadily from 2016 to late 2018, then dropped sharply. Something happened in Q4 2018 worth investigating.

What I Did
Step 1 — Data Preparation
Loaded and merged 6 CSV files (orders, customers, products, payments, reviews, categories) into one clean dataset. Handled missing values, fixed date formats, and engineered new features.
Step 2 — RFM Segmentation
Scored every customer on Recency, Frequency, and Monetary value. Grouped them into 4 segments:
SegmentCountAvg Order ValueChampions15,493$315Loyal Customers49,764$183At Risk23,944$100Lost Customers6,218$54
Step 3 — Churn Prediction
Defined churn as 180+ days since last purchase. Trained a Random Forest classifier to predict which customers would churn — got 69.2% accuracy without using Recency as a feature (to avoid data leakage).

Business Recommendations
If I were presenting this to a team, I'd say three things:

Focus retention budget on the "At Risk" segment (23,944 customers). They've bought before, they're not gone yet, and a targeted campaign could recover a meaningful chunk of revenue.
Don't try to win back Lost Customers with discounts. Their average order value is too low to justify the cost. Better to understand why they left.
Investigate Q4 2018. The sales drop is too sharp to be seasonal. Could be a logistics issue, a competitor, or a product problem — but it needs a separate analysis.


Tools & Stack


Python 3.11
├── Pandas       — data manipulation & merging
├── Matplotlib   — visualizations
├── Seaborn      — statistical plots
└── Scikit-learn — Random Forest classifier


Files in This Repo


ecommerce-analysis/
├── ecommerce_analysis.ipynb   ← main notebook
├── rfm_dashboard.png          ← RFM visualization
├── churn_model.png            ← churn prediction results
├── sales_dashboard.png        ← sales overview
└── README.md


What I'd Do Next
This project has a few limitations I'm aware of:

The churn definition (180 days) is arbitrary — a real business would define it based on their purchase cycle
69.2% accuracy is decent but not production-ready. Adding demographic data or browsing behavior would likely improve it
I'd want to test XGBoost and compare it against Random Forest

If I had more time, I'd also build a Power BI dashboard on top of this so non-technical stakeholders could explore the segments themselves.

<img width="2082" height="1476" alt="rfm_dashboard" src="https://github.com/user-attachments/assets/522830ce-b2b6-4b9d-9549-de1aeec5127b" />

<img width="1728" height="740" alt="churn_model" src="https://github.com/user-attachments/assets/b99036b6-f87c-4fc8-9d24-bcb5700cd6f5" />



Built by Abdulrahman Adel — Data Analyst based in Dubai
github.com/mrK-infosec | abdoadel3337@hotmail.com
