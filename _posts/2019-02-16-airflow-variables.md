---
title: "Airflow tutorial 7: Airflow variables"
categories:
  - airflow
tags:
  - airflow
  - python
  - tutorials
toc: true
toc_label: "Table of Contents"
---

__In this tutorial, we explore how to use Airflow variables__

{% include video id="bHQ7nzn0j6k" provider="youtube" %}

The [GitHub links](https://github.com/tuanavu/airflow-tutorial/tree/v0.7) for this tutorial

## What are Airflow variables?

- Variables are key-value stores in Airflow's metadata database.
- It is used to store and retrieve arbitrary content or settings from the metadata database.

## When to use Variables

- Variables are mostly used to store static values like:
    - config variables
    - a configuration file
    - list of tables
    - list of IDs to dynamically generate tasks from
- Separate the constants and variables from pipeline code:
    - It is useful to have some variables or configuration items accessible and modifiable through the UI.

## Working with Variables
- Variables can be listed, created, updated and deleted from the UI (`Admin -> Variables`).
- In addition, json settings files can be bulk uploaded through the UI. Please look at an example here for a [variable json setting file](https://github.com/tuanavu/airflow-tutorial/blob/master/examples/intro-example/dags/config/example_variables.json)

### Restrict the number of Airflow variables in your DAG

- Since Airflow Variables are stored in Metadata Database, so any call to variables would mean a connection to Metadata DB. 
    - Instead of storing a large number of variable in your DAG, which may end up saturating the number of allowed connections to your database.
    - It is recommended you store all your DAG configuration inside a single Airflow variable with JSON value.

<img src="/images/2019-02-16-airflow-variables/Screen Shot 2019-02-16 at 4.36.56 PM.png" width="700">

- You can then access the variables as follow:
    
{% raw %}
```python
# Config variables
## Common
var1 = "value1"
var2 = [1, 2, 3]
var3 = {'k': 'value3'}

## 3 DB connections called
var1 = Variable.get("var1")
var2 = Variable.get("var2")
var3 = Variable.get("var3")

## Recommended way
dag_config = Variable.get("example_variables_config", deserialize_json=True)
var1 = dag_config["var1"]
var2 = dag_config["var2"]
var3 = dag_config["var3"]

# You can directly use a variable from a jinja template
## {{ var.value.<variable_name> }}

t2 = BashOperator(
    task_id="get_variable_value",
    bash_command='echo {{ var.value.var3 }} ',
    dag=dag,
)

## {{ var.json.<variable_name> }}
t3 = BashOperator(
    task_id="get_variable_json",
    bash_command='echo {{ var.json.example_variables_config.var3 }} ',
    dag=dag,
)
```
{% endraw %}

### Access variables through Airflow command line

- You can run some CRUD operations on variables through the [Airflow CLI](https://airflow.apache.org/cli.html#variables)
- Some command you can run in this example:

{% raw %}
```bash
# get value of var1
docker-compose run --rm webserver airflow variables --get var1

# set value of var4
docker-compose run --rm webserver airflow variables --set var4 value4]

# import variable json file
docker-compose run --rm webserver airflow variables --import /usr/local/airflow/dags/config/example_variables.json
```
{% endraw %}