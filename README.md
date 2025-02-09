# data_warehouse
Q1. 20,332,093

```
SELECT COUNT(*) AS total_records
FROM `kestra-week2.hw3.yellow_taxi_2024`;
```

Q2. 0 MB for the External Table and 155.12 MB for the Materialized Table

This query will process 0 B when run.

This query will process 155.12 MB when run.

Q3: 

BigQuery is a columnar database, and it only scans the specific columns requested in the query. Querying two columns (PULocationID, DOLocationID) requires reading more data than querying one column (PULocationID), leading to a higher estimated number of bytes processed.

Q4: 8,333

```
SELECT COUNT(*) FROM kestra-week2.hw3.yellow_taxi_2024 WHERE fare_amount=0; 
```

Q5. Partition by tpep_dropoff_datetime and Cluster on VendorID

Q6. 310.24 MB for non-partitioned table and 26.84 MB for the partitioned table

```sql
CREATE OR REPLACE TABLE `kestra-week2.hw3.optimized_yellow_taxi` 
PARTITION BY DATE(tpep_dropoff_datetime)
CLUSTER BY VendorID
AS
SELECT *
FROM `kestra-week2.hw3.yellow_taxi_2024`;

SELECT distinct VendorID FROM `kestra-week2.hw3.yellow_taxi_2024` where DATE(tpep_dropoff_datetime) between '2024-03-01' and '2024-03-15'; 
SELECT distinct VendorID FROM `kestra-week2.hw3.optimized_yellow_taxi` where DATE(tpep_dropoff_datetime) between '2024-03-01' and '2024-03-15'; 
```

Q7. GCP Bucket

Q8. False

Q9. This query will process 0 B when run.

because BigQuery uses metadata from the materialized table to return the count without scanning the actual data.
