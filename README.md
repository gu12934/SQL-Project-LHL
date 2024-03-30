# Final-Project-Transforming-and-Analyzing-Data-with-SQL
![image](https://github.com/gu12934/SQL-Project-LHL/assets/36687057/695667bf-9427-4f5c-a39a-52dea437b544)
***
## Project/Goals
In this project, we will combine and practice implementing what we have learned throughout this course, including:

* Extracting data from a SQL database
* Cleaning, transforming and analyzing data
* Loading data into a database
* Developing and implementing a QA process to validate transformed data against raw data
***
## Files that were used

***
README.md file
* This file should be an overview of your project, covering roughly the same points as your presentation

cleaning_data.md file
* Fill out this file with a description of the issues that will be addressed by cleaning the data
Include the queries used to clean the data

startingwithquestions.md file
* Provide the answer to the 5 questions and the queries used to answer each question
startingwithdata.md file
Provide the 3 - 5 new questions you decided could be answered with the data
Include the answer to each question and the accompanying queries used to obtain the answer

QA.md file
* Identify and describe your risk areas
Develop and execute a QA process to address the risk areas identified, providing the SQL queries used to implement

schema.png file
* This file should contain the ERD of the database

***
## Process
### Loading CSV tables into pgadmin

* When loading CSV's into pgAdmin4:
1) right click your public schema. Click Create > Table
2) In the General Tab, name your new table the same as your CSV(i.e. all_sessions)
3) In the columns tab, create each column from your CSV file in the exact order it appears
4) Set each column data type to an acceptable type (remember to adjust Length/scale to either 255 or 550)
5) click save
6) navigate to tables on the left hand menu
7) right click your new table, and click import/export data

* After data is loaded
* 1) conduct sql queries on relevant files and screenshot the results into the project
***
References:
1) https://www.postgresqltutorial.com/postgresql-tutorial/import-csv-file-into-posgresql-table/ 
2) https://www.youtube.com/watch?v=6Jf7eTkIaR4 
***
### Data Cleaning
* dealing with null values, getting rid of them
* Handle missing data - imputing missing values
* address outliers - remove outliers
* data normalization (changing data type)
* duplicate data
* data transformations
***
## Results
* This data could tell me all about customer behaviour and which products are popular in which countres, i used the data to make these queries!
* The data helped me to answer various questions about inventories and tracking
***
## Challenges 
(discuss challenges you faced in the project)
* had a lot of challenges with importing the data, writing a query to import it effectively at first
* doing joins and connecting queries together
* casting as integers
* 
***
## Future Goals
* more data cleaning and joining with other tables
* making a legend for the dataset and table of values
* maybe doing predictive analytics down the line

## Project Presentation
* https://docs.google.com/presentation/d/17vUFTBp6rq80fNdA5jdDX8FNj_PqUAQxWrnVqPet5Sk/edit

