# Credit Card Spend Analysis

# 💳 Customer Credit Card Spend Analysis Dashboard

This project presents a complete end-to-end solution for analyzing customer credit card behavior using PostgreSQL and Power BI. 

It combines SQL queries with business intelligence dashboards to extract insights from customer, spending, and repayment datasets.


## 🎯 Project Objectives

- To analyze consumer credit card usage patterns across demographics, cities, and card types.

- To understand product categories where customers spend the most.

- To identify repayment behavior and detect potential late-paying customers.

- To determine the average credit limit and age of credit card users.

- To build a dynamic Power BI dashboard to visualize KPIs and patterns effectively.

To support data-driven decisions for financial product offerings and customer segmentation.


## 📁 Dataset Overview

The project utilizes three CSV files representing different aspects of customer activity:


### 1. Customer Data

- `Columns:` num, customer_id, age, city, card_type, credit_limit, company, job_segment  

- `Purpose:` Stores customer demographics and credit card metadata.


### 2. Repayment Data

- `Columns:` sl_no, customer_id, date, amount  

- `Purpose:` Tracks repayment transactions for each customer.


### 3. Spend Data

- `Columns:` sl_no, customer_id, date, product_type, amount  

- `Purpose:` Captures product-wise spending by customers.



## 🛠️ Tools & Technologies Used

- **PostgreSQL / pgAdmin4** – For database creation, data manipulation, and SQL querying

- **Power BI** – For building an interactive dashboard

- **CSV Files** – As data source inputs



## 🧱 Database Setup

### 🔹 Step 1: Create Database
```sql
CREATE DATABASE credit_card_analysis;

🔹 Step 2: Create Tables

**Customer Table**

CREATE TABLE Customer (
    num SERIAL PRIMARY KEY,
    customer_id VARCHAR(10) UNIQUE NOT NULL,
    age INT NOT NULL,
    city VARCHAR(50) NOT NULL,
    card_type VARCHAR(20) NOT NULL,
    credit_limit NUMERIC(15, 2) NOT NULL,
    company VARCHAR(50),
    job_segment VARCHAR(50)
);


**Repayment Table**

CREATE TABLE Repayment (
    sl_no SERIAL PRIMARY KEY,
    customer_id VARCHAR(10) REFERENCES Customer(customer_id) ON DELETE CASCADE,
    date DATE NOT NULL,
    amount NUMERIC(15, 2) NOT NULL
);


**Spend Table**

CREATE TABLE Spend (
    sl_no SERIAL PRIMARY KEY,
    customer_id VARCHAR(10) REFERENCES Customer(customer_id) ON DELETE CASCADE,
    date DATE NOT NULL,
    product_type VARCHAR(50) NOT NULL,
    amount NUMERIC(15, 2) NOT NULL
);


🔹 Step 3: Data Import

Right-click on each table in pgAdmin > Import/Export and load the CSV files.


📊 Power BI Dashboard Features

The interactive dashboard includes:

# KPI Cards for Total Spend, Transactions, Avg Credit Limit, and Avg Age.

# Bar Charts showing: Avg Spend by Product Type

# Transactions by Product Type

# Customers by City

# Pie Charts for: Job Segment-wise Spend

# Card Type-wise Spend

# Line Chart for: Month-on-Month Transactions & Avg Spend

# Map Visual showing: City-wise Spend & Transactions


❓ Key Business Questions Answered with SQL

1) What is the average credit limit?

2) Which card type is most common?

3) What is the average age of card holders?

4) What is the most common spending category?

5) Month-wise spend trend?

6) Average spend per category?

7) Average monthly transaction volume?

8) Top 5 cities by spend?

9) Card-type-wise yearly spend?

10) Most used credit card type?

11) Average days to pay bills?

12) Rate of late-payers (30+ days)?

13) City-wise customer distribution?

14) Spending range (min–max) per customer?


✅ Insights

-- Gold cards are the most used (40.09%).

-- Clothes, Camera, and Movies are top spend categories.

-- Repayments are mostly on time, with few late payers.

-- Spending peaks in July and November.

-- Govt and Self-employed segments are major contributors.




