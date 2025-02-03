# Data Engineering Zoomcamp 2025
## Module 2: Workflow Orchestration

To get started, first create a dev.env file containing the database ation using the following template:

```
DB_USER=<mydbuser>
DB_PASS=<my_dbpass>
KESTRA_USER=<my_valid@email.pls>
KESTRA_PASS=<my_kestra_pass>
```

Then run the following command to start the Kestra and the Postgres DB services:

```bash
docker-compose up
```
Kestra UI should now be accesible at http://localhost:8080.
Add the flows to Kestra running the following commands:

```bash
# curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/01_getting_started_data_pipeline.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/02_postgres_taxi.yaml
# curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/02_postgres_taxi_scheduled.yaml
# curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/03_postgres_dbt.yaml
# curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/04_gcp_kv.yaml
# curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/05_gcp_setup.yaml
# curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/06_gcp_taxi.yaml
# curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/06_gcp_taxi_scheduled.yaml
# curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/07_gcp_dbt.yaml
```

