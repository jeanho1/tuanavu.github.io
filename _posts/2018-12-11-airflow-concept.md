---
title: "Airflow tutorial 5: Airflow concept"
categories:
  - airflow
tags:
  - airflow
  - python
  - tutorials
toc: true
toc_label: "Table of Contents"
---

__We will learn about Airflow’s key concepts__

{% include video id="4rQSa2zEWfw" provider="youtube" %}

## Overview

Airflow is a workflow management system which is used to programmatically author, schedule and monitor workflows.

## DAGs

__Workflows__ are called __DAGs__ (Directed Acyclic Graph).

- A DAG is a collection of all the tasks you want to run, organized in a way that reflects their relationships and dependencies.


<img src="/images/2018-11-19-airflow-tutorial-introduction/airflow-dag.png" height="600" width="600" >

### Understand Directed Acyclic Graph

To understand what is a Directed Acyclic Graph? First, we need to understand the graph data structure. This is a very special data structure in computer science.

A Graph has 2 main parts:
- The vertices (nodes) where the data is stored
- The edges (connections) which connect the nodes    


<img src="/images/2018-12-11-airflow-concept/Screen Shot 2018-12-14 at 11.53.04 AM.png" >

Graphs are used to solve many real-life problems because they are used to represent networks. 
- For example: social networks, system of roads, airline flights from city to city, how the Internet is connected, etc. 

<figure style="width: 400px" class="align-center">     
    <img src="/images/2018-12-11-airflow-concept/1_3BvGbuFSHeLUihVXAAaNdw.png" height="500" width="400" >
</figure> 


- __Undirected graph__: The relationship exists in both directions, the edge has no direction. Example: If Mary was a friend of Francis, Francis would likewise be a friend of Mary. 

- __Directed graph__ (digraph): Direction matters, since the edges in a graph are all one-way
    - An example graph: the course requirements for a computer science major.
    - The class prerequisites graph is clearly a __digraph__ since you must take some classes before others.

<figure style="width: 500px" class="align-center">     
    <img src="/images/2018-12-11-airflow-concept/Screen Shot 2018-12-14 at 11.50.53 AM.png" >
</figure> 


- __Acyclic graph__: a graph has no cycles.
- __Cyclic graph__: a graph has cycles.    
    - A cycle in a directed graph is a path that starts and ends at the same node.
    - For example, the path (V5,V2,V3,V5) is a cycle. This is a loop.

<figure style="width: 400px" class="align-center">     
    <img src="/images/2018-12-11-airflow-concept/Screen Shot 2018-12-13 at 10.46.03 PM.png" height="400" width="400" >
</figure>


### DAGs Summary

__Directed Acyclic Graph__ is a graph that has __no cycles__ and the data in each node flows forward in only __one direction__.

It is useful to represent a complex data flows using a graph. 
- Each node in the graph is a task
- The edges represent dependencies amongst tasks.
- These graphs are called computation graphs or data flow graphs and it transform the data as it flow through the graph and enable very complex numeric computations.
- Given that data only needs to be computed once on a given task and the computation then carries forward, the graph is directed and acyclic. This is why Airflow jobs are commonly referred to as __"DAGs"__ (Directed Acyclic Graphs)

<figure style="width: 500px" class="align-center">     
    <img src="/images/2018-11-19-airflow-tutorial-introduction/airflow-dag.png" height="500" width="500">
</figure> 


Beside Airflow, there are other cutting edge big data/data science frameworks is built using graph data structure.
- __Tensorflow__ - An open source machine learning framework
    - TensorFlow uses a dataflow graph to represent your computation in terms of the dependencies between individual operations.

<figure style="width: 300px" class="align-center">     
    <img src="https://www.tensorflow.org/images/tensors_flowing.gif">
</figure>


## Operators, and Tasks

- __DAGs__ do not perform any actual computation. Instead, __Operators__ determine what actually gets done.
- __Task__: Once an operator is instantiated, it is referred to as a "task". An operator describes a single task in a workflow.
    - Instantiating a task requires providing a unique `task_id` and `DAG` container
- A __DAG__ is a container that is used to organize tasks and set their execution context.

```python
# t1, t2 are examples of tasks created by instantiating operators
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
```

### Operators categories

