## 1. Create a pipeline named 'GetMetaData_Example' to fetch the list of all the files available inside the ADLS folder.

Step taken
- 1. Created the pipeline with the specified name
- 2. Used a get metadata pipeline to get all the child items of the container(folder) in ADLS
- 3. Pass the output of the get metadata into a forEach activity to loop through each of the outputs of the get metadata activity 
- 4. For each item in the array, I used an if-else activity to check if the type of the item is a file. 
- 5. If the item type is a file, a copy activity is executed to copy the content from one folder to the next and if the type is not a file, nothing is executed 

![image](https://github.com/Idowuilekura/AzureLibPracticeQuestions/assets/38056084/0dae6b26-19c6-48fa-8c09-af9ac1d066f2)
