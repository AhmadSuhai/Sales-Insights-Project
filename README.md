# Sales-Insights-Project
Sales Insights Data Analysis Project

## 🧾 Project Scenario

A computer hardware business is facing challenges in a rapidly changing market. The sales director decides to invest in a **data analysis project** to gain real-time insights into sales performance. As a Data Analyst, your task is to work with sales and customer data using SQL and build a Power BI dashboard to visualize key business metrics.

---

## 🧰 Tools & Technologies

- **MySQL** – For data querying and manipulation
- **Power BI** – For dashboarding and data visualization
- **SQL** – Core language for data analysis

---

## 🗂️ Dataset Description

The dataset contains the following tables:
- `customers` – Customer details
- `transactions` – Sales records including currency, market code, etc.
- `date` – Date dimension for time-based filtering

---

🔍 SQL Analysis Tasks

Show all customer records:

sql
Copy
Edit
SELECT * FROM customers;
Show total number of customers:

sql
Copy
Edit
SELECT COUNT(*) FROM customers;
Show transactions for Chennai market (market code: Mark001):

sql
Copy
Edit
SELECT * FROM transactions WHERE market_code='Mark001';
Show distinct products sold in Chennai:

sql
Copy
Edit
SELECT DISTINCT product_code FROM transactions WHERE market_code='Mark001';
Show transactions where currency is USD:

sql
Copy
Edit
SELECT * FROM transactions WHERE currency="USD";
Show transactions for the year 2020 (join with date table):

sql
Copy
Edit
SELECT transactions.*, date.* 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020;
Show total revenue in 2020:

sql
Copy
Edit
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 
  AND (transactions.currency="INR\r" OR transactions.currency="USD\r");
Show revenue for January 2020:

sql
Copy
Edit
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND date.month_name="January" 
  AND (transactions.currency="INR\r" OR transactions.currency="USD\r");
Show total revenue in Chennai for 2020:

sql
Copy
Edit
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND transactions.market_code="Mark001";




📊 Power BI Dashboard
After data is cleaned and filtered using Power Query in Power BI, a new column norm_amount is created to normalize currency values:

powerquery
Copy
Edit
= Table.AddColumn(#"Filtered Rows", "norm_amount", 
each if [currency] = "USD" or [currency] ="USD#(cr)" 
then [sales_amount]*75 else [sales_amount], type any)
The Power BI dashboard includes visuals for:

Sales by region

Yearly/monthly sales performance

Currency-normalized revenue

Product performance trends

🎯 Project Outcome
By completing this project, you will:

Practice using SQL for real business analysis tasks

Learn to import and transform data for reporting

Build interactive dashboards in Power BI

Strengthen your portfolio for Data Analyst roles

👨‍💻 Author
Suhail Ahmad
💼 Aspiring Data Analyst | Passionate about data-driven solutions
📧 Email: suhailahdar68@gmail.com
🔗 LinkedIn


