# **FORESIGHT  - [Demand & Inventory Intelligence] — 30-Day Progress Log**

> Zidio Data Science & Analytics Internship

> Intern: **Muhammad Rayyan Shehzad**

> Start Date: **01-07-2026**   End Date: [DD-MM-YYYY]

---

## 📌 Project Overview

An e-commerce business is facing two major challenges regarding inventory management and sales:
* **Capital Tied Up in Slow-Moving Inventory:** A significant portion of working capital is trapped in low-demand stock that does not generate frequent sales (Overstocking).
* **Stockouts of Fast-Moving Items:** High-demand items that sell much faster are not being replenished or restocked in a timely manner, leading to lost revenue opportunities (Stockouts).

## 🧰 Tech Stack

| Area | Tools |
| :--- | :--- |
| **Language & analysis** | Python, pandas, numpy, Jupyter for exploration. |
| **Modelling** | scikit-learn, plus a forecasting approach (statsmodels / Prophet / LightGBM). |
| **Visualisation** | matplotlib / plotly; a clean, labelled style. |
| **Dashboard** | Streamlit (fast to build and deploy). |
| **Serving** | FastAPI for the scoring service (optional if the dashboard exposes scoring). |
| **Deployment** | Streamlit Community Cloud / Hugging Face Spaces / Render. |
| **Version control** | Git; meaningful commits; no data dumps or secrets committed. |

---

## 📂 Repository Structure

```sh
project/
 data/
 notebooks/
 src/
 app/
 reports/
 README.md
```

---

## 📊 Progress Summary

*(Fill this table as you go — one line per day, quick glance for anyone reviewing.)*

| Day | Date | Focus Area | Status | Summary |
|-----|------|------------|--------|---------|
| 01  |  06-07-2026    |  Data Verification          | Done      |  `Data Loading`, `Data View, Shape & Column`, `Primary & Secondary Data Verification`, `Primary Key Uniqueness Check`, `Referential Integrity` |
| 02  |  08-07-2026    |  Data Quality & Cleaning          | Done     |  `Null Count` , `Value-range Check`, `Math Consistency Check`       |
| 03  |  10-07-2026    |  Feature Engineering          | Done      |  `Calendar features` , `Profit` , `Margin` , `redefine 'sales_transaction' data`, `merge Customers & Products on 'sales_transactions'` |
| 04  |      |            | ☐      |         |
| 05  |      |            | ☐      |         |
| 06  |      |            | ☐      |         |
| 07  |      |            | ☐      |         |
| 08  |      |            | ☐      |         |
| 09  |      |            | ☐      |         |
| 10  |      |            | ☐      |         |
| 11  |      |            | ☐      |         |
| 12  |      |            | ☐      |         |
| 13  |      |            | ☐      |         |
| 14  |      |            | ☐      |         |
| 15  |      |            | ☐      |         |
| 16  |      |            | ☐      |         |
| 17  |      |            | ☐      |         |
| 18  |      |            | ☐      |         |
| 19  |      |            | ☐      |         |
| 20  |      |            | ☐      |         |
| 21  |      |            | ☐      |         |
| 22  |      |            | ☐      |         |
| 23  |      |            | ☐      |         |
| 24  |      |            | ☐      |         |
| 25  |      |            | ☐      |         |
| 26  |      |            | ☐      |         |
| 27  |      |            | ☐      |         |
| 28  |      |            | ☐      |         |
| 29  |      |            | ☐      |         |
| 30  |      |            | ☐      |         |

---

## 📅 Daily Log

*(One entry per day. Copy the block below for each day — 30 total.)*

### Week 1

#### Day 01 — 06-07-2026

**Goal for today:** Get the data, load it perfectly, and verify the data integrity before data manipulation to keep things smooth.

## **What I did:**

