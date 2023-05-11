# Twitter-Streaming-Pipeline


## Overview

ITI want to develop the job fair process and want to target international companies for student to work abroad to increase the number of people working abroad to solve the dollar issue, they want a fact table to be made over twitter to know all the tweets that are recruiting data engineers all over the world for the next 9 months, the script need to run every 10 minute and get real time data of the last 10 minute tweets talking about data engineer .

This repository contains scripts and tools for setting up a Twitter data pipeline to retrieve tweets, perform transformations using Apache Spark, and store the data in HDFS. Additionally, a data warehouse is created using Hive with dimension and fact tables for further analysis and insights.

## Tools and Technology Used
- Python 3
- Apache Spark (PySpark)
- Hive
- HDFS

## Twitter Listener

The first step in the pipeline is a script that connects to the Twitter API and retrieves recent tweets based on a given search query. In this project, the topic of interest is "Data_Engineering." The script makes a GET request to retrieve the relevant data and converts it to a JSON object. The data is then sent to the socket for further processing.

## Twitter_Stream
The Twitter_Stream script, written in PySpark, reads data from the socket stream. The fields of interest are defined, and a schema is created using StructType. The retrieved data includes tweet information such as ID, text, in_reply_to_user_id, created_at, public_metrics, and source. User information, such as username , is also retrieved. The JSON data is converted to a DataFrame using the defined schema.


## Hive Dimension Tables
The next step involves creating dimension tables in Hive and inserting the data into them. Two dimension tables are created: tweet_raw, which contains all the data about tweets, and user_raw, which contains user-related data.

## Fact Tables
The fact tables are created using a pyspark script. The fact grain is set to a day for meaningful analysis. 

## Pipeline
The pipeline script is a collection of all the individual scripts, allowing for easy execution. It can be run as a bash script or a Python script.

*Notes:*
- The script was originally designed to run every 10 minutes with crontab so i can fetch all the data related to data engineering until stopped

Feel free to explore the repository and use the provided scripts to set up your Twitter data pipeline and perform analysis using Apache Spark and Hive.
