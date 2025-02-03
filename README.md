# Data Engineering Zoomcamp 2025
## Module 2: Workflow Orchestration

To get started, first create a dev.env file containing the database ation using the following template:

```
DB_USER=<mydbuser>
DB_PASS=<my_dbpass>
KESTRA_USER=<my_valid@email.pls>
KESTRA_PASS=<my_kestra_pass>
```

Then run the following command to start the Kestra, Postgres DB and pgAdmin services:

```bash
docker-compose up
```
Kestra UI and pgAdmin should now be accesible at http://localhost:8080 and http://localhost:8090 respectively.

Add the content inside the flows/ directory to Kestra running the following commands:

```bash
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/02_postgres_taxi.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/02_postgres_taxi_scheduled.yaml
```

