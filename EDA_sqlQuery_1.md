# Exploratory Data Analysis (EDA)
**Music Royalty Insights** </br>
**Author**: Mal Sikora <br />

## Analysis 1: 
sqlQuery 1 – CHECKING DATA TYPES <br>
CHECKING FOR NULL VALUES AND EXPLORE UNIQUENESS & KEYS

### Query
````sql 
-- quering dbo.songs for reference
EXEC sp_help 'songs'

-- checking for duplicates in dbo.songs
SELECT song_id, COUNT (*) AS count
FROM songs
GROUP BY song_id
HAVING COUNT(*) > 1;

-- no record with this combination shows that each row is unique
SELECT song_id, song_title, album_id, COUNT(*) AS count
FROM songs
GROUP BY song_id, song_title, album_id
HAVING COUNT(*) > 1;

--example of duplicate
SELECT *
FROM dbo.songs
where song_id = 'SOALSZJ1370F1A7C75'

-- let's check for duplicates for albums
SELECT album_id, COUNT (*) AS count
FROM albums
GROUP BY album_id
HAVING COUNT(*) > 1;
-- being empty - no results - means that I can establish primary key here 

-- for dbo.artists 
SELECT artist_id, COUNT (*) AS count
FROM artists
GROUP BY artist_id
HAVING COUNT(*) > 1;
--empty again so I can make it a primary key 

-- making PK in songs table 
ALTER TABLE songs
ADD CONSTRAINT PK_songs_album_id_song_id PRIMARY KEY (album_id, song_id);

-- droping album_id from royalties because it can be queried with song_id and it is empty anyways
ALTER TABLE royalty_sales
DROP COLUMN album_id;

--changing in royalties_sale date_sale for just date
ALTER TABLE royalty_sales
ALTER COLUMN sale_date DATE;

-- creating FK
ALTER TABLE albums
ADD CONSTRAINT FK_albums_artist_id
FOREIGN KEY (artist_id)
REFERENCES artists (artist_id);

--populate album_id in royalties_sales 
UPDATE rs
SET rs.album_id = s.album_id
FROM royalty_sales rs
INNER JOIN songs s ON rs.song_id = s.song_id
WHERE rs.album_id IS NULL;

--is it unique? 
SELECT sale_id, COUNT (*) AS count
FROM royalty_sales
GROUP BY sale_id
HAVING COUNT(*) > 1;

-- Alter the column to be NOT NULL
ALTER TABLE royalty_sales
ALTER COLUMN sale_id [int] NOT NULL;

-- Add the primary key constraint
ALTER TABLE royalty_sales
ADD CONSTRAINT PK_royalty_sales PRIMARY KEY (sale_id);

--final check 
SELECT *
FROM royalty_sales
WHERE sale_id IS NULL;

````
</br>


