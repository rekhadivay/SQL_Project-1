What are your risk areas? Identify and describe them.



QA Process:
Describe your QA process and include the SQL queries used to execute it.
1.Normalization check---
--to check the leading space in column
select trim(leading ' ' from name) as name
from products2 
2. 
Normalize column--to set fullvisitorid column in all_seesions2 as numeric
UPDATE all_sessions2
SET fullvisitorid = CAST(fullvisitorid AS NUMERIC);

3..Null value checks--
  objective-to ensure that  Transactions and TotalTransactionRevenue columns in all_sessions table have any null value or not, i write sql query--

  SELECT * FROM all_sessions2 WHERE transactions IS not NULL;
  SELECT * FROM all_sessions2 WHERE totaltransactionrevenue IS not NULL;
  i did not remove nulls because removing nulls may affect the results of SQL queries and reports.Null values can be used to maintain data integrity.Removing null values may result in the loss of valuable data, especially if those nulls represent missing or unknown information.
  
4. Duplicate Data Check:
  Objective: Identify and eliminate duplicate records in tables.
  sql query: to check duplicates in fullvisitorid and channelgrouping, i wrote the folowing query

--to check duplicates
select productsku, v2productname,fullvisitorid, count(*) as num_productsku
from all_sessions2
group by productsku, v2productname, fullvisitorid
HAVING count(*) > 1

  SELECT fullvisitorid, channelgrouping
  FROM all_sessions2
  GROUP BY fullvisitorid, channelgrouping

5. --rounding ratio column
select round (ratio, 2) as ratio
from sales_report2
