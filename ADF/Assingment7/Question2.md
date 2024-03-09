# Create a pipeline name 'Foreach_Example' to copy the Customer & Customer address table data into ADLS using the one copy activity.

## Steps taken 

- 1. Created the Foreach_example pipeline
- 2. Used a lookup activity to extract the customer and customer address table from the saleslt databases with the query below
  ```sql
     SELECT 
  t.name AS TableName
  FROM sys.tables AS t
  INNER JOIN sys.schemas AS s 
  ON t.[schema_id] = s.[schema_id]
  WHERE s.name = N'saleslt' AND t.name = 'Product' OR t.name = 'Customer';
  ```
- 3.  A for-each activity was then used to loop through each table name, and a copy activity was used to move each table's contents to ADLS
  
![image](https://github.com/Idowuilekura/AzureLibPracticeQuestions/assets/38056084/0eb1799e-e2fd-412e-843b-b7ebbde9c97a)
