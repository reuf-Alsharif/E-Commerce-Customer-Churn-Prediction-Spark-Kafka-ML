# E-Commerce Customer Churn Prediction

**A Big Data Analytics Pipeline Using Apache Spark, Kafka-Based Streaming Simulation, and Machine Learning**

## Project Overview

This project presents a Big Data solution for analyzing e-commerce customer behavior and identifying users at risk of churn. It processes approximately **2.76 million behavioral events** to uncover customer engagement patterns, analyze cart abandonment, and support data-driven retention strategies.

The system integrates distributed data processing, simulated streaming ingestion, machine learning, and Power BI visualization within a seven-layer Big Data architecture.

## Project Objectives

- Process large-scale e-commerce behavioral data using Apache Spark.
- Simulate streaming data ingestion through a Kafka-inspired producer.
- Engineer customer-level behavioral features for churn risk analysis.
- Compare machine learning models for customer risk classification.
- Identify conversion bottlenecks and cart abandonment patterns.
- Develop business insights and projected retention campaign outcomes through Power BI dashboards.

## Dataset

The project uses the publicly available [RetailRocket E-Commerce Dataset on Kaggle](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset).

| Attribute | Description |
|---|---|
| Total events | Approximately 2.76 million |
| Unique users | 1,407,580 |
| File format | CSV |
| Data period | May–June 2015 |
| Event types | View, Add to Cart, Transaction |

The dataset captures customer interactions with e-commerce products and supports behavioral analysis and user-level feature engineering.

## Big Data Architecture

The pipeline is organized into seven layers:

1. **Data Source:** RetailRocket e-commerce event data.
2. **Data Ingestion:** Kafka-based streaming simulation using `MockKafkaProducer`.
3. **Raw Storage:** Parquet files for compressed, columnar storage.
4. **Distributed Processing:** Apache Spark for data cleaning, aggregation, and feature engineering.
5. **Processed Storage:** MockMongoDB implementation for demonstrating document-oriented storage.
6. **Analytics & Machine Learning:** Spark MLlib for churn risk classification.
7. **Output Generation:** CSV exports for Power BI dashboards.

## Methodology

### Data Processing and Feature Engineering

Apache Spark processes the event data and aggregates interactions at the user level. Behavioral features include event counts, views, cart additions, purchase counts, unique items viewed, conversion rates, and engagement scores.

The original CSV file was approximately 90 MB. Converting it to Parquet reduced the file size to approximately 34 MB, achieving **61.6% compression**.

### Customer Churn Risk Segmentation

Users are grouped into four behavioral risk categories:

- **High Risk:** Users who added products to their carts but did not complete purchases.
- **Medium Risk:** Users who viewed multiple products without adding items to their carts.
- **Low Risk:** Users who completed at least one transaction.
- **Unknown Risk:** Users with insufficient behavioral activity for reliable classification.

### Machine Learning

Three classification models were evaluated using Spark MLlib:

- Logistic Regression
- Decision Tree
- Random Forest

The Random Forest model achieved the strongest reported performance, with approximately **99% accuracy and a 0.99 F1-score**. View count and engagement score were the most influential features reported in the analysis.

## Key Findings

- **2.76M behavioral events** processed across approximately 1.4 million users.
- **27K high-risk users** identified for potential retention campaigns.
- **2.69% view-to-cart conversion rate**, highlighting a major conversion bottleneck.
- **69% cart abandonment rate** reported in the analysis.
- **61.6% storage reduction** achieved through Parquet conversion.
- **12 minutes and 34 seconds** reported for total pipeline execution.
- **1,769% projected ROI** for a hypothetical targeted retention campaign, based on the report's assumptions.

*Business impact and ROI figures are projections, not measured results from a live campaign. Model metrics reflect the reported experimental setup.*

## Visualization and Business Intelligence

Seven CSV outputs were prepared for Power BI, supporting dashboard analysis of:

- Customer behavior and daily activity
- Conversion funnel performance
- Churn risk segmentation
- Cart abandonment statistics
- Machine learning model comparison
- Business impact and projected revenue recovery
- Risk-based retention recommendations

## Technology Stack

- **Programming:** Python
- **Big Data Processing:** Apache Spark 3.5.1, PySpark
- **Storage:** Parquet, MockMongoDB
- **Streaming Simulation:** MockKafkaProducer
- **Machine Learning:** Spark MLlib
- **Data Analysis:** Pandas, NumPy
- **Visualization:** Power BI, Matplotlib
- **Development Environment:** Kaggle Notebooks

## Project Resources

- **Implementation:** [Open the project notebook on Google Colab](https://colab.research.google.com/drive/1dQEPU3gUa3Bf7npv3mxe2r1Bx8W2z2k6?usp=sharing)
- **Dataset:** [RetailRocket E-Commerce Dataset](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset)
- **Report:** `Customer_Churn_Project_Report.pdf`

## Limitations and Future Improvements

The current implementation is an academic prototype. Streaming ingestion and document storage are simulated rather than deployed using production Kafka brokers and a live MongoDB database.

Future work could include integrating real-time infrastructure, evaluating the model on independently defined targets, testing retention strategies through A/B experiments, and deploying the pipeline on a distributed cloud environment.

## Academic Context

**Course:** DS4511 – Big Data  
**Department:** Data Science Department  
**College:** College of Computing, Umm Al-Qura University

