What issues will you address by cleaning the data?

## Theory

1) dealing with null values

2) Handle missing data - imputing missing values

3) address outliers - remove outliers

4) data normalization (changing data type)

5) duplicate data

6) data transformations


## Process

Step 1: Retrieve sample data

Step 2: Explore unique values

Step 3: View the value of orderdate and requireddate.

Step 4: Identify missing and extreme values

Step 5: Choose the best tool to proceed

Step 6: Communicate your data-cleaning approach



## Cleaning hint: The unit cost in the data needs to be divided by 1,000,000.


## Queries:
Below, provide the SQL queries you used to clean your data.

## all_sessions2

-identify missing values
```
SELECT DISTINCT country, city
from all_sessions2
group by country,city
```

-look at all countries
```
SELECT DISTINCT *
from all_sessions2
WHERE country IN('(not set)')
OR City IN ('(not set)', 'not available in demo dataset');
```

-delete rows with non set values
```
DELETE from all_sessions2
WHERE country IN ('(not set)')
```
<img width="230" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/7ae21ef6-b2a6-48cb-80ee-5a6e6dea1033">

-delete rows with values in city column
```
DELETE FROM all_sessions2
WHERE city in ('(not set)', 'not available in demo dataset')
```
<img width="230" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/c642fbb2-d8e4-46b3-8083-290032aeb1f4">

-replace null values with 0 in total transaction revenue
```
UPDATE all_sessions2
SET totaltransactionrevenue = COALESCE(CAST(all_sessions2.totaltransactionrevenue AS integer), 0);
```
<img width="255" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/e4b2b382-7d4a-43dc-a832-0fe3e70c4b58">

-coalesce the null values in product column
```
UPDATE all_sessions2
SET productquantity = COALESCE(CAST(all_sessions2.productquantity AS integer), 0)
```
<img width="239" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/2be7fc09-f033-40bf-8244-5afdd4c09445">

-coalesce null values in transaction revenue column
```
UPDATE all_sessions2
SET productquantity = COALESCE(CAST(all_sessions2.transactionrevenue AS integer), 0)
```
<img width="235" alt="image" src="https://github.com/gu12934/SQL-Project-LHL/assets/36687057/15b742d1-fd82-479a-b955-53351e385255">


```
SELECT
visitid,
country,
city,
productsku,
productprice
--itemquantity col is nul, try to infer from productric and transactionrevenue
(totaltransactionrevenue /  productprice)::INT AS itemquantity,
ROUND(totaltransactionrevenue/ productprice,2) decimal_quantity,
totaltransactionrevenue
FROM
all_sessions2
WHERE totaltransactionrevenue IS NOT NULL
ORDER BY visitid)

-- leave null values null, update not null with decimal value
UPDATE all_sessions2
SET
totaltransactionrevenue=
CASE
WHEN totaltransactionrevenue IS NULL THEN NULL
ELSE (totalttransactionrevenue/1000000.0)::NUMERIC(10,2)
END
productprice=CASE
WHEN productprice IS NULL THEN NULL
ELSE(productprice/100000.0)::NUMERIC(10,2)
END,
productrevenue=
CASE WHEN productrevenue IS NULL THEN NULL
ELSE (prodcuctrevenue/1000000.0)::NUMERIC(10,2)
END, transactionrevenue=CASE WHEN transactionrevenue IS NULL THEN NULL
ELSE (transaction revenue/100000.0)::NUMERIC(10,2)

cleaning all_sessions 2

SELECT DISTINCT "time"
FROM all_sessions2
WHERE "time" is not NULL

create temporary table all_sessions_temp
AS 
SELECT * from all_sessions2

update all_sessions_temp
SET "time" = TO_TIMESTAMP("time": double precision);

-----------------------------------------------------------------
```

```
SELECT Customers.CustomerID, COUNT(*) AS TotalOrders
FROM Customers
INNER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
INNER JOIN Shippers ON Orders.ShipVia=Shippers.ShipperID
WHERE Orders.ShipCountry='Germany'
GROUP BY Customers.CustomerID
HAVING COUNT(*) > 5
ORDER BY TotalOrders DESC
LIMIT 10;

SELECT Customers.CustomerID, SUM(order_details.UnitPrice * order_details.Quantity) AS TotalOrders
FROM Customers
INNER JOIN Orders on Customers.CustomerID=Orders.CustomerID
INNER JOIN order_details ON Orders.OrderId=order_details.OrderId
GROUP BY Customers.CustomerID
HAVING SUM(order_details.UnitPrice * order_details.Quantity) > 50000;

SELECT EXTRACT(MONTH FROM Orders.OrderDate) AS OrderMonth, AVG(order_details.UnitPrice*order_details.Quantity) AS A AvgOrderValue
FROM Orders
INNER JOIN order_details ON Orders.OrderID=order_details.OrderID
WHERE EXTRACT(YEAR FROM Orders.OrderDate)=1997
GROUP BY EXTRACT(MONTH FROM Orders.OrderDate);

SELECT Categories.CategoryName, SUM(order_details.UnitPrice * order_details.Quantity) AS TotalRevenue
FROM Categories
INNER JOIN Products ON Categories.CategoryID=Products.CategoryID
INNER JOIN order_details ON Products.ProductID=order_details.ProductID
GROUP BY Categories.CategoryName;


SELECT Customers.CustomerID, SUM(order_details.UnitPrice * order_details.Quantity) AS TotalSales
FROM Customers
INNER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
INNER JOIN order_details ON Orders.OrderID=order_details.OrderID
GROUP BY Customers.CustomerID;

SELECT Customers.CustomerID, AVG(order_details.UnitPrice*order_details.Quantity) AS AvgOrderValue
FROM Customers
INNER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
INNER JOIN order_details ON Orders.OrderID=order_details.OrderID
GROUP BY Customers.CustomerID;
```

## analytics

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

## products
```
SELECT COUNT(*) AS num_productsku, productsku,productname
FROM product
GROUP BY productksu, productname
HAVING CONUT(*) >1
```

```
-- PRODUCTS TABLE
-- Look for null values
SELECT *
FROM products
WHERE NOT (products IS NOT NULL);

-- Look for duplicate skus
SELECT sku, count()
FROM products
GROUP BY sku
HAVING count() > 1

-- TRIM sku and name columns for any extra space
-- Fill out with 0 null values from columns sentiment_score and sentiment_magnitude
-- Order table by sku
-- Create a view of the cleaned table
CREATE OR REPLACE VIEW working_products AS 
    SELECT 
        TRIM(sku) AS sku,
        TRIM(name) AS product_name,
        ordered_quantity,
        stock_level,
        restocking_lead_time,
        CASE 
            WHEN sentiment_score IS NULL THEN 0
            ELSE sentiment_score
        END AS sentiment_score,
        CASE
            WHEN sentiment_magnitude IS NULL THEN 0
            ELSE sentiment_magnitude
        END AS sentiment_magnitude
    FROM products
    ORDER BY sku;

-- Make an empty copy of the original table 
CREATE TABLE clean_products AS
TABLE products
WITH NO DATA;

-- Insert clean data from the view table into the new clean table
INSERT INTO clean_products
SELECT * FROM working_products;

-- Rename column name
ALTER TABLE clean_products
    RENAME COLUMN name TO product_name;
```



## sales_by_sku

## sales_report
