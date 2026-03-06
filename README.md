# Data-Engineering-Real-World-Project-Ecommerce-Dataset
Step-by-step data engineering project using the Olist Brazilian E-Commerce dataset: ingestion &amp; exploration, cleaning, integration, optimization (cache), and data serving.



1️⃣ Data Understanding

The first step of the project is to understand the structure and contents of the dataset before building the data engineering pipeline.

This project uses the Olist Brazilian E-Commerce Public Dataset, which contains multiple CSV files representing different aspects of an e-commerce ecosystem such as:

Customers

Orders

Order Items

Payments

Reviews

Products

Sellers

Geolocation

Product Category Translation

Understanding these datasets is important before performing transformations, joins, and analytics.

Uploading the Dataset to Google Colab

The initial data exploration was performed in Google Colab.
The dataset was downloaded from Kaggle and extracted into the working directory.

Downloading the dataset

Extracting the dataset

Inspecting the dataset files

This step verifies that all CSV datasets are successfully extracted.

The dataset contains multiple CSV files including:

olist_customers_dataset.csv

olist_orders_dataset.csv

olist_order_items_dataset.csv

olist_order_payments_dataset.csv

olist_order_reviews_dataset.csv

olist_products_dataset.csv

olist_sellers_dataset.csv

olist_geolocation_dataset.csv

product_category_name_translation.csv

Creating a Spark Session

To process the dataset efficiently, a PySpark SparkSession was created.

The Spark session enables distributed data processing using Spark's DataFrame API.

Reading the Dataset with PySpark

The dataset was then loaded using Spark DataFrames with the following options:

header=True → ensures column headers are read correctly

inferSchema=True → automatically detects column data types

Inspecting the Dataset

After loading the dataset, the schema and sample records were inspected to understand the structure of the data.

Printing the Schema

This shows the data types and column structure of the dataset.

Previewing the Data

Displaying the first rows of the dataset helps verify that the data was loaded correctly.

Automating Dataset Inspection

Since the dataset contains multiple CSV files, repeating the same process manually would be inefficient.

To solve this, Gemini was used to help generate a PySpark script that automatically:

Lists all CSV files in the dataset directory

Iterates through each dataset

Loads each CSV file into a Spark DataFrame

Prints the schema

Displays sample rows

This significantly reduces repetitive work and ensures consistent inspection of all datasets.

Automation Code

Automated Output

The script successfully iterates through every dataset and displays its schema and sample rows.

Key Findings from Data Understanding

From the initial exploration:

The dataset contains 9 interconnected tables

Several tables contain timestamp fields related to purchase, approval, and delivery

Financial values such as price and freight_value are stored as numeric types

Many datasets share common keys such as:

customer_id

order_id

product_id

seller_id

These keys will be important later for data integration and aggregation.

2️⃣ Data Ingestion & Exploration

In the next stage of the project, the raw datasets will be ingested into a distributed processing environment.

The pipeline will use:

Google Cloud Dataproc

Hadoop Distributed File System (HDFS)

Spark clusters

The cluster architecture includes:

Master Node – manages the cluster and job scheduling

Worker Nodes – perform distributed parallel processing

Using a distributed cluster allows the pipeline to scale and process large datasets efficiently.

The next step will focus on:

Uploading datasets to HDFS

Running Spark jobs on the cluster

Performing distributed data exploration
