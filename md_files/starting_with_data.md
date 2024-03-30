***
## Task
Provide the 3 - 5 new questions you decided could be answered with the data
Include the answer to each question and the accompanying queries used to obtain the answer
 
 - find the total number of unique visitors by referring sites

- compute the percentage of visitors to the site that actually makes a purchase
***
## Question 1:  find the total number of unique visitors (fullVisitorID)


SQL Queries:

```
SELECT COUNT(DISTINCT fullVisitorId) AS total_unique_visitors
FROM public.all_sessions3;
```

Answer: 

<img width="161" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/33e19344-f121-44b2-be24-9f1b1401f338">



## Question 2:  find each unique product viewed by each visitor
SQL Queries:
```
SELECT fullVisitorId, v2ProductName
FROM all_sessions3
GROUP BY fullVisitorId, v2ProductName;
```

Answer:

<img width="412" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/443d6aae-be28-4657-9f4e-03d3b5d84658">



## Question 3: find all duplicate records

SQL Queries:
```
SELECT fullVisitorId, visitId, COUNT(*) AS duplicate_count
FROM public.all_sessions3
GROUP BY fullVisitorId, visitId
HAVING COUNT(*) > 1;
```

Answer:

<img width="321" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/3bc23a84-d061-4585-b08e-1e2927a83a52">


