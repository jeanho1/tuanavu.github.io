---
title: "Airflow tutorial 2: Set up airflow environment with docker"
categories:
  - airflow
tags:
  - airflow
  - python
  - tutorials
toc: true
toc_label: "Table of Contents"
---

__We will learn how to set up airflow environment using Docker__

{% include video id="vvr_WNzEXBE" provider="youtube" %}

The [GitHub links](https://github.com/tuanavu/airflow-tutorial/tree/v0.2) for this tutorial

## Airflow problem

- open source software grows at an overwhelming pace

<img src="/images/2018-11-20-set-up-airflow-env-with-docker/Screen Shot 2018-11-21 at 1.52.13 PM.png" width="800"/>  

- Airflow is built to integrate with all databases, system, cloud environments, …
	- Managing and maintaining all of the dependencies changes will be really difficult.
	- Takes lots of time to set up, and config Airflow env.
	- How to share development and production environments for all developers.

## Docker overview

<figure style="width: 300px" class="align-center">     
    <img src="/images/2018-11-20-set-up-airflow-env-with-docker/docker-logo.png" width="300"/>  
</figure>

- Docker is an open platform for developing, shipping, and running applications.
- Docker provides the ability to package and run an application in a loosely isolated environment called a container. The isolation and security allow you to run many containers simultaneously on a given host, regardless of its operating system: Mac, Windows, PC, cloud, data center, ...

- Containers are lightweight because they don’t need the extra load of a hypervisor, but run directly within the host machine’s kernel. This means you can run more containers on a given hardware combination than if you were using virtual machines.

<img src="/images/2018-11-20-set-up-airflow-env-with-docker/Screen Shot 2018-11-21 at 1.59.03 PM.png"/> 

### Benefits of using Docker

- Docker is freeing us from the task of managing, maintaining all of the Airflow dependencies, and deployment.
- Easy to share and deploy different versions and environments.
- Keep track through Github tags and releases.
- Ease of deployment from testing to production environment.

## Airflow docker image

Fork and clone the below Github repo and follow the instruction to set up
- airflow-tutorial: https://github.com/tuanavu/airflow-tutorial

### Prerequisites

- Install [Docker](https://www.docker.com/)
- Install [Docker Compose](https://docs.docker.com/compose/install/)
- Following the Airflow release from [Python Package Index](https://pypi.python.org/pypi/apache-airflow)

### Getting Started

- Clone the repo
- Install the prerequisites
- Run the service
- Check http://localhost:8080
- Done!
