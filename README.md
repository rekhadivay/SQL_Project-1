# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
While working with sales_reports,products,all_sessions,analytics and sales_by_sku tables for Transforming and Analyzing Data with SQL Project, our main goals are to find important information, make things work better, and choose the right actions. 
We look for trends and patterns in the data and spot any unusual things.If something strange happens in the data, we want to notice it.
By analysing various aspects of user visits,visit numbers,user interaction  and their impact on sales and engagement metrics,
the project aims to increase revenue. We figure out which products sell the most and make the most money.
We also understand what products people like on the website, how much time they spend. 
Utilize the date column for time-series analysis to identify trends and seasonality in user behavior and sales.
Finally, we make the data more suitable for studying and modeling.

## Process
### STEP 1--Imported csv files into pgadmin
### STEP 2--Cleaning(Date and Time Format change, change data types, removing nulls etc.),Quality Assurance steps(nulls and Duplicate checks,Data consistency checks) transformed and analyzed data( .
### STEP 3--Answered the questions based on the provided data
### STEP 4--Loaded final tables(ERD) into database 

## Results
### 1.Product Data:
The columns related to products, such as "productsku", "v2productname," "v2productcategory," and "productprice," provide information about the products sold on the site. we analyzed which products are popular and their pricing.
### 2.User Engagement:
The "pageviews" and "timeonsite" , columns provide insights into user engagement. we can analyzed which pages are viewed the most and how much time, on average, users spend on the site.
### 3.Geographical Information:
The "country" and "city" columns allow you to identify the geographic locations of users. This can help in targeting specific regions for marketing or understanding the site's global reach.
### 4.Transaction Data:
Columns like "totaltransactionrevenue" and "transactions" contain transaction-related information. we determined the total revenue generated and the number of transactions, providing insights into the site's financial performance.
### 5.Date and Time Analysis:
Analyzing the "date" and "time" columns reveal patterns and trends over time. For example,we identify busy seasons or times of the day when user activity is higher.
## Challenges 
i faced many challenges because the data we have been provided was very messy. lots of nulls values, duplicates, leading whitespace etc.The data has missing or unclear information ("(not set)"). Dealing with messy data can be like trying to solve a puzzle with missing pieces.To get answers, i needed to change how the data looks for example, date,time format, data type, unitprice formatting.There's a lot of data in Analytics table, it slow down my computer.
## Future Goals
if i would have more time, i would throughly clean the data for better understanding and deeper analysis.Dive deeper into user behavior analysis to optimize website features,product categories, content, and design for improved user experiences.
