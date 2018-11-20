---
title: "Airflow tutorial 1: Introduction to Apache Airflow"
categories:
  - airflow
tags:
  - airflow
  - python
  - tutorials
toc: true
toc_label: "Table of Contents"
---

__An introduction to Apache Airflow tutorial series__

{% include video id="AHMm1wfGuHE" provider="youtube" %}

The goal of this video is to answer these two questions:
- What is Airflow?
- Use case & Why do we need Airflow?

## What is Airflow?

- __Airflow__ is a platform to programmaticaly author, schedule and monitor workflows or data pipelines.

## What is a Workflow?
- a sequence of tasks
- started on a schedule or triggered by an event
- frequently used to handle big data processing pipelines

### A typical workflows

<img src="/images/2018-11-19-airflow-tutorial-introduction/Screen Shot 2018-11-18 at 3.15.40 PM.png">

1. download data from source
2. send data somewhere else to process
3. Monitor when the process is completed
4. Get the result and generate the report
5. Send the report out by email

## A traditional ETL approach

<img src="/images/2018-11-19-airflow-tutorial-introduction/Screen Shot 2018-11-18 at 3.25.53 PM.png">

Example of a naive approach:
- Writing a script to pull data from database and send it to HDFS to process.
- Schedule the script as a cronjob.

### Problems

- __Failures__: 
    - retry if failure happens (how many times? how often?)
- __Monitoring__: 
    - success or failure status, how long does the process runs?
- __Dependencies__:
    - Data dependencies: upstream data is missing.
    - Execution dependencies: job 2 runs after job 1 is finished.
- __Scalability__:
    - there is no centralized scheduler between different cron machines.
- __Deployment__:
    - deploy new changes constantly
- __Process historic data__:
    - backfill/rerun historical data

## Apache Airflow

- The project joined the Apache Software Foundation’s incubation program in 2016.
- A workflow (data-pipeline) management system developed by Airbnb
    - A framework to define tasks & dependencies in python
    - Executing, scheduling, distributing tasks accross worker nodes.
    - View of present and past runs, logging feature
    - Extensible through plugins
    - Nice UI, possibility to define REST interface
    - Interact well with database
- Used by more than 200 companies: Airbnb, Yahoo, Paypal, Intel, Stripe,

### Airflow DAG

- A workflow as a Directed Acyclic Graph (DAG) with multiple tasks which can be executed independently
- Airflow DAGs are composed of Tasks

<img src="/images/2018-11-19-airflow-tutorial-introduction/airflow-dag.png" height="800" width="800">

### Demo

- http://localhost:8080/admin

### What makes Airflow great?

- Can handle upstream/downstream dependencies gracefully (Example: upstream missing tables)
- Easy to reprocess historical jobs by date, or re-run for specific intervals
- Jobs can pass parameters to other jobs downstream
- Handle errors and failures gracefully.  Automatically retry when a task fails.
- Ease of deployment of workflow changes (continuous integration)
- Integrations with a lot of infrastructure (Hive, Presto, Druid,  AWS, Google cloud, etc)
- Data sensors to trigger a DAG when data arrives
- Job testing through airflow itself
- Accessibility of log files and other meta-data through the web GUI
- Implement trigger rules for tasks
- Monitoring all jobs status in real time + Email alerts
- Community support

### Airflow applications

- __Data warehousing__: cleanse, organize, data quality check, and publish/stream data into our growing data warehouse
- __Machine Learning__: automate machine learning workflows
- __Growth analytics__: compute metrics around guest and host engagement as well as growth accounting
- __Experimentation__: compute A/B testing experimentation frameworks logic and aggregates
- __Email targeting__: apply rules to target and engage users through email campaigns
- __Sessionization__: compute clickstream and time spent datasets
- __Search__: compute search ranking related metrics
- __Data infrastructure maintenance__: database scrapes, folder cleanup, applying data retention policies, …


## The Hierarchy of Data Science

<img src="/images/2018-11-19-airflow-tutorial-introduction/Screen Shot 2018-11-09 at 9.11.11 PM.png" height="500" width="500">

This framework puts things into perspective. Before a company can optimize the business more efficiently or build data products more intelligently, layers of foundational work need to be built first. Data is the fuel for all data products. 

Unfortunately, most data science training program right now only focus on the top of the pyramid of knowledge. There is a discrepancy between the industry and the colleges or any data science training program. I hope this tutorial is helpful for anyone who tries to fill out the gap.
