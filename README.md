# gcp_dataproc_spark_airflow
Data Workflows with GCP Dataproc, Apache Airflow and Apache Spark
# Objective
In our case, we need to make a workflow that runs a Spark Application and let us monitor it, all components should be production-ready. First, let review some core concepts and features.
Features and Core Concepts
Features
To create a workflow in Airflow is as simple as write python code no XML or command line if you know some python Yes! You can do some Airflow.
Airflow is not just for Spark It has plenty of integrations like Big Query, S3, Hadoop, Amazon SageMaker and more


# Core concepts
# 1. DAG
Directed Acyclic Graph is a group of all the tasks programmed to run, they are organized in a way that reflects relationships and dependencies [Airflow ideas].

# Airflow DAG represented graphically
# 2. Operator
The description of a single task, it is usually atomic. For example, the PythonOperator is used to execute the python code [Airflow ideas].

# 3. Task
A parameterized instance of an Operator; a node in the DAG [Airflow ideas].

# 4. Task Instance
A task instance represents a specific run of a task and is characterized as the combination of a DAG, a task, and a point in time (execution_date). Task instances also have an indicative state, which could be “running”, “success”, “failed”, “skipped”, “up for retry”, etc. [Airflow ideas]

# Building Environment
We have different options to deploy Spark and Airflow, exist many interesting articles on the web. Here are some of them:
Deploy Spark on Kubernetes
Deploy Spark on a Virtual Machine
Deploy Airflow on dockers

Now following our objective, we need a simple way to install and configure Spark and Airflow to help us we’ll use Cloud Composer and Dataproc both are products of Google Cloud.

# Cloud composer: 
is a fully managed workflow orchestration service built on Apache Airflow [Cloud composer docs]. The main advantage is that we don’t have to worry about deployment and configuration, all are backed by Google also makes simple to scale Airflow. Cloud Composer integrates with GCP, AWS, and Azure components also technologies like Hive, Druid, Cassandra, Pig, Spark, Hadoop, etc.

# Dataproc: 
is a fully managed cloud service for running Apache Spark, Apache Hive and Apache Hadoop [Dataproc page]. Some features are easy deployment and scaling, integration with Cloud Composer (Airflow) and a feature we’ll be using here is create automatically a Dataproc cluster just for processing and then destroy so you will pay for minutes and avoid unused infrastructure.

## Code
This part will be from a simple Airflow workflow to the complex workflow needed for our objective.
Simple DAG
Everyone starts learning to program with a Hello World! so let's do the same but in Airflow.
Writing an Airflow workflow almost follow these 6 steps
Imports libraries Airflow, DateTime and others
Define a start date of the workflow
Set the default arguments for our DAG
Define the DAG
Set Operators
Define DAGs dependencies

Now save the code in a file gcp_spark_airflow.py and upload it to the DAGs folder in the bucket created. That folder is exclusive for all your DAGs.

After the file is uploaded return to the Airflow UI tab and refresh (remember the indentation in your code and It could take up to 5 minutes to update the page).