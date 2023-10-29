What issues will you address by cleaning the data?

##Theory

1) dealing with null values

2) Handle missing data - imputing missing values

3) address outliers - remove outliers

4) data normalization (changing data type)

5) duplicate data

6) data transformations


##Process

Step 1: Retrieve sample data

Step 2: Explore unique values

Step 3: View the value of orderdate and requireddate.

Step 4: Identify missing and extreme values

Step 5: Choose the best tool to proceed

Step 6: Communicate your data-cleaning approach



##Cleaning hint: The unit cost in the data needs to be divided by 1,000,000.


##Queries:
Below, provide the SQL queries you used to clean your data.

all_sessions2

analytics


update analytics
```
ALTER TABLE analytics
ALTER COLUMN unit_price TYPE DECIMAL;

ALTER TABLE analytics
RENAME COLUMN unit_price TO unitprice;

UPDATE analytics
SET unitprice=
CASE
WHEN unitprice iS NOT NULL THEN (unitprice/100000.0)::DECIMAL(10,2)
ELSE unitprice
END;

conversion of data types
SELECT *
FROM sales_analytics
JOIN sales_sessions USING
(fullvisitorid)
WHERE 
productprice=sales
OR productprice=unitprice
OR revenue=totaltransactionrevenue

SELECT * FROM analytics
WHERE fullvisitorid='3758780440084540279'
ORDER BY UNITPRICE
```

products

sales_by_sku

sales_report
