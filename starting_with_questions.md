ALTER TABLE "all_sessions" RENAME TO all_sessions;Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
SELECT 
		"city",
	MAX("transactionRevenue") AS Highest
FROM all_sessions 
GROUP BY "city", "transactionRevenue"
ORDER BY("transactionRevenue") 

SELECT 
		"country",
	MAX("transactionRevenue") AS Highest
FROM all_sessions 
GROUP BY "country", "transactionRevenue"
ORDER BY("transactionRevenue") 


Answer:
- The city that has the highest level of transaction revenue is "Sunnyvale" 

- The country that has the highest level of transaction revenue is "United States"





**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
```
SELECT "city",floor(AVG("total_ordered"))
FROM all_sessions AS a1
JOIN sales_by_sku ON "a1"."productSKU" = "sales_by_sku"."productSKU"
WHERE "total_ordered" <> 0
GROUP BY "city"
ORDER BY "city" 
```
```
SELECT "country",floor(AVG("total_ordered"))
FROM all_sessions AS a1
JOIN sales_by_sku ON "a1"."productSKU" = "sales_by_sku"."productSKU"
WHERE "total_ordered" <> 0
GROUP BY "country"
ORDER BY "country" 
```


Answer: 
- Starting with Saudi Arabia wich has the highest number of average product ordered of 134. Kuwait has 114, Hondura has 112...etc 

- For cities, it is Riyadh from Saudi Arabia 319, Brno from Czeh Republic 319, Rexburg from United States 250...etc 





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
```
SELECT "country","v2ProductCategory" , COUNT(*)
FROM all_sessions
GROUP BY "v2ProductCategory" ,"country"
ORDER BY "country" DESC
```



Answer:
- When I order by "country" I recognize there is a pattern between "Home/Apparel/Men's/Men's-T-Shirts/ AND Home/Shop by Brand/YouTube/ for every country. These two categories' numbers are the highest amongst all other categories. A lot of countries are purchasing Men's T-shirts and I'm assuming Youtube is one of the most effective channel for advertising. 




**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
```
SELECT "country","v2ProductName" , COUNT(*)
FROM all_sessions
GROUP BY "v2ProductName","country"
ORDER BY COUNT(*) DESC
```



Answer:
- The top selling product is ""Google Men's 100% Cotton Short Sleeve Hero Tee White". Nearly most of the top selling products are purchased by the United States. 





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:
```
SELECT "country" ,"totalTransactionRevenue"
FROM all_sessions
WHERE "totalTransactionRevenue" IS NOT NULL
ORDER BY "totalTransactionRevenue" DESC
```



Answer:
- According to the above query, only four countries generated total transaction revenue: United States, Israel, Asutralia, Canada and Switzerland while United States contributed the most (above 90%). We can summarize that US generated the most impact of revenue and Switzerland the least. 







