# Zillow Data Analytics Pipeline Using AWS Lambda and Redshift

## Project Overview
This project is designed to create an automated data analytics pipeline for Zillow data, utilizing AWS Lambda functions, Amazon Redshift, and Amazon QuickSight for dashboard creation. The pipeline leverages Apache Airflow to automate the entire process, ensuring seamless data ingestion, transformation, and visualization.

## Project Structure

### 1. Data Ingestion
- **Bucket 1**: 
  - **Description**: The first bucket serves as the entry point for raw data.
  - **Data Source**: Data is fetched from RapidApi using a Python script.
  - **AWS Lambda Function**: 
    - **Trigger**: Activated when new data enters the bucket.
    - **Action**: Sends the raw data to the second bucket.

### 2. Data Transformation
- **Bucket 2**: 
  - **Description**: This bucket handles data transformation and cleaning.
  - **AWS Lambda Function**: 
    - **Trigger**: Activated when new data enters the bucket.
    - **Action**: Transforms JSON data into CSV format, performs necessary data cleaning, and sends the cleaned data to the third bucket.

### 3. Data Loading and Visualization
- **Bucket 3**: 
  - **Description**: The final bucket stores the cleaned and transformed data.
  - **Data Ingestion to Amazon Redshift**: 
    - The cleaned data from the third bucket is ingested into Amazon Redshift.
- **Amazon QuickSight**: 
  - **Description**: Used for creating dashboards.
  - **Data Source**: Connects to Amazon Redshift to fetch and visualize data.

### 4. Pipeline Automation
- **Apache Airflow**: 
  - **Role**: Automates the entire pipeline process.
  - **Tasks**: Manages and schedules data ingestion, transformation, and loading tasks.

## Setup and Installation

### Prerequisites
- AWS account with necessary permissions for S3, Lambda, Redshift, and QuickSight.
- Python installed on your local machine.
- Apache Airflow installed and configured.

### Steps

1. **Create S3 Buckets**:
    - Create three S3 buckets to handle raw data, transformed data, and cleaned data.

2. **Setup AWS Lambda Functions**:
    - **Lambda Function 1**: Fetch data from RapidApi and upload to Bucket 1.
    - **Lambda Function 2**: Transform JSON to CSV, clean data, and upload to Bucket 2.

3. **Configure Amazon Redshift**:
    - Setup Amazon Redshift cluster.
    - Create necessary tables and schemas to store cleaned data.

4. **Connect Amazon QuickSight**:
    - Connect Amazon QuickSight to the Redshift cluster.
    - Create data visualizations and dashboards.

5. **Automate with Apache Airflow**:
    - Define Airflow DAG to automate the data pipeline.
    - Schedule tasks for data ingestion, transformation, and loading.

## Usage

1. **Data Ingestion**:
    - Trigger the first Lambda function manually or schedule it to run at regular intervals to fetch new data.

2. **Data Transformation**:
    - The second Lambda function is triggered automatically when new data arrives in Bucket 2.

3. **Data Loading and Visualization**:
    - Data is ingested into Amazon Redshift and visualized using Amazon QuickSight dashboards.

4. **Pipeline Automation**:
    - Apache Airflow handles the scheduling and execution of all tasks in the pipeline.

## Conclusion

This project provides a scalable and automated solution for Zillow data analytics using AWS services. By leveraging AWS Lambda, Amazon Redshift, and Apache Airflow, the pipeline ensures efficient data processing and insightful visualizations through Amazon QuickSight.

## Author
Vishnusai Bhadramraju


## Acknowledgments
- RapidApi for data access.
- AWS for providing the cloud infrastructure.
- The open-source community for Apache Airflow and other tools used in this project.

---
