
---

# 📊 [Python] Analyzing Churned User Behaviors of an E-commerce Platform  
  
Author: Catherine Vu

Date: 12/06/2026  

Tools Used: Python  

---

## 📑 Table of Contents  
1. [📌 Background & Overview](#-background--overview)  
2. [📂 Dataset Description & Data Structure](#-dataset-description--data-structure)
4. [🔎 Final Conclusion & Recommendations](#-final-conclusion--recommendations)

---

## 📌 Background & Overview  

### 🎯 Business questions:
An e-commerce company is experiencing customer churn and wants to understand **who is leaving and why** — in order to design targeted retention campaigns before users disengage completely.

**Main business question:**
> *"What behaviors and characteristics define churned users, and what can the company do to reduce churn?"*

***This project uses Python to:***

✔️ Identify the key behaviors and characteristics that define churned users  
✔️ Provide actionable recommendations to reduce customer churn

### 👤 Who is this project for?  

This project is relevant for:

- **Marketing & CRM teams** — to identify at-risk customer segments and design targeted retention campaigns or promotions.
- **Business analysts & data teams** — as a foundation for building a churn prediction model in future phases.
- **Senior management** — to understand the scale of churn risk and prioritize retention as a business objective.

---

## 📂 Dataset Description & Data Structure  

### 📌 Data Source  
- Source: [Ecommerce Customer Churn Analysis](https://www.kaggle.com/datasets/ankitverma2010/ecommerce-customer-churn-analysis-and-prediction/data) (Kaggle)
- Size: 5630 rows and 20 columns  
- Format: .xlsx  

### 📊 Data Structure & Relationships  

#### 1️⃣ Tables Used:  
- **Table:** E Comm 

#### 2️⃣ Table Schema & Data Snapshot  

Table: E Comm

<details>
<summary>Click to view table schema</summary>

| Column Name | Data Type | Description |
|---|---|---|
| CustomerID | Integer | Unique identifier for each customer |
| **Churn** | Integer | Target variable — whether the customer has **churned (1) or not (0)** |
| Tenure | Float | Number of months the customer has been with the company |
| PreferredLoginDevice | Text | Device the customer most often uses to log in (Mobile Phone, Computer, etc.) |
| CityTier | Integer | Tier classification of the customer's city (1, 2, or 3) |
| WarehouseToHome | Float | Distance between warehouse and customer's home |
| PreferredPaymentMode | Text | Customer's preferred payment method (Credit Card, COD, etc.) |
| Gender | Text | Customer's gender |
| HourSpendOnApp | Float | Average number of hours spent on the app/website |
| NumberOfDeviceRegistered | Integer | Number of devices registered to the customer's account |
| PreferedOrderCat | Text | Customer's preferred order category (Mobile, Grocery, etc.) |
| SatisfactionScore | Integer | Customer's satisfaction rating |
| MaritalStatus | Text | Customer's marital status (Married, Single, etc.) |
| NumberOfAddress | Integer | Number of addresses registered by the customer |
| Complain | Integer | Whether the customer raised a complaint in the last month (1) or not (0) |
| OrderAmountHikeFromlastYear | Float | Percentage increase in order amount compared to last year |
| CouponUsed | Float | Number of coupons used by the customer |
| OrderCount | Float | Total number of orders placed by the customer |
| DaySinceLastOrder | Float | Number of days since the customer's last order |
| CashbackAmount | Float | Average cashback amount received by the customer |

</details>

---

## ⚒️ Main Process

1️⃣ **Data Cleaning & Preprocessing**
#### Step 1.1 — Load data & initial exploration
**Purpose:** Load the dataset and get a first look at its structure, size, and data types.

<img width="1408" height="243" alt="1 1a" src="https://github.com/user-attachments/assets/78806f1d-61f7-4a5a-a9c7-d696eafacbaa" />
<img width="3599" height="575" alt="1 1b" src="https://github.com/user-attachments/assets/9514f641-1dd6-4821-9007-66089c9aaee9" />
<img width="1209" height="1153" alt="1 1c" src="https://github.com/user-attachments/assets/9ae438d3-9648-4946-b5c6-e733821ccd4f" />

**Observation:** The dataset contains 5,630 rows and 20 columns. All column data types are appropriate for their content.


#### Step 1.2 — Check for missing values
**Purpose:** Identify which columns contain missing values before deciding how to handle them.

<img width="602" height="1366" alt="1 2a" src="https://github.com/user-attachments/assets/ddc3fac6-6337-4cec-ac53-89966b7692d2" />

**Observation:** 7 columns contain missing values: Tenure, WarehouseToHome, HourSpendOnApp, OrderAmountHikeFromlastYear, CouponUsed, OrderCount, DaySinceLastOrder.


#### Step 1.3 — Handle missing values
**Purpose:** Decide on a strategy to deal with missing values — either dropping rows or filling them — based on how significant the missing data is.

<img width="2075" height="617" alt="1 3a" src="https://github.com/user-attachments/assets/bea92869-8811-4b81-b330-5b10b4a1e0e1" />
<img width="992" height="1361" alt="1 3b" src="https://github.com/user-attachments/assets/2c7ea6d1-7083-42cf-b70d-e3b236198616" />

**Observation:** The total number of rows with missing values falls below the 5% threshold typically used to justify dropping rows. Since the missing row percentage is higher than that, median imputation was used to preserve sample size for analysis.


#### Step 1.4 — Check for duplicates
**Purpose:** Identify duplicate customer records that could skew statistical measures and analysis results.

<img width="3596" height="213" alt="1 4" src="https://github.com/user-attachments/assets/252ef4d4-9905-4b54-a55a-b4e76e9d1dbb" />

**Observation:** No duplicate CustomerID found in the dataset.


2️⃣ **Exploratory Data Analysis (EDA)**
#### Step 2.1 — Descriptive statistics overview
**Purpose:** Get a statistical summary (mean, median, min, max, std) of all numerical variables.
<img width="3598" height="600" alt="2 1" src="https://github.com/user-attachments/assets/4d060ae3-58a8-4322-bef3-938ef7dd3795" />


#### Step 2.2 — Distribution of numerical variables
**Purpose:** Visualize the distribution and detect outliers in 7 key numerical variables using box plots.

<img width="1013" height="453" alt="2 2a" src="https://github.com/user-attachments/assets/52da991b-74b9-4dfa-b6a2-89c437923a59" />
<img width="2831" height="936" alt="2 2b" src="https://github.com/user-attachments/assets/dfb80c9b-eec9-456d-922a-ab09e6a9b01c" />
<img width="2815" height="911" alt="2 2c" src="https://github.com/user-attachments/assets/254a4cd1-10e9-45a1-8f83-577d33905286" />
<img width="2849" height="904" alt="2 2d" src="https://github.com/user-attachments/assets/b71a0684-e72c-4622-807b-24eddac8bc70" />

**Observation:** All numerical values are positive, which is expected given the nature of the data (e.g. tenure in months, distance, order count cannot be negative). Outliers are present but are considered reasonable and reflective of real customer behavior — no further action required for numerical variables.


#### Step 2.3 — Distribution of categorical variables
**Purpose:** Visualize the frequency distribution of categorical variables using bar charts to understand customer segment composition and detect any data inconsistencies.

<img width="1169" height="533" alt="2 3" src="https://github.com/user-attachments/assets/e00bee6b-0e51-43a9-99f9-53b0105b5e17" />
<img width="3557" height="845" alt="2 3b" src="https://github.com/user-attachments/assets/195f2cde-b4d3-42a4-adac-baff5cbc3969" />
<img width="3561" height="917" alt="2 3c" src="https://github.com/user-attachments/assets/6a5e5251-6493-4f5b-9125-ccd5eba1019d" />
<img width="3561" height="953" alt="2 3d" src="https://github.com/user-attachments/assets/bacafff3-5294-452d-9ff3-fa4aff9c94c5" />
<img width="3554" height="780" alt="2 3e" src="https://github.com/user-attachments/assets/8eb6c6a5-68d8-4c65-9eb2-504735060d38" />

**Observation:** Found inconsistent labeling in 2 columns — "Phone" and "Mobile Phone" in PreferredLoginDevice; "Mobile" and "Mobile Phone" in PreferedOrderCat. These were standardized before re-plotting to ensure accurate distribution analysis.

3️⃣ Churn Analysis — Relationship with Target Variable

#### Step 3.1 — Numerical variables vs. Churn (box plots)
**Purpose:** Compare the distribution of each numerical variable between churned and non-churned customers to identify which variables differ meaningfully.
<img width="901" height="346" alt="3 1" src="https://github.com/user-attachments/assets/5b393cfe-37af-431f-97b0-82896b38d665" />
<img width="3192" height="890" alt="3 1a" src="https://github.com/user-attachments/assets/fbb6c6e7-6666-493e-bc99-d44a4c8f211d" />
<img width="3130" height="826" alt="3 1b" src="https://github.com/user-attachments/assets/37dacda1-e1b8-4739-aefa-1fc2e9865b71" />
<img width="3150" height="841" alt="3 1c" src="https://github.com/user-attachments/assets/e73ebd71-67a4-4332-bd19-8e60680c257a" />

**Observation:** Tenure shows the clearest separation between groups — churned customers tend to have low tenure (roughly 1–8 months). Other numerical variables show no meaningful difference between the two groups.

  
#### Step 3.2 — Categorical variables vs. Churn (stacked bar charts)
**Purpose:** Examine churn rate (%) within each category of every categorical variable to identify high-risk customer segments.

<img width="1128" height="411" alt="3 2" src="https://github.com/user-attachments/assets/60c7496c-7aae-45b1-96c2-c24479f03cf8" />
<img width="2801" height="766" alt="3 2a" src="https://github.com/user-attachments/assets/fedc69cf-c6a2-4472-baa9-559fb4eeb8ad" />
<img width="2780" height="789" alt="3 2b" src="https://github.com/user-attachments/assets/33a36a03-ffee-4976-811e-86da14de7873" />
<img width="2777" height="801" alt="3 2c" src="https://github.com/user-attachments/assets/a9736957-e09a-4e1b-90b3-63dde26e533a" />
<img width="2782" height="726" alt="3 2d" src="https://github.com/user-attachments/assets/6ef45caf-f1f0-47ed-84d0-bb09292fe79d" />

**Observation:** Higher churn rates were found among customers who: pay via COD or E-wallet, have 5–6+ registered devices, prefer the Mobile Phone category, are Single, and have filed a complaint.


#### Step 3.3 — Correlation heatmap
**Purpose:** Quantify the strength and direction of relationships between all numerical variables and churn.

<img width="955" height="185" alt="3 3" src="https://github.com/user-attachments/assets/a195a58f-1393-4e18-81de-bef51fbc758b" />
<img width="1248" height="1036" alt="3 3a" src="https://github.com/user-attachments/assets/e2a54a59-8deb-466a-a028-0e12d6f0eac4" />

**Observation:** Tenure shows the strongest negative correlation with churn (r = -0.35) — confirming that lower tenure means higher churn risk. Complain shows a moderate positive correlation with churn (r = 0.25) — consistent with the pattern observed in Step 3.2

---

## 🔎 Final Conclusion & Recommendations  

👉🏻 Based on the insights and findings above, we would recommend the **Marketing & CRM teams** to consider the following:  

📍 Key Takeaways:  
✔️ **Prioritize retaining new customers (Low Tenure):**
- Tenure is the strongest predictor of churn — customers in their first 6 months carry the highest churn risk.
- Launch a dedicated onboarding program with special incentives during the first 3 months to build early loyalty.
- Focus retention efforts on Single customers, who show a disproportionately higher churn rate compared to other 
  marital status groups.

✔️ **Resolve complaints faster:**
- Customers who filed a complaint churn at approximately 3x the rate of those who didn't — making complaint handling a critical retention lever.
- Reduce complaint response time and implement a structured follow-up process after resolution to rebuild customer trust.

✔️ **Re-engage Mobile Phone category buyers**
- Customers who prefer the Mobile Phone category show a higher churn rate — suggesting they may make a one-time purchase and disengage before developing a shopping habit.
- Introduce post-purchase promotions (e.g. discount on next order, accessory bundles) in the days following a Mobile Phone purchase to encourage repeat engagement and build long-term shopping habits on the platform.

