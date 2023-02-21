What issues will you address by cleaning the data?
- FIRST STEP : remove irrelavant data (no values)
- Deleted "searchKeyword" column 
- Deleted "eCommerceAction_type" column 
- Deleted "itemQuantity" column
- Deleted "itemRevenue" column

 - SECOND STEP : remove duplicate data
 - Deleted "fullVisitorID" duplicates (no values across the entire row)

Queries:
Below, provide the SQL queries you used to clean your data.
```
SELECT * FROM all_sessions 
WHERE "searchKeyword" IS NULL 

DELETE FROM all_sessions
DROP COLUMN "searchKeyword"  
```
- Repeated the above steps for column "eCommerceAction_type", "itemQuantity", "itemReveue", "userid" 

```
SELECT * FROM all_sessions 
WHERE ("fullVisitorId" IS NULL AND "channelGrouping IS NULL)

DELETE FROM all_sessions 
WHERE ("fullVisitorId" IS NULL AND "channelGrouping IS NULL)
```
-updated the data type on column "unit_price" FROM "NUMERIC" to "REAL to remove trailing zeros

```
SELECT * FROM analytics

ALTER TABLE analytics
ALTER COLUMN "unit_price" TYPE REAL;
```

-divide "productPrice" column by "1000000" in table "all_sessions"

```
UPDATE all_sessions
SET "productPrice =  "productPrice" / 1000000.0
```