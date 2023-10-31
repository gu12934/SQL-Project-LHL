## What are your risk areas? Identify and describe them.

complete (i.e. no blank or null values)
unique (i.e. no duplicate values)
consistent with what we expect (eg. a decimal between a certain range)


## QA Process:
Describe your QA process and include the SQL queries used to execute it.


## find all duplicate records

SQL Queries:

SELECT fullVisitorId, visitId, COUNT(*) AS duplicate_count
FROM public.all_sessions3
GROUP BY fullVisitorId, visitId
HAVING COUNT(*) > 1;


Answer:
<img width="321" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/3bc23a84-d061-4585-b08e-1e2927a83a52">


## pecularities within the data showing transaction revenue but no product quantity corresponding to the entries

SQL Queries:

SELECT country, city, (all_sessions3.totaltransactionrevenue)::INTEGER AS total_revenue, SUM(CAST(productquantity AS INTEGER))
FROM all_sessions3
GROUP BY country, city, 3
ORDER BY total_revenue DESC;



<img width="380" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/93dded01-2e3a-4f3d-9924-edc2d7c2ba4f">




Identify and describe your risk areas

Develop and execute a QA process to address the risk areas identified, providing the SQL queries used to implement

Final project SQL presentation - https://docs.google.com/presentation/d/17vUFTBp6rq80fNdA5jdDX8FNj_PqUAQxWrnVqPet5Sk/edit?usp=sharing
