# AWS Core Services Hands-on (ITCS 6190 / 8190 - Cloud Computing for Data Analysis)

## 📘 Overview
This hands-on project explores the **core AWS services**—**Amazon S3**, **AWS Glue**, **Amazon CloudWatch**, and **Amazon Athena**—to perform data analysis on an e-commerce dataset.  
The main goal is to create an end-to-end data workflow that loads raw data into AWS, processes it, and queries it for insights.

---

## 🧩 Services Used
- **Amazon S3** – Stores raw and processed data.
- **AWS Glue** – Crawls and catalogs the dataset into a structured schema.
- **AWS CloudWatch** – Monitors the Glue crawler execution and job logs.
- **Amazon Athena** – Queries the cataloged data directly from S3 using SQL.

---

## 🗂️ Dataset
**Source:** [Unlock Profits with E-Commerce Sales Data (Kaggle)](https://www.kaggle.com/datasets/thedevastator/unlock-profits-with-e-commerce-sales-data)

The dataset includes transaction-level sales data for various products, categories, and regions—ideal for analytics on profitability, growth, and sales patterns.

---

## ⚙️ Workflow Steps

### 1. **Amazon S3 Configuration**
- Create two buckets:
  - `raw-data-bucket`: To store the uploaded CSV dataset.
  - `processed-data-bucket`: To store the transformed or queried data.
- Upload the CSV dataset to the raw data bucket.

### 2. **IAM Role Setup**
- Create an **IAM Role** with the following permissions:
  - `AmazonS3FullAccess`
  - `AWSGlueServiceRole`
- Assign this role to the Glue crawler to allow access to S3 and Glue services.

### 3. **AWS Glue Crawler**
- Create a **Glue Crawler**:
  - Data source: `raw-data-bucket`
  - Target: AWS Glue Data Catalog
  - IAM role: The role created in the previous step.
- Run the crawler to automatically detect schema and create a table in the Glue Data Catalog.

### 4. **Monitoring with CloudWatch**
- Open **Amazon CloudWatch** to:
  - Monitor the Glue crawler execution logs.
  - Check for any errors or warnings during data crawling.

### 5. **Athena Query Execution**
- In **Amazon Athena**, select the database created by the Glue crawler.
- Run SQL queries on the table to analyze sales performance and profitability.

---

### Screenshots
<img width="1440" height="900" alt="Screenshot 2025-10-28 at 1 52 57 PM" src="https://github.com/user-attachments/assets/c7c122d7-6eea-4fa2-9d1f-c25b48642703" />
<img width="1440" height="900" alt="Screenshot 2025-10-28 at 1 53 34 PM" src="https://github.com/user-attachments/assets/62da6bef-f6b5-4c5f-9550-a81f9aab2291" />
<img width="1440" height="900" alt="Screenshot 2025-10-28 at 12 24 58 PM" src="https://github.com/user-attachments/assets/5da5911c-b5c5-4062-b114-a9f26431bf9d" />
<img width="1440" height="900" alt="Screenshot 2025-10-28 at 12 25 09 PM" src="https://github.com/user-attachments/assets/7fa429cb-b839-4cf0-84ae-f104b353f5a5" />






## 🧮 Queries Executed in Athena

Each query includes a `LIMIT 10` condition to restrict the output for review.

1. **Cumulative Sales Over Time (Specific Year)**  
   Calculate the running total of sales per day for a given year.

2. **Geographic "Hotspot" Analysis for Unprofitable Products**  
   Identify states with the highest negative profits.

3. **Impact of Discounts on Profitability by Sub-Category**  
   Analyze how discount levels affect profit margins per sub-category.

4. **Top 3 Most Profitable Products Within Each Category**  
   Rank products by total profit using a window function.

5. **Monthly Sales and Profit Growth Analysis**  
   Compute monthly totals and growth rates for sales and profits.

---

## 📂 Project Structure

```
CLOUD-HANDSON-AWSCLOUDSERVICES/
├── Output CSV Files/           # Query results exported from Athena
│   ├── query1_cumulative_sales.csv
│   ├── query2_unprofitable_hotspots.csv
│   ├── query3_discounts_profitability.csv
│   ├── query4_top3_profitable_products.csv
│   └── query5_monthly_growth.csv
├── CSV Files Screenshots.zip   # Screenshots of S3, IAM, CloudWatch, and Athena
├── Cloud HandsOn AWS Web Services.pdf  # Detailed project documentation
└── README.md                   # Project overview (this file)
```

---

## 📊 Results
All query results have been exported as **CSV files** and are available in the `Output CSV Files/` folder. Each file corresponds to one of the five analytical queries executed in Amazon Athena.

---

## 📸 Screenshots
Screenshots demonstrating each step of the AWS workflow are included in `CSV Files Screenshots.zip`:
- **S3 Buckets** (raw and processed data buckets)
- **IAM Role Configuration** (permissions for Glue)
- **AWS Glue Crawler** (data catalog creation)
- **CloudWatch Logs** (crawler execution monitoring)
- **Athena Query Execution** (SQL queries and sample outputs)

---

## 🧠 Key Learnings
- Practical understanding of AWS data analytics pipeline setup.
- Hands-on experience integrating S3, Glue, and Athena.
- Ability to monitor AWS services using CloudWatch.
- SQL proficiency for analytical queries on semi-structured data.
- Understanding of serverless, scalable data processing architectures.

---

## 📤 Submission Contents
This GitHub repository includes:
- ✅ SQL query results (CSV files in `Output CSV Files/`)
- ✅ Screenshots (compressed in `CSV Files Screenshots.zip`)
- ✅ Comprehensive project documentation (`Cloud HandsOn AWS Web Services.pdf`)
- ✅ This README file explaining the approach and workflow

---

## 🧑‍🏫 Course Information
**Course:** ITCS 6190 / 8190 – Cloud Computing for Data Analysis  
**Instructor:** Marco Vieira  
**Semester:** Fall 2025

---

## 🎯 Conclusion
This project demonstrates how AWS core services work together to simplify large-scale data ingestion, transformation, and analysis. Through S3, Glue, CloudWatch, and Athena, we established a **serverless data analytics pipeline** that is both cost-effective and scalable—essential skills for modern cloud-based data engineering and analysis.
