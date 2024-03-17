We have a scenario where we need to update customer password details using the Type 3 Slowly Changing Dimension (SCD) methodology. The objective is to archive the current password in the "old password" column and update it with the new password in the "current password" column for each new password record.

The process was done using Azure Data Factory Data Flow 

Steps
- 1. The first step was to create the database with four columns: the id, name, password_current to hold the current password and password_old to hold the old password.
- 2. The second step was to insert records into the database
  3. The next step was to upload a text file to Azure Data Lake Storage
  4. The next step was to create a new data flow object in ADF in which the flows will be saved
  5. Two sources were created which is for the table in the database and the file in the ALDS
  6. A select function was used to select the id, name, current password and old_password column with a suffix of db added to the column name(this was done in order to specify columns from the database.
  7. A lookup function was used to find the ID in the file and the database; this was done to check for IDs that were present in the database.
  8. A filter function was used to select only id with the corresponding ID in the database using the `!isnull(id_db)`
  9. A select function was used to select the id, name, password and password_current from the matched lookup
  10. A derived column function was used to set the `password_old` column to the current password from the database and the `password_current` to the password from the file
  11. For the records that were not matched in the lookup activity, a filter function was used to find the records that didn't exit. After which the process applied to the records that match were also used for this
 
   ![image](https://github.com/Idowuilekura/AzureLibPracticeQuestions/assets/38056084/cc3ae245-285d-4457-bd5d-443e1210d59f)

 
   
     
