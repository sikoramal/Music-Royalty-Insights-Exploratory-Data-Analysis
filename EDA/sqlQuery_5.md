## Analysis 5: 
sqlQuery 5 – EXPLORATION: artists & songs   <br>
EXPLORATION: songs & artists <br>

### Query
````sql
SELECT TOP 10 *
FROM artists ; 

SELECT TOP 10 *
FROM songs ; 

SELECT real_name, artist_name, role,   count(*) as count
FROM artists 
GROUP BY  real_name, artist_name, role
HAVING count(*) > 1 ; -- the are doubles 

SELECT *
FROM artists
WHERE real_name = 'Price Cummings'
-- two different artist_id so assume they are not the same person 

SELECT *
FROM artists
GROUP BY artist_id, real_name, artist_name, role, country, city, email, zip_code
HAVING COUNT(*) > 1;
-- comes up empty, definetly no doubles  

SELECT country, count(*) as count
FROM artists
GROUP BY country
ORDER BY count asc ;  -- Tanzania for the win, British Virgin Islands the lowest 


-- for songs I wanna check for duplicates across

SELECT * 
FROM songs
GROUP BY song_id, song_title, album_id
HAVING count(song_title) > 1 ;  -- no doubles

--how many songs we have in the table? 
SELECT count(*) as count
FROM songs ; -- 7574

````
</br>
