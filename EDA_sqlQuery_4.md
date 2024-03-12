## Analysis 4: 
sqlQuery 4 – EXPLORATION: albums  <br>
EXPLORATION: albums <br>

### Query
````sql
SELECT TOP 10 *
FROM albums ; 

-- any null values? 
SELECT *
FROM albums
WHERE album_title IS NULL ; 

-- no null values - note: joining as inner join due to this table having all info 

-- checking the distribiution of genres in albums table 
SELECT TOP 5 genre, count(*) as count
FROM  albums
GROUP BY genre 
ORDER BY count desc ; 
-- Indie, Pop, Rap, Pop-Rock, Punk are the top five. with ASC the least amt of count is Ambiend, Folk
-- and Unpluged

SELECT count(*) as count
FROM albums; -- 748 


SELECT album_id, release_date
FROM albums
ORDER BY release_date desc ; -- 1970-01-01 to 2023-03-06

-- which album has the most tracks 
SELECT album_id, num_of_tracks
FROM albums
ORDER BY num_of_tracks desc ; -- 15 is the most

SELECT avg(num_of_tracks) as avg 
FROM albums -- 8 avg per album 

-- statistics for royalty_share 
SELECT 
	count(*) AS num_rows,
	ROUND(AVG(royalty_share),2) AS avg_royalty_share,
	ROUND(MIN(royalty_share),2) AS min_royalty_share,
	ROUND(MAX(royalty_share),2) AS max_royalty_share,
	ROUND(SUM(royalty_share), 2) AS sum_qroyalty_share,
	ROUND(STDEV(royalty_share),2) AS stdev_royalty_share
FROM albums ; 


````
</br>
