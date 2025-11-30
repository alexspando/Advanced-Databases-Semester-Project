# Advanced-Databases-Semester-Project
Semester project for the Database Systems course. The project involves building a data processing pipeline using AWS (S3, RDS, EMR) and Apache Spark. It includes data storage, ETL workflows, and analytical queries on large datasets.


Overview

This repository contains the implementation of the semester project for the course “Advanced Database Systems” (9th Semester, NTUA, 2025–26) 

advanced_db_project_2025

.

The project focuses on analysis of large-scale datasets using Apache Hadoop (≥3.0) and Apache Spark (≥3.5), executed on a dedicated AWS cloud environment provided by the course.
It includes distributed data processing, geospatial analytics, performance evaluation across Spark APIs, and scalability experiments.

Technologies & Tools
Distributed Frameworks

Apache Spark ≥ 3.5

Apache Hadoop ≥ 3.0

Apache Sedona 1.6.1 (for geospatial analytics)

Cloud Infrastructure

AWS EMR Cluster

AWS S3 (input datasets)

Preconfigured Jupyter environment

Languages

Python / Scala (depending on the implementation)

Datasets

All datasets are available in the S3 bucket provided by the course:
s3://initial-notebook-data-bucket-dblab-905418150721/ 

advanced_db_project_2025

.

Main Dataset

Los Angeles Crime Data (2010–2019, 2020–present)
Public crime reports for the City of Los Angeles.

Supplementary Datasets

Census Blocks (2020, GeoJSON)

Census Block Fields

Median Household Income by ZIP Code (2021)

LA Police Stations

Race / Ethnicity Codes

MO Codes (crime method descriptions)

(Exact S3 URIs listed in Table 1 of the assignment statement) 

advanced_db_project_2025

.

Project Objectives

As defined in the assignment:

Gain hands-on experience with installing, configuring, and managing distributed systems (Hadoop/Spark)

Analyze large datasets using DataFrame, SQL, and RDD APIs

Understand Spark’s optimizations, resource constraints, and scaling limits

Use Apache Sedona for geospatial processing

Evaluate performance under different cluster configurations

📝 Implemented Queries

Below is a high-level description of the required queries, as specified in the assignment 

advanced_db_project_2025

.

Query 1 — Age Group Ranking in Aggravated Assault Cases

Goal: Rank victim age groups involved in crimes containing the phrase “aggravated assault” in their description.
Age groups:

Children (<18)

Young adults (18–24)

Adults (25–64)

Elderly (>64)

APIs

DataFrame API

DataFrame API with UDF

RDD API

Cluster Configuration

4 executors

1 core, 2GB RAM per executor

Deliverable

Execution time comparison across the three approaches

Query 2 — Top 3 Victim Descent Groups per Year

Goal: For each year, compute the top 3 racial/ethnic groups (Vict Descent) with the most victims, including percentage of total victims.

APIs

DataFrame API

Spark SQL

Cluster Configuration

4 executors

1 core, 2GB RAM per executor

Deliverable

Performance comparison between DataFrame and SQL APIs

Query 3 — Most Frequent Crime Methods (MO Codes)

Goal: Rank crime modus operandi (MO codes) by frequency and join them with their descriptions (from MO Codes dataset).

APIs

DataFrame API

RDD API

Additional Requirements

Use explain() and join hints to analyze Catalyst optimizer strategies

Test different join strategies:

BROADCAST

MERGE

SHUFFLE_HASH

SHUFFLE_REPLICATE_NL

Deliverable

Comparison of join strategies and performance analysis

Query 4 — Nearest Police Station Analysis

Goal: For each police station:

Count the number of crime incidents closest to that station compared to any other

Compute the average distance of these incidents

Exclude coordinates incorrectly located at Null Island (0,0)

Geospatial Processing

Must use Apache Sedona

Use Census Blocks mapping where appropriate

APIs

DataFrame or SQL

Cluster Scaling Configurations

Run the implementation using 2 executors with:

1 core, 2GB RAM

2 cores, 4GB RAM

4 cores, 8GB RAM

Deliverable

Performance scaling analysis

Join strategy evaluation

Query 5 — Correlation of Crime Rate and Income

Goal: Using Census 2020 population data and 2021 household income data:

Compute correlation between per-capita annual income and annual crime rate (per person) for 2020–2021

Repeat analysis for:

the top 10 highest-income regions

the bottom 10 lowest-income regions

Notes

Regions are defined by the COMM field in Census Blocks

Requires population & income joins (possibly spatial)

Cluster Configurations (total 8 cores, 16GB)

2 executors × 4 cores, 8GB

4 executors × 2 cores, 4GB

8 executors × 1 core, 2GB

Deliverable

Execution time comparison and correlation results
