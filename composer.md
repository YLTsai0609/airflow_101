# Google Composer & Airflow

* Google 代管的 Airflow
* [doc](https://cloud.google.com/composer/docs/concepts/features)
  * GKE cluster - scheduler, workers, queue run as GKE workloads
  * web server - airflow web interface
  * database - hold airflow metadata
  * cloud storage - store DAGs, logs, custom pligins, daya for the environments

## Managements
* web interface
* command line tools - `gcloud composer environments`
* REST, RPC API provide programmatic access to your airflow environments.
* `gcloud composer environments describe ENVIRONMENT_NAME \
  --location LOCATION`
* `gcloud beta composer environments restart-web-server ENVIRONMENT_NAME \
  --location=LOCATION`