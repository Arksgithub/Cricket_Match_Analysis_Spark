# IPL_Match_Analysis_Spark
1. Environment Setup:
- Set up Apache Spark on the local or cloud environment.
- Install required libraries (PySpark, Matplotlib, Seaborn, Pandas, etc.).
# Import necessary libraries
from pyspark.sql import SparkSession
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
2. Creating a Spark Session:
- Start by creating a Spark session to handle distributed data
spark = SparkSession.builder \
    .appName("IPL Data Analysis") \
    .getOrCreate()
3. Loading the Dataset:
Load the IPL dataset into a Spark DataFrame. It can be done by setting the path from the S3 bucket or by uploading the file into the DBFS and giving the Spark API path
# Load IPL dataset
df = spark.read.csv('path_to_IPL_dataset.csv', header=True, inferSchema=True)
df.show(5)
4. Data Cleaning and Transformation:
- Handle missing values and filter necessary columns.
- Perform type casting and data transformation.
# Data cleaning
df_cleaned = df.na.drop()  # Drop rows with missing values
df_cleaned = df_cleaned.withColumnRenamed("old_column", "new_column")  # Rename columns if necessary
5. Exploratory Data Analysis (EDA):
- Conduct descriptive statistics and visualization of basic metrics (matches, teams, venues, etc.).
# Show basic stats
df_cleaned.describe().show()
6. Analysis of Team Performance After Winning the Toss:
- Filter the dataset for teams that won the toss and analyze their performance.