* Loaded data from the Kaggle Repo: [Dataset Link](https://www.kaggle.com/datasets/mrayyanshehzad/synthetic-retail-dataset-10-million-transactions)
* Viewed the data along with its shape and columns
* Verified the rows of Primary Data (the master tables that remain constant)
* Verified the rows of Secondary Data (the tables that may vary over time / are not constant)
* Checked the Primary Keys of the master tables to maintain data integrity
* Checked the Referential Integrity of Foreign Keys and the promotions
* Set up my GitHub repository and uploaded the Day 01 file

## **Key learnings:**

* Learned how to load data if it is not directly in the root folder of a Kaggle zip file
* Understood the key instances to check under Data Verification
* Learned how to print data in a better way using `{<variable>/<string>:20s}` or `{<variable>/<string>:>8}`
* Developed an understanding of Constant (primary) and Variable (secondary) Data
* Understood how datasets are linked to each other

## **Issues / blockers:**

* Loading data was hard because the required file was not in the root folder
* Didn't know about data verification before, so I had to learn it from AI, whereas previously I jumped directly into data cleaning
* Figuring out the logical perspective of which data should be an exact size (like master tables) and which can tolerate a little variance (like sales transactions)

## **Plan for next day:**

* Data Cleaning & Quality Check
---

#### Day 02 — 08-07-2026

**Goal for today:** Check the quality of the data and clean it, along with handling missing and null values.

## **What I did:**

* Checked the count of null values in each table
* Filled the missing null values in the `sales_transaction` promotion column
* Checked the value ranges of the data to identify and avoid negative or out-of-bound values
* Verified the mathematical correctness of logical operations by taking a sample dataset and confirming that `total_value` equals `quantity` × `price` × `discount`

## **Key learnings:**

* We cannot simply ignore missing or null values; data must remain complete and consistent across all referential tables
* Detecting and avoiding negative values early prevents issues and improves the performance of future Machine Learning models
* Verifying mathematical correctness ensures that the displayed data is reliable and trustworthy

## **Issues / blockers:**

* Spent 2 to 3 hours troubleshooting a critical data loading issue. Previously, importing a different dataset filled up Google Colab's network virtual memory cache. Because of how the KaggleHub API operates, this cache could not be overwritten or cleared from the server side. To resolve this, I switched to the Kaggle CLI tool to download the data directly. KaggleHub routes requests through Google's virtual network memory before mounting it to the Google Collab notebook, whereas Kaggle CLI provides a more direct and reliable transfer.
* Figuring out how to verify mathematical correctness was challenging due to having very few numeric columns. I ultimately had to isolate and focus on the `total_value` calculation to perform this check successfully.

## **Plan for next day:**

* Feature Engineering to extract some useful features
---

#### Day 03 — 10-07-2026

**Goal for today:** Feature Extraction to make the data more reliable and easy to understand on the basis of data visualization later on.

## **What I did:**

* First, I copied the `sales_transactions` dataframe into the `sales` dataframe.
* Then, I identified the features that could be extracted and would be useful to have in the dataset.
* I found `date` in `sales_transactions` to extract days, months, years, etc.
* I found `unit_price` and `cost_price` in `sku_master` to get margin as a new feature.
* I added the `cost_price` from `sku_master` to `sales_transactions` using `merge()` to get profit by means of `total_value - (quantity * cost_price)`.
* Finally, I added back all the extracted and generated features into the `sales_transactions` dataset.
* After that i added usefuls features from `sku_master` & `customer_master` into the `sales_transactions`. 

## **Key learnings:**

* I learnt a very useful function of Pandas called `.to_datetime()`, in which I passed the date column and used its multiple functions to extract required features: `.dt.year`, `.dt.month`, `.dt.strftime('%b')`, `.dt.quarter`, `.dt.day_name()`, & `.dt.dayofweek`. Such a useful function; I found handling dates really hard, but using this made it so easy.
* I got to know how to extract features in an effective way, and especially how new features are generated by performing calculations between multiple features, as I did in margin & profit feature engineering.

## **Issues / blockers:**

* Initially, I designed my function to extract the months, and it worked perfectly, but it becomes hectic if I have to extract multiple date-related features.
* I was confused between `.merge()`, `.join()`, & `.concat()` functions, but after working with them, I'm very much clear about the `.merge()` function.

## **Plan for next day:**

* Maybe Exploratory Data Analysis
---

#### Day 04 — 12-07-2026

**Goal for today:** Start Exploratory Data Analysis and derive useful insights

## **What I did:**
* I started working on the exploratory data analysis.
* I get the Sales Performance & Trend by using Calender data & Reveneue Calculation using `total_value` & `quater`based coloring to better understand the seasonality.
* As only revenue can't explain which month made most profit so i visualize Profit & Reveneue side by side.
* Before i move on to the Customer & Behavioural Analysis the processor & RAM were exhausting so badly.
* So I applied Checkpointing/ Staging the Data. 

## **Key learnings:**
* I develop the understanding of how to use `.agg()` along with the `.groupby()`.
* I found that Histogram & Bar plot are foundation of deriving insights.
* I get to know how can make the processor consume less memory by means of Checkpointing.
* Explored a new File format `Parquet` which is fast & smart and comes with compression & decompression algorithm to make files lightweight.
* As my memory got exhausted so i use google collab and there i did checkpointing.
* I get to know how G-Drive Mounting works and helps to keep things stored.

## **Issues / blockers:**
* The issue i'm facing is processor get always exhausted due to lack of RAM i have.
* So i have to perform Checkpointing, as the load was actually created by file `sales_transactions` as it contains 10million records and also i added more features by feature engineering to it's extensively heavy file.
* Therefore i separated the EDA file from this Data Preprocessing File.
## **Plan for next day:**

* Continue Working on EDA.
---

#### Day 05 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

### Week 2

#### Day 06 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 07 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 08 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 09 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 10 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

### Week 3

#### Day 11 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 12 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 13 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 14 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 15 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

### Week 4

#### Day 16 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 17 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 18 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 19 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 20 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

### Week 5

#### Day 21 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 22 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 23 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 24 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 25 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

### Week 6

#### Day 26 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 27 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 28 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 29 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

#### Day 30 — [Date]

**Goal for today:**

## **What I did:**

## **Key learnings:**

## **Issues / blockers:**

## **Plan for next day:**

---

## ✅ Final Deliverables

*(List the final output links/paths once ready.)*

- [ ] Data pipeline / cleaned dataset
- [ ] EDA & data-quality report
- [ ] Model(s) — forecast / classification / clustering
- [ ] Dashboard (Streamlit / Power BI)
- [ ] Deployed service (if applicable)
- [ ] Executive readout / final presentation
- [ ] Demo video

## 🔑 Key Learnings (Overall)

*(Fill at the end — 3–5 bullets on what the internship taught you.)*
