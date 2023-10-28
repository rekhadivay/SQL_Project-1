Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
```sql
SELECT country, city, SUM(transactionrevenue) AS total_transaction_revenue
FROM all_sessions2
where transactionrevenue is not null
GROUP BY country, city
having  SUM(transactionrevenue) >0
ORDER BY total_transaction_revenue DESC;
```


Answer:
![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/b6df6353-9522-491e-8386-d6486978280b)




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
```sql
SELECT city, country,productsku,v2productcategory, AVG(transactions) AS average_products_ordered
FROM all_sessions2
WHERE transactions IS NOT NULL
GROUP BY city, country, productsku,v2productcategory
ORDER BY city, country, productsku,v2productcategory;
```


Answer:
![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/a1548a6c-fd83-4de0-a01c-dae0f0b47257)






**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**
### -The Pattern i obeserved in this output is that the product type count is of same number for each city and country.

SQL Queries:
```sql
SELECT  visitid,city, country, v2productcategory,v2productname, COUNT(*) AS product_count
FROM all_sessions2
WHERE v2productcategory IS NOT NULL
GROUP BY visitid,city, country, v2productcategory, v2productname
ORDER BY visitid,city, country, product_count DESC;
```



Answer:![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/2b1e2465-af79-44ad-a0a6-a25978f56cee)






**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
```sql
WITH RankedSales AS (
    SELECT
        city,
        country,
        v2productname AS top_selling_product,
        SUM(productquantity) AS total_quantity_sold,
        RANK() OVER (PARTITION BY city, country ORDER BY SUM(productquantity) DESC) AS rank
    FROM
        all_sessions2
    WHERE
        v2productname IS NOT NULL
        AND productquantity IS NOT NULL -- Ensure product quantity is not null
    GROUP BY
        city,
        country,
        v2productname
)

SELECT
    city,
    country,
    top_selling_product,
    total_quantity_sold
FROM
    RankedSales
WHERE
    rank = 1;
```



Answer:![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/64bed222-64fd-4ac4-a6f9-0f3ac8250b15)






**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:
```sql
SELECT
    als.city,
    als.country,
    round(SUM(an.revenue)/1000000:: numeric, 2) AS total_revenue,
    round(AVG(an.revenue)/1000000 :: numeric,2) AS average_revenue,
    MAX(an.revenue)/1000000 AS max_revenue,
    MIN(an.revenue)/1000000 AS min_revenue
FROM analytics2 an
JOIN all_sessions2 als ON an.visitid = als.visitid
WHERE an.revenue IS NOT NULL AND als.city IS NOT NULL AND als.country IS NOT NULL
GROUP BY als.city, als.country
ORDER BY als.city, als.country;
```



Answer:![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/a6e9e268-5eaa-4647-bf9c-71d34a70603e)








