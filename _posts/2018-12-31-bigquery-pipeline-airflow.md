---
title: "Airflow tutorial 6: Build a data pipeline using Google Cloud Bigquery"
categories:
  - airflow
tags:
  - airflow
  - python
  - tutorials
toc: true
toc_label: "Table of Contents"
---

__In this tutorial, we will build a data pipeline using Google Cloud Bigquery and Airflow__

{% include video id="wAyu5BN3VpY" provider="youtube" %}

The [GitHub links](https://github.com/tuanavu/airflow-tutorial/tree/v0.6) for this tutorial

## A quick look at this tutorial

This tutorial is inspired by this [blog post](https://cloud.google.com/blog/products/gcp/how-to-aggregate-data-for-bigquery-using-apache-airflow) from the official Google Cloud blogs.

We will be using 2 public datasets hosted on Google BigQuery:
- [Github Archive](https://bigquery.cloud.google.com/table/githubarchive:day.20181230): 30 million events monthly, including issues, commits, and pushes on Github.
- [Hacker news](https://bigquery.cloud.google.com/table/bigquery-public-data:hacker_news.full): contains a full daily update of all the stories and comments from Hacker News.

From the public datasets, we will create a data pipeline for aggregating daily stats about Github repos and the associated Hacker News story and pushing the result into a new joint table every day. The final table will be used to power this visualization report: [GitHub on Hacker News trends dashboard](https://datastudio.google.com/open/0B2H0iLe8kbvIUnFxMElvQktUNE0) created using [Google Data Studio](https://cloud.google.com/data-studio/).


## Overview of Google BigQuery

Google BigQuery is a big data analytics product from Google that helps you run ad-hoc analysis on massive dataset using Google Cloud infrastructure. With the power BigQuery, you can run a query to analyze terabytes of data within seconds.

Some characteristics of Google BigQuery:
- __Serverless__: is an execution model where the cloud provider (AWS, Google) will dynamically allocate the resources to run your code, and only charge for that amount of resources. 
- __Highly Scalable__: can scale to tens of thousands of machines in Google Data Center.
- __High performance__: massively parallel execution and automatic performance optimization.
- __High Availability__: Automatically replicates data between zones to enable high availability. It also automatically load balances to provide optimal performance and to minimize the impact of any hardware failures.

The advantage of choosing Google BigQuery for this tutorial:
- Access to [Google BigQuery public datasets](https://cloud.google.com/bigquery/public-data): Google pays for the storage of these datasets and provides public access to the data via your cloud project. You pay only for the queries that you perform on the data. Moreover, there’s a [1TB per month free tier](https://cloud.google.com/bigquery/pricing#pricing_summary) for queries, making getting started super easy.
- Real-time analysis of massive datasets
- No-ops (no operations): no need to do operations work like setting up or maintaining any infrastructure. Just focus on your code.

### Working with Google BigQuery

- The first step you need to do is sign in to your Google account
- Search for Google Cloud, sign up
- Go to [Google cloud console](https://console.cloud.google.com)
- Search for [Bigquery](https://console.cloud.google.com/bigquery) in the navigation bar. 

In this tutorial, we will be using 2 public datasets hosted on Google BigQuery:
- Github Archive: 30 million events monthly, including issues, commits and pushes on Github.
    - Link: [Data](https://bigquery.cloud.google.com/table/githubarchive:day.20181230) - [More info](https://blog.github.com/2017-01-19-github-data-ready-for-you-to-explore-with-bigquery/)
- Hacker news: contains a full daily update of all the stories and comments from Hacker News.
    - Link: [Data](https://bigquery.cloud.google.com/table/bigquery-public-data:hacker_news.full) - [More info](https://medium.com/@hoffa/hacker-news-on-bigquery-now-with-daily-updates-so-what-are-the-top-domains-963d3c68b2e2)


### Exploratory data analysis

The first step in working with any new datasets is to do some analysis to explore the data.

You can either use:
- the [BigQuery Web UI](https://bigquery.cloud.google.com) to run your adhoc queries.
- go through my [jupyter notebook](https://github.com/tuanavu/airflow-tutorial/blob/master/notebooks/gcloud-example/github-trend-analysis.ipynb) to reproduce my analysis.

Steps to run my jupyter notebook docker environment and reproduce the analysis:
- Clone this [airflow-tutorial repo](https://github.com/tuanavu/airflow-tutorial)
- Go to the `notebooks` directory, you should see a `docker-compose.yml` file

```
cd notebooks
```

- Run this command in the terminal to start the docker environment

```
docker-compose up
```

- You should see a similar output in your terminal with the first time login token:

```
Copy/paste this URL into your browser when you connect for the first time, to login with a token:
http://(7b568d3eba0f or 127.0.0.1):8888/?token=7d229945745ecd113adc572d50d93c98e3552516ee65a432
```

- Copy the token and open a new web browser, enter:

```
localhost:8889/?token=7d229945745ecd113adc572d50d93c98e3552516ee65a432
```
- That's it. You should now see the `work/github-trend-analysis.ipynb` file


## Building the data pipeline

### Setting up

In order to run this data pipeline example, you need to set up a few things first. Specifically:
- Create a service account (Cloud Console)
- Setup a Google Cloud Connection in Airflow
- Supply the config variables

Follow this [instruction](https://github.com/tuanavu/airflow-tutorial/tree/master/docs/bigquery_github_trends.md) to set up and run your DAG.

### Running the Airflow docker environment

I have already created a new [docker environment](https://github.com/tuanavu/airflow-tutorial/blob/master/docker-compose-gcloud.yml) to run this data pipeline example. Steps to run the airflow environment:
- Check out the [Github master branch](https://github.com/tuanavu/airflow-tutorial) of this tutorial
- Start the Airflow environment with docker

```bash
bash run_gcloud_example.sh
```

- Stop the Airflow environment when you are finished

```bash
bash stop_gcloud_example.sh
```



### Test your DAG

After connection and config variables have been set up using this [instruction](https://github.com/tuanavu/airflow-tutorial/tree/master/docs/bigquery_github_trends.md), you can now test and run your DAG.

- Using the command below to test specific task in the DAG:

```bash
docker-compose -f docker-compose-gcloud.yml run --rm webserver airflow test [DAG_ID] [TASK_ID] [EXECUTION_DATE]
```

- Examples:

```bash
# Task 1
docker-compose -f docker-compose-gcloud.yml run --rm webserver airflow test bigquery_github_trends bq_check_githubarchive_day 2018-12-01

# Task 2
docker-compose -f docker-compose-gcloud.yml run --rm webserver airflow test bigquery_github_trends bq_check_hackernews_full 2018-12-01
```

## Resources

- [github-trend-analysis - jupyter notebook](https://github.com/tuanavu/airflow-tutorial/blob/master/notebooks/gcloud-example/github-trend-analysis.ipynb)
- [Instruction to run this pipeline](https://github.com/tuanavu/airflow-tutorial/blob/master/docs/bigquery_github_trends.md)
- [How to run a terabyte of queries each month without a credit card](https://www.youtube.com/watch?v=w4mzE--sprY)
- [How to aggregate data for BigQuery using Apache Airflow](https://cloud.google.com/blog/products/gcp/how-to-aggregate-data-for-bigquery-using-apache-airflow)
- [GitHub data, ready for you to explore with BigQuery](https://blog.github.com/2017-01-19-github-data-ready-for-you-to-explore-with-bigquery/)
- [Hacker News on BigQuery](https://medium.com/@hoffa/hacker-news-on-bigquery-now-with-daily-updates-so-what-are-the-top-domains-963d3c68b2e2)
- [BigQuery pricing](https://cloud.google.com/bigquery/pricing#pricing_summary)
