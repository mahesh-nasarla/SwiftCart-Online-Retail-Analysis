# 🛍️ **SwiftCart Online Retail Analysis**

**🐍 Python | 🐼 Pandas | 🔢 NumPy | 📊 Matplotlib | 📈 Seaborn | 🔍 Exploratory Data Analysis**

An end-to-end retail data analysis project focused on understanding customer activity, product performance, recorded sales patterns, order outcomes, sales channels, and regional demand.

---

## 📌 **1. Project Overview**

SwiftCart is presented as an online retail business serving customers across cities and states in India. Its data includes customer details, products, quantities, recorded amounts, order status, shopping channels, and shipping locations.

The business challenge is not simply collecting this data; it is making sense of it. This project explores questions such as:

- Which product categories contribute most to the recorded amount?
- Which customer groups appear most often?
- Which channels and regions have higher activity?
- When is activity stronger or weaker?
- Which categories have more returns or cancellations?

I worked through the data preparation and exploratory analysis process using Python. The aim was to turn raw records into findings that a retail team could use when reviewing stock, promotions, customer engagement, and order experience.

## 📊 **2. Project at a Glance**

| **Item** | **Details** |
|---|---|
| Dataset | SwiftCart Online Retail Dataset |
| Final Dataset Size | 31,047 records × 21 columns |
| Unique SKUs | 5,287 |
| Product Categories | 8 |
| Sales Channels | 7 |
| Shipping States | 35 |
| Unique Non-Missing Customer IDs | 28,394 |
| Date Coverage | 4 January 2022 – 6 December 2022 |
| Currency | INR |

**Note:** Each row is treated as a dataset record. A record is not automatically the same as a unique order, because an order can appear in multiple rows and some order IDs are missing.

## 🧰 **3. Tools and Libraries**

- **Python:** Main programming language.
- **Pandas:** Data inspection, cleaning, grouping, pivot tables, and analysis.
- **NumPy:** Numerical operations and data handling.
- **Matplotlib:** Charts and visual exploration.
- **Seaborn:** Statistical plots and distribution comparisons.
- **Jupyter Notebook:** Analysis workflow and documentation.

## 🎯 **4. Business Questions**

The analysis was organised around practical retail questions:

- Who appears most often in the customer records, and how do age and gender groups differ?
- Which product categories, sizes, and SKUs have the most recorded activity?
- How is the recorded amount distributed across products, channels, states, and months?
- What share of records is delivered, returned, cancelled, or refunded?
- Are order outcomes different across product categories or customer groups?
- Does buying a larger quantity have a clear relationship with the recorded amount?

## ⚙️ **5. Project Workflow**

### 🔹 **5.1 Data Understanding**

I started by checking the dataset shape, column names, data types, summary statistics, unique values, and missing-value counts. This helped identify which fields were customer-related, product-related, numerical, categorical, date-based, or location-based.

The final dataset contains 21 columns, including customer ID, gender, age, age group, date, month, status, channel, SKU, category, size, quantity, amount, city, state, postal code, country, and B2B indicator.

📂 **Dataset Reference:** SwiftCart Online Retail Sales Dataset on Kaggle.

### 🧹 **5.2 Data Cleaning and Validation**

I used Pandas to prepare the data for analysis. The main checks and actions included:

- Standardised column names into snake_case and cleaned extra spaces and inconsistent text labels.
- Converted the date field from Excel serial values into a datetime format.
- Converted age values to numeric, treated ages above 100 as invalid, and filled remaining missing ages with the median age of 37.
- Filled missing gender values as `Unknown` and completed missing age-group labels using the available age-related pattern.
- Recovered some missing customer IDs where the order ID structure provided a usable identifier; 41 customer IDs remained missing.
- Kept 1,080 missing order IDs as missing rather than creating IDs that could not be verified.
- Standardised state and city labels, including mapping NEW DELHI to DELHI.
- Checked postal-code format and set 10 malformed values to missing.
- Checked quantity and amount ranges, currency, country, and exact duplicate rows.

**✅ Data Validation Results**

| **Check** | **Final Result** |
|---|---:|
| Dataset Shape | 31,047 × 21 |
| Exact Duplicate Rows | 0 |
| Remaining Missing Cells | 2,084 |
| Age Range | 18–78 |
| Quantity Range | 1–20 |
| Recorded Amount Range | ₹229–₹3,036 |
| Currency / Country | INR / IN across all records |

The 2,084 remaining missing cells are in `order_id` (1,080), `customer_id` (41), `date` (488), `month` (465), and `ship_postal_code` (10). I left values missing when there was no reliable source to recover them.

