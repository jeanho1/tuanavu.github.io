---
title: "Airflow tutorial 4: Writing your first pipeline"
categories:
  - airflow
tags:
  - airflow
  - python
  - tutorials
toc: true
toc_label: "Table of Contents"
---

__We will learn how to write our first DAG step by step__

{% include video id="43wHwwZhJMo" provider="youtube" %}

## Steps to write an Airflow DAG

- A DAG file, which is basically just a Python script, is a configuration file specifying the DAG's structure as code.
- There are only 5 steps you need to remember to write an Airflow DAG or workflow:
    - Step 1: Importing modules
    - Step 2: Default Arguments
    - Step 3: Instantiate a DAG
    - Step 4: Tasks
    - Step 5: Setting up Dependencies

## Step 1: Importing modules

- Import Python dependencies needed for the workflow

```python
from datetime import timedelta

import airflow
from airflow import DAG
from airflow.operators.bash_operator import BashOperator
```

## Step 2: Default Arguments
- Define default and DAG-specific arguments

```python
default_args = {
    'owner': 'airflow',    
    'start_date': airflow.utils.dates.days_ago(2),
    # 'end_date': datetime(2018, 12, 30),
    'depends_on_past': False,
    'email': ['airflow@example.com'],
    'email_on_failure': False,
    'email_on_retry': False,
    # If a task fails, retry it once after waiting
    # at least 5 minutes
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
    }
```

## Step 3: Instantiate a DAG
- Give the DAG name, configure the schedule, and set the DAG settings

```python
dag = DAG(
    'tutorial',
    default_args=default_args,
    description='A simple tutorial DAG',
    # Continue to run DAG once per day
    schedule_interval=timedelta(days=1),
)
```

Here is a couple of options you can use for your `schedule_interval`. You can choose to use some preset argument or cron-like argument:

| preset  | meaning | cron  |
|:--------|:-----------------------------------------------------------------|:------------|
| `None`  | Don't schedule, use for exclusively "externally <br>triggered" DAGs  |   |
| `@once`  | Schedule once and only once   |   |
| `@hourly`  | Run once an hour at the beginning of the hour  | `0 * * * *`  |
| ``@daily``  | Run once a day at midnight  | ``0 0 * * *``  |
| ``@weekly``  | Run once a week at midnight on Sunday morning  | ``0 0 * * 0``  |
| ``@monthly``  | Run once a month at midnight of the first day <br>of the month  | ``0 0 1 * *``  |
| ``@yearly``  | Run once a year at midnight of January 1  | ``0 0 1 1 *``  |

__Example usage__:
- Daily schedule: 
    - `schedule_interval='@daily'`
    - `schedule_interval='0 0 * * *'`

## Step 4: Tasks

- The next step is to lay out all the tasks in the workflow.

{% raw %}
```python
# t1, t2 and t3 are examples of tasks created by instantiating operators
t1 = BashOperator(
    task_id='print_date',
    bash_command='date',
    dag=dag,
)

t2 = BashOperator(
    task_id='sleep',
    depends_on_past=False,
    bash_command='sleep 5',
    dag=dag,
)

templated_command = """
{% for i in range(5) %}
    echo "{{ ds }}"
    echo "{{ macros.ds_add(ds, 7)}}"
    echo "{{ params.my_param }}"
{% endfor %}
"""

t3 = BashOperator(
    task_id='templated',
    depends_on_past=False,
    bash_command=templated_command,
    params={'my_param': 'Parameter I passed in'},
    dag=dag,
)
```
{% endraw %}

## Step 5: Setting up Dependencies

- Set the dependencies or the order in which the tasks should be executed in.
- Here’s a few ways you can define dependencies between them:

```python
# This means that t2 will depend on t1
# running successfully to run.
t1.set_downstream(t2)

# similar to above where t3 will depend on t1
t3.set_upstream(t1)
```

```python
# The bit shift operator can also be
# used to chain operations:
t1 >> t2

# And the upstream dependency with the
# bit shift operator:
t2 << t1
```

```python
# A list of tasks can also be set as
# dependencies. These operations
# all have the same effect:
t1.set_downstream([t2, t3])
t1 >> [t2, t3]
[t2, t3] << t1
```

## Recap

- Basically a DAG is just a Python file, which is used to organize tasks and set their execution context. DAGs do not perform any actual computation. 
- Instead, tasks are the element of Airflow that actually “do the work” we want performed. And it is your job to write the configuration and organize the tasks in specific orders to create a complete data pipeline.

- Your final DAG will look like this:

{% raw %}
```python
"""
Code that goes along with the Airflow tutorial located at:
https://github.com/apache/incubator-airflow/blob/master/airflow/example_dags/tutorial.py
"""
from airflow import DAG
from airflow.operators.bash_operator import BashOperator
from datetime import datetime, timedelta


default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': datetime(2015, 6, 1),
    'email': ['airflow@example.com'],
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
    # 'queue': 'bash_queue',
    # 'pool': 'backfill',
    # 'priority_weight': 10,
    # 'end_date': datetime(2016, 1, 1),
}

dag = DAG(
    'tutorial', 
    default_args=default_args, 
    schedule_interval=timedelta(days=1))

# t1, t2 and t3 are examples of tasks 
# created by instantiating operators
t1 = BashOperator(
    task_id='print_date',
    bash_command='date',
    dag=dag)

t2 = BashOperator(
    task_id='sleep',
    bash_command='sleep 5',
    retries=3,
    dag=dag)

templated_command = """
    {% for i in range(5) %}
        echo "{{ ds }}"
        echo "{{ macros.ds_add(ds, 7)}}"
        echo "{{ params.my_param }}"
    {% endfor %}
"""

t3 = BashOperator(
    task_id='templated',
    bash_command=templated_command,
    params={'my_param': 'Parameter I passed in'},
    dag=dag)

t2.set_upstream(t1)
t3.set_upstream(t1)
```
{% endraw %}
