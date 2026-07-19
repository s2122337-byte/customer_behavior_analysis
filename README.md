# Customer Shopping Behavior Analysis

End-to-end data analysis project covering data cleaning, database storage, SQL analysis, and dashboard visualization for a customer shopping behavior dataset of 3,900 records.

## 🔧 Workflow

```
CSV Data → Pandas (Cleaning & Feature Engineering) → PostgreSQL (Storage) → SQL (Analysis) → Power BI (Visualization)
```

## 📁 Project Structure

```
├── customer_shopping_behavior.csv       # Raw dataset (3,900 rows, 18 columns)
├── customer_behavior_analysis.ipynb     # Data cleaning & PostgreSQL loading (Pandas)
├── customer_behavior.sql                # 10 business-question SQL queries
├── customer_behavior_analysis.pbix      # Power BI dashboard
└── README.md
```

## 🗂 Dataset

The dataset contains customer transaction records with the following attributes:
Customer ID, Age, Gender, Item Purchased, Category, Purchase Amount, Location, Size, Color, Season, Review Rating, Subscription Status, Shipping Type, Discount Applied, Previous Purchases, Payment Method, and Frequency of Purchases.

## 🧹 Data Cleaning (Pandas)

- Filled missing `review_rating` values using category-wise median
- Standardized column names (lowercase, underscores)
- Engineered `age_group` (Young Adult / Adult / Middle-aged / Senior) using quartile binning
- Converted `frequency_of_purchases` into a numeric `purchase_frequency_days` field
- Dropped the redundant `promo_code_used` column (identical to `discount_applied`)
- Loaded the cleaned dataset into PostgreSQL using SQLAlchemy's `to_sql()`

## 🗄 Database

PostgreSQL database: `customer_behavior`, table: `customer`

## 📊 SQL Analysis — Business Questions

1. Total revenue: Male vs Female customers
2. Customers using a discount who still spent above the average
3. Top 5 products by average review rating
4. Average purchase amount: Standard vs Express shipping
5. Average spend & revenue: Subscribers vs Non-subscribers
6. Top 5 products by discount usage rate
7. Customer segmentation — New / Returning / Loyal
8. Top 3 products per category
9. Subscription status among repeat buyers (>5 purchases)
10. Revenue contribution by age group

## 📈 Dashboard

The cleaned dataset was connected to **Power BI** to build an interactive dashboard covering revenue trends, customer segments, product performance, and discount behavior.

## 🛠 Tech Stack

| Stage | Tool |
|---|---|
| Data Cleaning & Feature Engineering | Python (Pandas), Jupyter Notebook |
| Database | PostgreSQL |
| Analysis | SQL |
| Visualization | Power BI |

## ⚙️ Setup

1. Clone the repository
   ```bash
   git clone <repo-url>
   cd customer-shopping-behavior-analysis
   ```
2. Install dependencies
   ```bash
   pip install pandas sqlalchemy psycopg2-binary
   ```
3. Set your PostgreSQL password as an environment variable (never hardcode it):
   ```bash
   # Windows PowerShell
   $env:PG_PASSWORD="your_password"

   # macOS/Linux
   export PG_PASSWORD="your_password"
   ```
4. Run `customer_behavior_analysis.ipynb` to clean the data and load it into PostgreSQL.
5. Run the queries in `customer_behavior.sql` against the `customer` table.
6. Open `customer_behavior_analysis.pbix` in Power BI Desktop to explore the dashboard.

## 📌 Note

Database credentials are read from environment variables and are **not** stored in the code.