### 📉 **5.3 Outlier Review**

I used the Interquartile Range (IQR) method and box plots to flag unusual values in age, quantity, and amount.

| **Column** | **Flagged Records** | **Decision** |
|---|---:|---|
| Age | 600 | Retained; ages 76–78 may be valid |
| Quantity | 171 | Retained; the IQR is zero because most records have quantity 1 |
| Amount | 1,115 | Retained; higher-value purchases may be genuine |

The flagged values were not removed simply because they were outside the IQR limits. A statistical flag alone does not prove that a record is incorrect.

### 🔍 **5.4 Exploratory Data Analysis (EDA)**

After preparing the cleaned dataset, I explored the business from several angles:

- **Descriptive Analysis:** Mean, median, standard deviation, range, quartiles, percentiles, variance, and skewness.
- **Customer Analysis:** Gender, age groups, customer ID frequency, customer segments, B2B/non-B2B activity, and city/state distribution.
- **Product Analysis:** Category performance, size distribution, product demand, SKU frequency, and average recorded amount by category.
- **Sales Analysis:** Total and average recorded amount, monthly trends, channel contribution, and geographic performance.
- **Order Analysis:** Order ID frequency, order status, quantity patterns, and monthly order outcomes.
- **Time-Based Analysis:** Date coverage, monthly activity, daily patterns, and customer/order activity over time.
- **Group-Based Analysis:** Comparisons by category, gender, age group, channel, state, and order status.
- **Pivot Tables and Crosstabs:** Comparisons such as month by status, age group by gender, category by size, channel by gender, and state by channel.
- **Relationship Analysis:** Numerical-versus-numerical, numerical-versus-categorical, and categorical-versus-categorical comparisons.

### 📊 **5.5 Data Visualization and Storytelling**

I used Matplotlib and Seaborn to create charts that answer specific questions rather than adding visuals just for appearance.

The visualisation notebook includes:

- Histograms for transaction amount distribution.
- Box plots for amount by order status.
- Scatter plots for quantity versus amount.
- Count plots for order status.
- Bar charts for category-wise recorded amount.
- Line charts for monthly recorded amount.
- Correlation heatmaps for numerical variables.
- Violin plots for amount distribution across categories.

For the main charts, I documented the observation, what it means for the business, and a practical action the business could test.

## 💡 **6. Key Findings**

The following findings come from the cleaned dataset and the analysis notebooks.

| **Area** | **Finding** |
|---|---|
| Customers | Women account for 20,813 records (67.04%). Men have a higher average recorded amount per record (₹800.75) than women (₹628.31). |
| Age Groups | Adults account for 15,560 records (50.12%) and the highest total recorded amount (₹1.06 crore). Average recorded amounts are close across age groups. |
| Products | Sets lead with 12,391 records and ₹1.05 crore in recorded amount; Kurtas follow with 10,446 records and ₹49.59 lakh. |
| Sizes | M is the most frequently recorded size (5,485), followed by L (5,144) and XL (4,437). |
| Sales | Total recorded amount is ₹2,11,76,377 (about ₹2.12 crore). The average is ₹682.07 and the median is ₹646 per record. |
| Channels | Amazon leads with 11,016 records and ₹75.20 lakh in recorded amount, followed by Myntra and Flipkart. |
| Orders | 28,641 records (92.25%) are Delivered; 1,045 are Returned, 844 Cancelled, and 517 Refunded. |
| Time | March has the highest monthly recorded amount (₹19.09 lakh); November has the lowest (₹15.92 lakh). |
| Geography | Maharashtra leads with ₹29.90 lakh, followed by Karnataka with ₹26.46 lakh. Bengaluru has the highest city record count (2,673). |
| Relationships | Quantity and amount have a very weak positive correlation (0.054); quantity alone does not explain recorded amount. |

### 🔎 **6.1 Order and Category Patterns Worth Reviewing**

- **Bottom:** Highest category-level cancellation rate (6.41%) and return rate (7.69%).
- **Western Dress:** Highest refund rate (3.05%) and a return rate of 6.64%.
- **Sets:** Highest delivery share (94.96%) in the category-versus-status crosstab.
- **Amazon:** Has the highest counts across channels for delivered, returned, cancelled, and refunded records. This reflects its larger record volume, so channel comparisons should consider rates as well as counts.

## 🚀 **7. Business Recommendations**

Based on the findings, these are practical actions SwiftCart could test and measure:

