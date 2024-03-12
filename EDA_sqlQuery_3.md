## Analysis 3: 
sqlQuery 3 – sqlQuery 3 – EXPLORATION: royalty_sales <br>
EXPLORATION: royalty_sales <br>

### Query
````sql
-- exploring royalty_sales table 
SELECT *
FROM royalty_sales ; -- 114,358

SELECT TOP 10 *
FROM royalty_sales  
-- findings: song_id have some null spaces, check for payable_curency consistency, album_id is also null 

-- next: how many nulls in song_id 
SELECT sale_id, count(*) as count 
FROM royalty_sales
WHERE song_id IS NULL 
GROUP BY sale_id;
-- the finding of that is 114,358 rows

-- I want to know how many song_id we have and I want to sort them alphabetically 
SELECT song_id, count(*) as count
FROM royalty_sales
GROUP BY song_id
ORDER BY count desc; 
-- with  ASC we have 53,766 song_id with null values (tho it still shows no nulls there). 
-- the highest amout of song_id is 16 

SELECT * 
FROM royalty_sales
WHERE song_id = '' ; 
-- so those have empty spaces and we have 53 766 of them. 

-- exploring date
SELECT sale_id, sale_date
FROM royalty_sales
ORDER BY sale_date  ;
--this way I see that the latest sale is 2022-05-31 and the oldest is from 2000-01-01

-- store: do we have null values there, thich is the most/least popular, how many of them is there
SELECT store, count(*) as count
FROM royalty_sales
GROUP BY store
ORDER BY count desc; 

--96 rows, it would mean we have 96 of them, let's check: 
SELECT count( DISTINCT store) as store
FROM royalty_sales ; 

-- it is 96 of them
--now let's check for the null values there
SELECT store
FROM royalty_sales
WHERE store IS NULL ; 
-- NO NULL VALUES  

--exploring currency
SELECT payable_currency, count(*) AS count
FROM royalty_sales
GROUP BY payable_currency
ORDER BY count desc;  -- 685 desc Nepalese Rupee, 684 asc Falkland Island Pounds

-- NOTE payable_amt_due is a amount payed in the currency, usd_payable is the amt that is payed in USD dollars
--after conversion 

-- move on to payable_amt_due to see the statistics 
SELECT 
	COUNT(*) AS num_rows,
	ROUND(AVG(payable_amt_due),2) AS avg_payable_amt_due,
	ROUND(MIN(payable_amt_due),2) AS min_payable_amt_due,
	ROUND(MAX(payable_amt_due),2) AS max_payable_amt_due,
	ROUND(SUM(payable_amt_due), 2) AS sum_payable_amt_due,
	ROUND(STDEV(payable_amt_due),2) AS stdev_payable_amt_due
FROM royalty_sales ; 

-- more info from here
SELECT 
	COUNT(*) AS num_rows,
	ROUND(AVG(usd_payable),2) AS avg_usd_payable,
	ROUND(MIN(usd_payable),2) AS min_usd_payable,
	ROUND(MAX(usd_payable),2) AS max_usd_payable,
	ROUND(SUM(usd_payable), 2) AS sum_usd_payable,
	ROUND(STDEV(usd_payable),2) AS stdev_usd_payable
FROM royalty_sales ; 

-- move on to quantity  to see the statistics 
SELECT 
	count(*) AS num_rows,
	ROUND(AVG(quantity),2) AS avg_quantity,
	ROUND(MIN(quantity),2) AS min_quantity,
	ROUND(MAX(quantity),2) AS max_quantity,
	ROUND(SUM(quantity), 2) AS sum_quantity,
	ROUND(STDEV(quantity),2) AS stdev_quantity
FROM royalty_sales ; 

````
</br>
