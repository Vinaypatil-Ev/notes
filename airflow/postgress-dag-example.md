#### Postgress simple dag

```py

from airflow import DAG
from datetime import datetime
from airflow.providers.postgres.operators.postgres import PostgresOperator

with DAG(
    dag_id = "postgress_proc_dag",
    startdate = datetime(2023, 5, 10),
    scheduel_interval="@daily"
    catchup=False,
    ) as dag:

    create_table = PostgresOperator(
        task_id = "postgress_conn",
        postgres_conn_id = "postgress",
        sql = """
            SELECT * FROM postgress_table 
        """
    )

```