Typically, __Operators__ are classified into three categories:
- __Sensors__: a certain type of operator that will keep running until a certain criteria is met. Example include waiting for a certain time, external file, or upstream data source.
    - [`HdfsSensor`](https://github.com/apache/incubator-airflow/blob/master/airflow/sensors/hdfs_sensor.py): Waits for a file or folder to land in HDFS
    - [`NamedHivePartitionSensor`](https://github.com/apache/incubator-airflow/blob/master/airflow/sensors/named_hive_partition_sensor.py): check whether the most recent partition of a Hive table is available for downstream processing.    

- __Operators__: triggers a certain action (e.g. run a bash command, execute a python function, or execute a Hive query, etc)
    - [`BashOperator`](https://github.com/apache/incubator-airflow/blob/master/airflow/operators/bash_operator.py): executes a bash command
    - [`PythonOperator`](https://github.com/apache/incubator-airflow/blob/master/airflow/operators/python_operator.py): calls an arbitrary Python function
    - [`HiveOperator`](https://github.com/apache/incubator-airflow/blob/master/airflow/operators/hive_operator.py): executes hql code or hive script in a specific Hive database.
    - [`BigQueryOperator`](https://github.com/apache/incubator-airflow/blob/master/airflow/contrib/operators/bigquery_operator.py): executes Google BigQuery SQL queries in a specific BigQuery database
    

- __Transfers__: moves data from one location to another.
    - [`MySqlToHiveTransfer`](https://github.com/apache/incubator-airflow/blob/master/airflow/operators/mysql_to_hive.py): Moves data from MySql to Hive.
    - [`S3ToRedshiftTransfer`](https://github.com/apache/incubator-airflow/blob/master/airflow/operators/s3_to_redshift_operator.py): load files from s3 to Redshift

### Working with Operators

- Airflow provides prebuilt operators for many common tasks.
- There are more operators being added by the community. You can just go to the [Airflow official Github repo](https://github.com/apache/incubator-airflow), specifically in the `airflow/contrib/` directory to look for the community added operators.
- All operators are derived from `BaseOperator` and acquire much functionality through inheritance. Contributors can extend `BaseOperator` class to create custom operators as they see fit.


```python
class HiveOperator(BaseOperator):
    """
    HiveOperator inherits from BaseOperator
    """
```

## Defining Task Dependencies

- After defining a DAG, and instantiate all the tasks, you can then set the dependencies or the order in which the tasks should be executed.
- Task dependencies are set using:
    - the `set_upstream` and `set_downstream` operators.
    - the bitshift operators `<<` and `>>`

```python
# This means that t2 will depend on t1
# running successfully to run.
t1.set_downstream(t2)

# bit shift operator
# t1 >> t2
```


## DagRuns and TaskInstances

- A key concept in Airflow is the `execution_time`. The execution times begin at the DAG’s `start_date` and repeat every `schedule_interval`.
- For this example the scheduled execution times would be ("2018–12–01 00:00:00", "2018–12–02 00:00:00", ...). For each execution_time, a `DagRun` is created and operates under the context of that execution time. A `DagRun` is simply a DAG that has a specific execution time.

```python
default_args = {
    'owner': 'airflow',    
    'start_date': datetime(2018, 12, 01),
    # 'end_date': datetime(2018, 12, 30),   
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
    }

dag = DAG(
    'tutorial',
    default_args=default_args,
    description='A simple tutorial DAG',
    # Continue to run DAG once per day
    schedule_interval=timedelta(days=1),
)
```

- __DagRuns__ are DAGs that runs at a certain time.
- __TaskInstances__ are the task belongs to that __DagRuns__. 
    - Each __DagRun__ and __TaskInstance__ is associated with an entry in Airflow’s metadata database that logs their state (e.g. "queued", "running", "failed", "skipped", "up for retry"). 

<img src="/images/2018-12-11-airflow-concept/Screen Shot 2018-12-15 at 8.18.10 PM.png" width="700" >

Screenshot taken from [Quizlet’s Medium post](https://medium.com/@dustinstansbury/understanding-apache-airflows-key-concepts-a96efed52b1a)

## Resources
- [Understanding Apache Airflow’s key concepts](https://medium.com/@dustinstansbury/understanding-apache-airflows-key-concepts-a96efed52b1a)
- [A Beginner’s Guide to Data Engineering — Part II](https://medium.com/@rchang/a-beginners-guide-to-data-engineering-part-ii-47c4e7cbda71)
- [Graphs and Graph Algorithms](http://interactivepython.org/runestone/static/pythonds/Graphs/toctree.html)
