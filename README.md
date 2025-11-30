Advanced Database Systems – Semester Project (NTUA, 2025–26)
Overview

This repository contains the implementation of the semester project for the course “Advanced Database Systems” (9th Semester, NTUA, 2025–26). The project focuses on large-scale data analysis using Apache Hadoop (≥3.0) and Apache Spark (≥3.5), executed on the AWS cloud environment provided by the course. The work includes distributed data processing, geospatial analytics, performance evaluation across Spark APIs, and scalability experiments.

Technologies & Tools
Distributed Frameworks

Apache Spark ≥ 3.5
Apache Hadoop ≥ 3.0
Apache Sedona 1.6.1 (geospatial analytics)

Cloud Infrastructure

AWS EMR Cluster
AWS S3 (input datasets)
Preconfigured Jupyter environment

Languages
Python / Scala

Datasets
All datasets are hosted in the S3 bucket provided by the course:
s3://initial-notebook-data-bucket-dblab-905418150721/.

Main Dataset
Los Angeles Crime Data (2010–2019, 2020–present)

Supplementary Datasets
Census Blocks (2020, GeoJSON)
Census Block Fields
Median Household Income by ZIP Code (2021)
LA Police Stations
Race and Ethnicity Codes
MO Codes (crime method descriptions)

Project Objectives

According to the assignment, the project aims to:

Develop familiarity with installing, configuring, and managing distributed systems (Hadoop/Spark).

Analyze large datasets using DataFrame, SQL, and RDD APIs.

Understand Spark’s optimizations and resource limitations.

Use Apache Sedona for geospatial processing.

Evaluate performance across different cluster configurations.

Implemented Queries
Query 1 — Age Group Ranking in Aggravated Assault Cases

Goal: Rank victim age groups involved in crimes whose description contains “aggravated assault”.
Age groups:

<18

18–24

25–64

64

APIs: DataFrame API, DataFrame API with UDF & RDD API

Cluster Configuration:

4 executors, 1 core, 2GB RAM per executor

Deliverable: Comparison of execution times across implementations.

Query 2 — Top 3 Victim Descent Groups per Year

Goal: For each year, compute the top 3 racial/ethnic (Vict Descent) victim groups, including their percentage of total victims.

APIs: DataFrame API & SQL API

Cluster Configuration:

4 executors, 1 core, 2GB RAM

Deliverable: Performance comparison between the two APIs.

Query 3 — Most Frequent Crime Methods (MO Codes)

Goal: Determine the frequency of crime methods (MO Codes) and join them with their descriptions.

APIs: DataFrame API & RDD API
Additional Requirements:
Use explain() to analyze Catalyst optimizer strategies.
Experiment with join strategies: BROADCAST, MERGE, SHUFFLE_HASH, SHUFFLE_REPLICATE_NL.

Deliverable: Analysis of join strategies and performance impact.

Query 4 — Nearest Police Station Analysis

Goal: For each police station, compute:

The number of crime incidents closest to that station compared to all others.
The average distance from the incident locations.
Coordinates incorrectly mapped to (0,0) must be removed.

Geospatial Processing:

Must use Apache Sedona.
APIs: DataFrame or SQL API.

Cluster Configurations (2 executors):

1 core, 2GB RAM
2 cores, 4GB RAM
4 cores, 8GB RAM

Deliverable: Performance analysis across configurations.

Query 5 — Correlation of Crime Rate and Income

Goal: Using Census 2020 population data and 2021 household income data:
Compute the correlation between per-capita annual income and per-capita crime rate for 2020–2021.
Repeat the analysis for the top 10 highest-income and bottom 10 lowest-income regions.

Notes:
Regions are defined by the COMM field in Census Blocks.

Cluster Configurations (total 8 cores, 16GB):
2 executors × 4 cores, 8GB
4 executors × 2 cores, 4GB

8 executors × 1 core, 2GB

Deliverable: Execution time comparison and correlation results.
