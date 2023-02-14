What are your risk areas? Identify and describe them.
- NULL value : since this is a large dataset, there might be null values that will affect the result. 
- Country/City value : since this is an ecommerce databadse, it is important to know where the customers are from. Thus, country and city  cannot have values other than places. 



QA Process:
Describe your QA process and include the SQL queries used to execute it.
```
SELECT "fullVisitorId","city","country"
FROM all_sessions
WHERE ("city" = 'not available in demo dataset' AND "country" = '(not set)')
```