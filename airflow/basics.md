#### What is DAG?.

The dag is directed acyclic graph, In airflow node of dag represents task and edge represents the dependency. there is no cycle in graph.


#### Basic DAG skeleton.

```py
from airflow import DAG
form datetime import datetime

with DAG(dag_id='user_processing', # unique id across all the dags
	   start_date = datetime(2022, 1, 1), # the datetime when dag will start execution
	   schedule_interval='@daily', # frequecy at which dag runs
	   dagrun_timeout = datetime.timedelta(minute=60), # dag's runnig timeout time
	   tags=["data_dag1", "data_dag2"], # tags associated with dag
	   params={"example_key":"example_value"}
	   catchup=False)
	as dag:

```
	