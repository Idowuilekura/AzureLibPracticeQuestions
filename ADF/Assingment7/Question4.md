# Create a pipeline that will create the incremental pipeline for the customer table using the table instead of HighWaterMark File.
The question aims to create a pipeline that copies data from an SQL server table in an incremental manner. The process involves copying all data records from the last time the record was inserted into the database.
Steps taken
- 1. Created the pipeline
- 2. Created a table called (Saleslt.HighwaterMark), which holds the last modified time
  3. A lookup activity was used to get the time value from the highwater mark table
  4. Another lookup activity was used to get the highest timestamp from the customer table
  5. A copy activity was done to copy the content of the customer data for all records that are greater than the highwatermark value and less than or equal to the highest time in the customer table
```sql
SELECT *
FROM 
saleslt.customer 
WHERE modifieddate > '@{activity('get the high water mark value').output.value[0].LastModified}' AND modifieddate <= '@{activity('get the last modified date from the customer table').output.value[0].lastmodifieddate}'
```
6. A script activity was used to remove the previous record and update the table with the highest timestamp in the customer table

```sql
TRUNCATE TABLE saleslt.highwatermark;

INSERT INTO saleslt.highwatermark SELECT '@{activity('get the last modified date from the customer table').output.value[0].lastmodifieddate}';
```

![image](https://github.com/Idowuilekura/AzureLibPracticeQuestions/assets/38056084/e86dc82d-8315-4ffd-88cd-b3952dedb1dc)

