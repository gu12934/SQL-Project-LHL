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
## Process
### Loading CSV tables into pgadmin

When loading CSV's into pgAdmin4:
1) right click your public schema. Click Create > Table
2) In the General Tab, name your new table the same as your CSV(i.e. all_sessions)
3) In the columns tab, create each column from your CSV file in the exact order it appears
4) Set each column data type to an acceptable type (remember to adjust Length/scale to either 255 or 550)
5) click save
6) navigate to tables on the left hand menu
7) right click your new table, and click import/export data

References:
1) https://www.postgresqltutorial.com/postgresql-tutorial/import-csv-file-into-posgresql-table/ 
2) https://www.youtube.com/watch?v=6Jf7eTkIaR4 
***
### Data Cleaning
* Data cleaning process
* dealing with null values
* Handle missing data - imputing missing values
* address outliers - remove outliers
* data normalization (changing data type)
* duplicate data
* data transformations
***
### Next steps
* startingwithquestions.md file
* startingwithdata.md file
* QA.md file
* schema.png file

-Continue doing the data cleaning and adding more tables/joins to the project
***
## Results
This data could tell me all about customer behaviour and which products are popular in which countres, i used the data to make these queries!
(fill in what you discovered this data could tell you and how you used the data to answer those questions)
***
## Challenges 
(discuss challenges you faced in the project)
* had a lot of challenges with importing the data, writing a query to import it effectively at first
* doing joins and connecting queries together
* casting as integers
***
## Future Goals
(what would you do if you had more time?)
* more data cleaning
* making a legend for the dataset and table of values
* maybe doing predictive analytics down the line

## Project Presentation
* https://docs.google.com/presentation/d/17vUFTBp6rq80fNdA5jdDX8FNj_PqUAQxWrnVqPet5Sk/edit

