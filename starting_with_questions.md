Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
```
SELECT
country, SUM(total_transaction_revenue) AS total_transaction_revenue
FROM all_sessions
WHERE total_transaction_revenue !=0
GROUP BY country
GROUP BY total_transaction_revenue DESC;
```

```
SELECT
country,city, SUM(CAST(all_sessions2.totaltransactionrevenue AS integer)) AS total_transaction_revenue
FROM all_sessions2
GROUP BY country, city
ORDER BY total_transaction_revenue DESC
```

 SELECT countries, cities, sum(revenues) as revenue FROM table as s1  JOIN table as s2 ON s1.ID = s2.ID ORDER BY revenue desc



Answer:




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:

SELECT countries, cities, visitor average(productsOrdered) as averageProductOrdered FROM table as s1 JOIN table as s2 ON s1.ID=s2.ID ORDER BY averageProductOrdered desc

Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







