What issues will you address by cleaning the data?
### Issues while Data cleaning process---
While working with data i found many issues. There were many Null Values, Duplicate data, Inconsistent Data,outliers, Normalization issues etc.Understanding the context of your data is crucial. Sometimes, what appears to be a duplicate,null value or outliers might actually hold essential contextual information. Removing them can lead to misinterpretations.
 Duplicate and null records can lead to inaccurate results and skewed statistics but removing them also can lead to a loss of potentially valuable information. 
In some cases, they might carry unique identifiers that are significant for analysis. maintaining duplicates or null values may be necessary to preserve the original data's size and structure. 
Deleting them could result in a dataset that no longer accurately represents the real-world situation.Aggressive data cleaning can involve data manipulation, loss of Context which may not accurately represent the original dataset.  Removing outliers, duplicates, or null values without proper analysis can lead to an incomplete dataset, potentially eliminating critical insights.
i also had many issues while removing nulls , removing duplicates in data cleaning process because removing all nulls can harm to data size. 
 


### Queries:
Afrer observing the Data carefully and thorough understanding of the project's requirements, specifications, and quality standards, i found that there are many null values, duplicate values, leading space, date and time format,  in data which is irelavent etc. i tried to change the date and time format. i backed up the tables first not to change the original tables.
Here's a description of the cleaning process that includes SQL queries i used to execute them:
### 1.Null value checks--
  To ensure that  Transactions and TotalTransactionRevenue columns in all_sessions table have any null value or not, i write sql query--
```sql
  SELECT *
FROM all_sessions2
WHERE transactions IS not NULL;
```
Another--
```sql
  SELECT *
FROM all_sessions2
 WHERE totaltransactionrevenue IS NULL;
```

  i did not remove nulls because removing nulls may affect the results of SQL queries and reports.Null values can be used to maintain data integrity.Removing null values may result in the loss of valuable data, especially if those nulls represent missing or unknown information.
  
  
### 2.Remove duplicates---  
 I selected 2 columns to delete duplicates from all_sessions which are fullvisitorid, visitid. i want to set fullvisitorid as PK thats why i deleted the duplicates. i first checked that with sql query. 
 ```sql
Select distinct fullvisitorid, visitid
 from all_sessions2
```
 
To remove duplicates i created different table named unique_all_sessions_2 with distinct values

```sql
SQL query--
  create table unique_all_sessions2 as 
  select distinct fullvisitorid, visitid
  from all_sessions2
```
  
### 3. To change Data type and Time format in timeonsite i used the below query--
```sql
alter table all_sessions2
alter column timeonsite type time using to_char((timeonsite || 'seconds')::interval,'HH24:MI:SS')::time;
```

### 4.To change Time format i wrote the below sql query--
```sql
alter table all_sessions2
alter column time type time using to_char((time || 'seconds')::interval,'HH:MI:SS')::time;
```

### 5.Date format--
To change date format which was in 8 digit, i created new column new_date and drop the old column, date. i used the below query for that--
```sql
ALTER TABLE all_sessions2
ADD COLUMN new_date varchar;

UPDATE all_sessions2
SET new_date = TO_CHAR(TO_DATE(cast(date as text), 'YYYYMMDD'), 'YYYY-MM-DD');

alter table all_sessions2
drop column date
```

### 6. To change productprice column format, the SQL query i used--

```sql
update all_sessions2
set productprice= productprice/1000000
```
### 7. To change unit_price column format, the SQL query i used--
 ```sql
update analytics2
set unit_price= unit_price/1000000
```

### 8. To alter the leading whitespace in name column
```sql
update products2
set name = trim(leading ' ' from name);
```

### 9. --to set fullvisitorid as numeric
```sql
UPDATE all_sessions2
SET fullvisitorid = CAST(fullvisitorid AS NUMERIC);
```
