### Question 1: Which products have been ordered the most in descending order of ordered quantity?

```sql
SQL Queries: 
SELECT SKU, name, orderedQuantity
FROM products2
ORDER BY orderedQuantity DESC
limit 10;
```

### Answer: ![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/bbb89f9a-61c6-4cf3-88c9-b3ba508ced33)




### Question 2: How many products have a restocking lead time of 8 days (from Products2 table)
SQL Queries:
```sql
SELECT COUNT(*) AS num_products
FROM products2
WHERE restockingLeadTime = 8;
```

### Answer: ![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/cd0b2ced-4c3f-4397-bb27-d2f90bb2a511)




### Question 3: What are the products with a sentiment score greater than 0.5 and a stock level less than 50 but greater than 0?order them in descending order.

SQL Queries:
```sql
SELECT SKU as productsku, name as productname, sentimentscore, stocklevel
FROM products2
WHERE (sentimentScore > 0.5) AND (stockLevel < 50 and stocklevel > 0)
order by sentimentscore, stocklevel desc;
```

### Answer:  ![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/ba2c1cf0-a22e-422d-880a-e13637a68b4c)





### Question 4: What is the average sentiment score and  sentiment magnitude for products with a stock level greater than 100?

SQL Queries:
```sql
SELECT AVG(sentimentScore) AS avg_sentiment_score, AVG(sentimentMagnitude) AS avg_sentiment_magnitude
FROM products2
WHERE stockLevel > 100;
```

### Answer: ![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/23d40c6a-4811-460a-8163-8fc22a162fee)




### Question 5: Find top 5 products by sentiment score and with a stock level less than 20.

SQL Queries:
```sql
SELECT SKU as productsku, name as productname, stockLevel,sentimentscore
FROM products2
WHERE stockLevel < 20
ORDER BY sentimentScore DESC
LIMIT 5;
```

### Answer:  ![image](https://github.com/rekhadivay/SQL_Project-1/assets/116858892/68ddff33-9578-4633-857a-bda4ccb1386f)

