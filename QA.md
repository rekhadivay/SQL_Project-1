What are your risk areas? Identify and describe them.
### Risk areas in QA process--1.Data Completeness:
Description: The presence of null or missing values in several columns, such as "totaltransactionrevenue," "country," and "city," indicates a risk of incomplete data.
Impact: Incomplete data can lead to inaccurate analysis and reporting, as well as potential issues in data transformations and calculations.
### 2.Data Consistency:
Description: The use of various placeholder values like "(not set)" in the "country" and "city" columns suggests data consistency issues.
Impact: Inconsistent data can make it challenging to perform meaningful analysis or join data with other sources accurately.
### 3. Data Accuracy and source reliability:
Description: The presence of unexpected or inconsistent values, such as "not available in demo dataset" in the "country" column, suggests potential data accuracy problems and may indicate uncertainity or unrelibility of datasources.
Impact: Inaccurate data can lead to incorrect insights and decision-making.
### 4.Data Duplication:
Description: Identical rows with the same data can be seen, such as multiple entries with the same name in  "v2productname."
Impact: Data duplication can distort analysis and inflate transaction or revenue figures if not handled appropriately.

### QA Process:
Describe your QA process and include the SQL queries used to execute it.
### 1.Normalization check---
--to check the leading space in column
select trim(leading ' ' from name) as name
from products2 
2. 
### Normalize column--to set fullvisitorid column in all_seesions2 as numeric
UPDATE all_sessions2
SET fullvisitorid = CAST(fullvisitorid AS NUMERIC);

### 3..Null value checks--
  objective-to ensure that  Transactions and TotalTransactionRevenue columns in all_sessions table have any null value or not, i write sql query--

  SELECT * FROM all_sessions2 WHERE transactions IS not NULL;
  SELECT * FROM all_sessions2 WHERE totaltransactionrevenue IS not NULL;
  i did not remove nulls because removing nulls may affect the results of SQL queries and reports.Null values can be used to maintain data integrity.Removing null values may result in the loss of valuable data, especially if those nulls represent missing or unknown information.
  
### 4. Duplicate Data Check:
  Objective: Identify and eliminate duplicate records in tables.
  sql query: to check duplicates in fullvisitorid and channelgrouping, i wrote the folowing query
--to check duplicates

```sql
 select productsku, v2productname,fullvisitorid, count(*) as num_productsku
 from all_sessions2
 group by productsku, v2productname, fullvisitorid
 HAVING count(*) > 1
```

### 5. Rounding ratio column
```sql
select round (ratio, 2) as ratio
from sales_report2
```
### 6. data consistency check:
```sql
SELECT city, country
FROM all_sessions2
WHERE (country != 'not set') and (city != 'not available in demo dataset') and (city != '(not set)')
```

