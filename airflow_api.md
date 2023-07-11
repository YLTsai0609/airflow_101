# API Documemnts

# [Fundamental Concepts](https://airflow.apache.org/docs/apache-airflow/stable/tutorial/fundamentals.html)
## [DAG](https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/dags.html#subdags)
* **DAG**
    * compose from task, workflow as code.
* **Operator**
    * defines a unit of work for airflow to complete.
    * BashOperator, PythonOperator, KubernetesPodOperator
* **Task**
    * to use an operator, need to instantiate it as task with parameters.
    * 

* **Templating with Jinja**
    * a set of built-in parameters and macros.
    * hooks for the pipeline, such as date stamp `{{ds}}`
    * there is more information in templates reference.
* **dependency**
    * t1.set_downstream(t2) == t1 >> t2
    * t1.set_downstream([t2,t3]) == t1 >> [t2,t3]

* tinezome - timezone aware DAG is simple, dates using pendulum
    * Don’t try to use standard library timezone as they are known to have limitations and we deliberately disallow using them in DAGs.

* command line metadata validation

    * airflow db init
    * airflow dags list
    * airflow tasks list tutorial
    * airflow tasks list tutorial

* Testing
    * airflow tasks test tutirial print_date 2015-06-01

* Backfill
    * airflow dags backfill tutorial --start-date 2015-06-01 --end-date 2015-06-07

# [TaskGroups vs SubDAGs](https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/dags.html#taskgroups-vs-subdags)

* In general, SubDAGs, is a better option given that is purely UI grouping concept.
* All tasks within the TaskGroup still behave as any othe tasks outside the TaskGroup.
* DAG dependency 
    * Triggering - Using TriggerDagRunOperator
    * waiting - ExternalTaskSensor
    * TaskGroup - break down DAG into tasks - should be more appropriate.


# [Trigger Rules](https://airflow.apache.org/docs/apache-airflow/1.10.10/concepts.html#trigger-rules)

* all operators gave trigger_rule arguments, by default, trigger_rule is all_success (trigger it when all directly upstream tasks have succeeded)