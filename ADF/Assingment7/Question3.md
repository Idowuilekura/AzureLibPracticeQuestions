# 3. Create a pipeline that first checks whether the Customer.csv file is available in the folder location. It will copy the file data to the Customer Table if it is available.

Step taken

- 1. Created the pipeline 
- 2. Used the get metadata activity to get the child items in the folder of interest 
- 3. Used the for-each activity to loop through the output of the get metadata activity 
- 4. Used the if-else condition to check if the file type is a file and if the name of the file is customer.csv
- 5. If the output is true then copy the file to the customer directory. 

![image](https://github.com/Idowuilekura/AzureLibPracticeQuestions/assets/38056084/f0da0a0c-bca4-4d4b-89ec-6c68a5bb47ca)

