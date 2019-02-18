---
title: "Airflow tutorial 3: Set up airflow environment using Google Cloud Composer"
categories:
  - airflow
tags:
  - airflow
  - python
  - tutorials
toc: true
toc_label: "Table of Contents"
---

__We will learn how to set up airflow environment using Google Cloud Composer__

{% include video id="ld6JO3MiuPQ" provider="youtube" %}

## Overview of Cloud Composer

<figure style="width: 200px" class="align-center">     
    <img src="/images/2018-11-23-set-up-airflow-with-google-composer/cloud-composer.png" />
</figure>  

- A fully managed Apache Airflow to make workflow creation and management easy, powerful, and consistent.
- Cloud Composer helps you create Airflow environments quickly and easily, so you can focus on your workflows and not your infrastructure.

### Hosting Airflow on-premise

Let's say you want to host Airflow on-premise. In another word, you host Airflow on your local server. There are a lot of problems with this approach:
- You will need to spend a lot of time doing DevOps work: create a new server, manage Airflow installation, takes care of dependency management, package management, make sure your server always up and running, then you have to deal with scaling and security issues...
- If you don't want to deal with all of those DevOps problem, and instead just want to focus on your workflow, then Google Cloud composer is a great solution for you.

### Google Cloud Composer benefit

- The nice thing about Google Cloud Composer is that you as a Data Engineer or Data Scientist don’t have to spend that much time on DevOps.
- You just focus on your workflows (writing code), and let Composer manage the infrastructure.
- Of course you have to pay for the hosting service, but the cost is low compare to if you have to host a production airflow server on your own. This is an ideal solution if you are a startup in need of Airflow and you don’t have a lot of DevOps folks in-house.


<img src="/images/2018-11-23-set-up-airflow-with-google-composer/Screen Shot 2018-11-23 at 9.44.02 PM.png" />  

## Key Cloud Composer features

- Simplicity:
    - One-click to create a new Airflow environment
    - Client tooling including Google Cloud SDK, Google Developer Console
    - Easy and controlled access to the Airflow Web UI
- Security:
    - Identity access management (IAM): manage credentials, permissions, and access policies.
- Scalability:
    - Easy to scale with Google infrastructure.
- Production monitoring:
    - Stackdriver logging and monitoring: 
        - Provide logging and monitoring metrics, and alert when your workflow is not running.
    - Simplified DAG (workflow) management
    - Python package management
- Comprehensive GCP integration:
    - Integrate with all of Google Cloud services: Big Data, Machine Learning...
    - Run jobs elsewhere: Other cloud provider, or on-premises.

### Releases

Google Cloud composer is a new product from Google. With the latest push from Google, you can be sure that Apache Airflow is the current cutting edge technology in the software industry.

- First beta release: May 1, 2018 (6 months ago)

<img src="/images/2018-11-23-set-up-airflow-with-google-composer/Screen Shot 2018-11-26 at 4.13.21 PM.png" />  

- Latest release: October 24, 2018
    - Support Python 3 and Airflow 1.10.0
    
<img src="/images/2018-11-23-set-up-airflow-with-google-composer/Screen Shot 2018-11-26 at 4.16.08 PM.png" /> 

## Set up Google Cloud Composer environment

- It’s extremely easy to set up. If you have a Google Cloud account, it’s really just a few clicks away.

### Composer environment

- You can create multiple environments within a project.
- Each environment is a different kubernetes cluster with multiple nodes, so they are perfectly isolated from each other.

<img src="/images/2018-11-23-set-up-airflow-with-google-composer/Screen Shot 2018-11-26 at 3.44.58 PM.png" />  

#### Create an environment

- Choose how many nodes and disk size

<figure style="width: 400px" class="align-center">     
    <img src="/images/2018-11-23-set-up-airflow-with-google-composer/Screen Shot 2018-11-26 at 3.45.49 PM.png" width="400" />
</figure>  

- Choose Airflow and Python version

<figure style="width: 400px" class="align-center">     
    <img src="/images/2018-11-23-set-up-airflow-with-google-composer/Screen Shot 2018-11-26 at 3.46.11 PM.png" width="400" />
</figure>

#### A complete Composer environment

<img src="/images/2018-11-23-set-up-airflow-with-google-composer/Screen Shot 2018-11-26 at 4.07.34 PM.png" width="700" />

#### Installing Python dependencies
- Installing a Python dependency from Python Package Index (PyPI)

<img src="/images/2018-11-23-set-up-airflow-with-google-composer/Screen Shot 2018-11-26 at 4.07.56 PM.png" width="700" />

### Deployment

Deployment is simple. Google Cloud Composer uses Cloud Storage to store Apache Airflow DAGs, so you can easily add, update, and delete a DAG from your environment.

Manual deployment:
- You can drag-and-drop your Python `.py` file for the DAG to the Composer environment's `dags` folder in Cloud Storage to deploy new DAGs. Within seconds the DAG appears in the Airflow UI.
- Using gcloud sdk command to deploy a new dag.
Auto deployment:
- Your DAGs files are stored in a Git repository. You can set up a continuous integration pipeline to automatically deploy every time a merge request is done in the master branch.

## More information

- [Cloud Composer official documentation](https://cloud.google.com/composer/docs/quickstart)
- [Watch full talk from Google](https://www.youtube.com/watch?v=GeNFEtt-D4k): Live demo of getting a worfklow up and running in Google Cloud Composer.
