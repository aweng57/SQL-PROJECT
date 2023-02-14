Question 1: What is the most used "channelGrouping" method? 

SQL Queries:
```
SELECT COUNT("channelGrouping"), "channelGrouping"
FROM all_sessions 
GROUP BY "channelGrouping" 
ORDER BY COUNT("channelGrouping")  DESC
```

Answer: 
The most used method for channel grouping is organic search 


Question 2: Which page title did customers spend their most time on?

SQL Queries:
```
SELECT MAX("time"), "pageTitle" 
FROM all_sessions
GROUP BY "pageTitle"
ORDER BY MAX("time") DESC
```
Answer: Customers spend most of their on on ""Men's Apparel | Google Merchandise Store"



Question 3: Which product is the most popular? 

SQL Queries:
```
SELECT * FROM "sales_report"
ORDER BY "total_ordered" DESC
```

Answer: The most popular product is ""Ballpoint LED Light Pen" which has a total order of 456. 



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
