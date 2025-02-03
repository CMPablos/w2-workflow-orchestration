# Data Engineering Zoomcamp 2025
## Homework Solutions for Module 2: Workflow Orchestration 

### Q1. Within the execution for Yellow Taxi data for the year 2020 and month 12: what is the uncompressed file size (i.e. the output file yellow_tripdata_2020-12.csv of the extract task)?

- Comment the block with the purge_files id in the in2_postgres_taxi.yaml flow so no files are removed after the execution.

- Execute flow 02_postgres_taxi with the following variable values: \
<b>taxi type:</b> yellow  \
<b>year:</b> 2020 \
<b>month:</b> 12 

- Go to Executions > Outputs, elect extract under Tasks, then outputFiles. The file size should be on the right side.

<b>Answer</b>: 128.3MB


### Q2. What is the rendered value of the variable file when the inputs taxi is set to green, year is set to 2020, and month is set to 04 during execution?

The unrendered value is "{{inputs.taxi}}_tripdata_{{inputs.year}}-{{inputs.month}}.csv", to get the answer simply replace each variable inside the {{}} brackets.

<b>Answer</b>: green_tripdata_2020-04.csv

### Q3. How many rows are there for the Yellow Taxi data for all CSV files in the year 2020?

- Backfill the yellow taxi data for all 2020 as following:
    - In the kestra UI:
        - Go to flows on the left side menu
        - Open flow with Id 02_postgres_taxi_scheduled
        - Go to the Triggers tab at the top
        - Open Backfill executions for Id yellow_scedule
        - On the Start and End inputs select 2020-01-01 and 2020-12-31
        - Make sure taxi type is set as yellow
        - Fill in the DB credentials
- Once the backfill finishes, go to pgAdmin and connect to the 'kestra' database
- Run the following query to count the number of rows for 2020 yellow taxi data:
```SQL
SELECT count(1) FROM yellow_tripdata 
WHERE filename LIKE 'yellow_tripdata_2020%'
```
<b>Answer</b>: 24,648,499

### Q4. How many rows are there for the Green Taxi data for all CSV files in the year 2020?

- Backfill the 2020 green taxi data following the steps for Q3
- Run the following query to get the total number of rows for 2020 green taxi data:
```SQL
SELECT count(1) FROM green_tripdata 
WHERE filename LIKE 'green_tripdata_2020%'
```
<b>Answer</b>: 1,734,051

### Q5. How many rows are there for the Yellow Taxi data for the March 2021 CSV file

- Backfill the yellow taxi data from 2021-03-01 00:00:00 to 2021-03-31
- Run the following query to get the total number of rows for yellow taxi data, Mach 2021:
```SQL
SELECT count(1) FROM yellow_tripdata 
WHERE filename LIKE 'yellow_tripdata_2021-03%'
```
<b>Answer</b>: 1,925,152

### Q6. How would you configure the timezone to New York in a Schedule trigger?

- As an example, a trigger set to the New York timezone would be configured as following:

```YAML
triggers:
    - id: newyork_schedule
      type: io.kestra.plugin.core.trigger.Schedule
      cron: 0 10 1 * *
      timezone: America/New_York
```

<b>Answer</b>: Add a timezone property set to America/New_York in the Schedule trigger configuration.