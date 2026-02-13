## In this activity, you will create a second data pipeline that:
1. Create a file using the BashOperator
2. Read the file using the PythonOperator

## At the end of this activity, you will be able to:
- Find the documentation you need to implement an operator
- Execute Bash commands from your DAG
- Create a DAG following best practices
- Execute Python functions from your DAG
- Define dependencies between your tasks

## Prerequisites:
Local development environment with the Astro CLI

## Instructions:
### Step 1: Defining the DAG
Create a dag file check_dag.py. Then, define a DAG with the identifier check_dag.

We expect check_dag to run every day at midnight from the 1st of January 2025. 

Also, the DAG should have the following description "DAG to check data" and belongs to the data_engineering team.

### Step 2: Creating the Tasks
We want to add three tasks to this DAG.

The first task executes the following Bash command: echo "Hi there!" >/tmp/dummy, to create a file dummy in the tmp directory with "Hi there!". The task's name should be create_file

Use the @task.bash decorator for Bash commands.

The second task executes the following  Bash command: test -f /tmp/dummy, to verify that the file dummy exists in the tmp directory. The task's name should be check_file

The third task executes the following Python function: 
print(open('/tmp/dummy', 'rb').read()) 
to read and print on the standard output the content of the dummy file.

### Step 3: Defining the dependencies
You should define the dependencies to get the order of execution:
create_file -> check_file_exists -> read_file

Finally, make sure that you have no errors by going to the Airflow UI.
