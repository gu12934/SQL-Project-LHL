Answer the following questions and provide the SQL queries used to find the answer.

    
## Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:


```
SELECT
country,city, SUM(CAST(all_sessions2.totaltransactionrevenue AS integer)) AS total_transaction_revenue
FROM all_sessions2
GROUP BY country, city
ORDER BY total_transaction_revenue DESC
```

Answer:

<img width="369" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/9c97825e-d6c1-4906-a23b-040897010552">

## Question 2: What is the average number of products ordered from visitors in each city and country?**

SQL Queries:

```
SELECT country, city, AVG(all_sessions2.productquantity::INTEGER) AS avg_product
FROM all_sessions2
GROUP BY country, city 
ORDER BY avg_product DESC;
```

Answer:

<img width="367" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/8fdb94b1-3afe-4252-9fd3-570d08107b93">


## Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**

SQL Queries:
```
SELECT country, city, (all_sessions2.v2productcategory::VARCHAR) AS product_category 
FROM all_sessions2 
GROUP BY all_sessions2.v2productcategory,all_sessions2.country, all_sessions2.city
ORDER BY product_category DESC;
```

<img width="448" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/95f008a0-7026-47f0-8a13-b4ff51cf9425">


```
SELECT country, city, "v2productcategory"::VARCHAR AS product_category, COUNT(*) AS category_count
FROM all_sessions2
GROUP BY country, city, "v2productcategory"
ORDER BY category_count DESC;
```

Answer:

<img width="558" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/54ef6fab-0494-469c-8799-f2cd6f7298e4">




## Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:

```
SELECT country, city, pagetitle, "v2productcategory"::VARCHAR AS product_category, COUNT(*) AS category_count
FROM all_sessions2
GROUP BY country, city,pagetitle, "v2productcategory"
ORDER BY category_count DESC;
```

<img width="612" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/de454a56-bea7-4eab-bfb4-ae2adc659e59">

It seems that 103 items were bought from NEST USA

Answer:


```
SELECT country, city, pagetitle, v2productname, "v2productcategory"::VARCHAR AS product_category, COUNT(*) AS category_count
FROM all_sessions2
GROUP BY country, city,pagetitle,v2productname, "v2productcategory"
ORDER BY category_count DESC;
```

<img width="607" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/bc708cf2-ab02-4517-ae49-24106483a6f9">

<img width="486" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/54d51e33-315e-412b-827c-fbb7a95e3ef9">



## Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

```
SELECT country, city, (all_sessions3.totaltransactionrevenue)::INTEGER AS total_revenue
FROM all_sessions3
GROUP BY country, city, 3
ORDER BY total_revenue DESC;
```


Answer:

<img width="326" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/2a385abf-fa83-41b1-a0dc-24d99d1a2446">

```
SELECT country, city, (all_sessions3.totaltransactionrevenue)::INTEGER AS total_revenue, SUM(CAST(productquantity AS INTEGER))
FROM all_sessions3
GROUP BY country, city, 3
ORDER BY total_revenue DESC;
```
Answer:

<img width="382" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/878fed4c-b6bb-409e-a004-acfe016ba941">