1. **📦 Plan Inventory Around Demand:** Give priority to Sets and Kurtas and use the size-level results to guide stock planning, especially for M, L, and XL.

2. **🔍 Investigate Returns Before Changing Stock:** Review sizing details, product descriptions, quality feedback, and return reasons for Bottom and Western Dress.

3. **🛒 Protect Leading Channels:** Maintain product availability and strong listings on Amazon, Myntra, and Flipkart. Review return and cancellation rates—not just counts—before changing channel budgets.

4. **📅 Test Offers in Weaker Months:** Review what contributed to March's stronger recorded amount and test focused campaigns during November. Compare campaign results with a baseline before scaling them.

5. **📍 Focus Regional Tests:** Maintain availability in Maharashtra and Karnataka and test local campaigns in cities such as Bengaluru and Hyderabad. Use conversion and delivery data before expanding to lower-activity locations.

6. **👥 Use Customer Segments Carefully:** Continue serving the largest recorded customer groups, while testing higher-value product recommendations for men. Evaluate the results rather than assuming the segment differences will hold for every campaign.

**Note:** These are recommendations to test, not results from campaigns already run.

## 📁 **8. Project Files**

The project materials can be organised in the repository like this:

```text
SwiftCart-Online-Retail-Analysis/
│
├── notebooks/
│   ├── swiftcart_Datacleaning.ipynb
│   ├── Swiftcart_dataset_Analysis.ipynb
│   └── Visualization_swiftcart.ipynb
│
├── data/
│   └── SwiftCart_Cleaned_Dataset.csv
│
├── reports/
│   ├── SwiftCart_Data_Quality_Validation_Report.pdf
│   └── SwiftCart_Business_Insights_Report.pdf
│
├── presentation/
│   └── SwiftCart_Project_Presentation.pptx
│
└── README.md
```

Use the final filenames that you upload to GitHub. The notebooks currently refer to input files by name, so update the file paths in the first data-loading cells if you place the files in different folders.

## ▶️ **9. How to Run**

1. Clone or download the repository.
2. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

3. Place the raw dataset where the cleaning notebook can access it. The cleaning notebook currently reads `swiftcart_store_data.csv`.
4. Run `swiftcart_Datacleaning.ipynb` from top to bottom. It saves the cleaned output as `SwiftCart_Cleaned_Dataset.csv`.
5. Make sure the cleaned CSV is available to the analysis and visualisation notebooks. Both use `SwiftCart_Cleaned_Dataset.csv` as their input.
6. Run `Swiftcart_dataset_Analysis.ipynb` and `Visualization_swiftcart.ipynb` to review the EDA outputs and charts.

**⚠️ File-format Note:** The cleaned dataset file shared with this project has a `.xls` filename but contains CSV-formatted text. Save or rename it as `SwiftCart_Cleaned_Dataset.csv` before using it with the notebooks' `pd.read_csv()` commands.

## ⚠️ **10. Scope and Limitations**

- The completed work documented here covers data understanding, cleaning and validation, descriptive analysis, EDA, visualisation, and business recommendations.
- The uploaded materials do not show completed hypothesis tests, confidence interval analysis, forecasting, or a full feature-engineering stage.
- These are useful next steps, but are not presented as completed work.
- The total amount of ₹2.12 crore is the sum of the amount column across all records and statuses. It is a recorded amount, not verified net sales, revenue after returns, or profit.
- Record counts should not be described as unique order counts. The dataset has 27,555 non-missing order IDs and 1,080 missing order IDs; some order IDs appear on multiple rows.
- Customer-level conclusions should also account for 41 missing customer IDs and the possibility that multiple rows relate to one order.
- Date-based results should be read with care because 488 records have unavailable dates and 465 have unavailable month labels.
- The analysis is based on the fields available in this dataset. It does not contain stock-on-hand, website traffic, advertising spend, product cost, or customer feedback, so it cannot directly measure stockouts, conversion, campaign ROI, or profit.

## 📚 **11. What I Learned**

This project gave me practical experience in taking a dataset from its raw form through cleaning, validation, exploration, and visual explanation.

I practised using Pandas to investigate and prepare data, choosing charts based on the question, comparing groups with pivots and crosstabs, and explaining what a result could mean for a business.

The main lesson was to go beyond describing a chart: check what the data supports, be clear about its limitations, and suggest a business action that can be tested.

---

### 🏁 **Project Summary**

**Project:** SwiftCart Online Retail Analysis

**Focus:** Python-based data cleaning, exploratory data analysis, visualisation, and business insights
