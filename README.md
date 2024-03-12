# Music Royalty Insights Exploratory-Data-Analysis in SSMS

I appreciate all ⭐ 
Thank you 💙

**Author**: Mal Sikora <br />
**Email**: sikoramald@gmail.com <br />
**Website**: https://malsprojects.wixsite.com/my-site  <br />
**LinkedIn**: https://www.linkedin.com/in/mal-sikora/  <br />

## Introduction
An examination of a Music Royalty database through SQL analysis. </br>

ℹ️ **_Note_** </br>
Used: SQL Server (SSMS) </br>
SQL language: T-SQL </br>

**Exploratory Data Analysis:**
* [sqlQuery 1 – CHECKING DATA TYPES](/EDA_sqlQuery_1.md)<br>
* [sqlQuery 2 – CHECKING FOR NULL VALUES AND EXPLORE UNIQUENESS & KEYS](EDA_sqlQuery_2.md) <br>
* [sqlQuery 3 – EXPLORATION: royalty_sales](EDA_sqlQuery_3.md)<br>
* [sqlQuery 4 – EXPLORATION: albums](EDA_sqlQuery_4.md) <br>
* [sqlQuery 5 – EXPLORATION: artists & songs](EDA_sqlQuery_5.md) <br>
* [sqlQuery 6 – FULL STACK](EDA_sqlQuery_6.md)
   <br>
## Datasets files
This case study uses: 

### Table: royalty_sales
| Column            | Data Type         | Constraints  | Nullable |
|-------------------|-------------------|--------------|----------|
| sale_id           | bigint            | PK, not null |          |
| sale_date         | date              |              | null     |
| store             | varchar(50)       |              | null     |
| album_id          | varchar(50)       |              | null     |
| song_id           | varchar(50)       |              | null     |
| quantity          | bigint            |              | null     |
| payable_currency  | varchar(50)       |              | null     |
| payable_amt_due   | real              |              | null     |
| exchange_rate     | real              |              | null     |
| usd_payable       | real              |              | null     |

### Table: songs
| Column      | Data Type       | Constraints  | Nullable |
|-------------|-----------------|--------------|----------|
| song_id     | nvarchar(50)    | PK, not null |          |
| song_title  | nvarchar(100)   |              | not null |
| album_id    | int             | PK, not null |          |

### Table: albums
| Column         | Data Type  | Constraints  | Nullable |
|----------------|------------|--------------|----------|
| album_id       | int        | PK, not null |          |
| artist_id      | int        |              | not null |
| album_title    | nvarchar(100) |           | not null |
| genre          | nvarchar(50) |             | not null |
| release_date   | date       |              | not null |
| num_of_tracks  | tinyint     |              | not null |
| type           | nvarchar(50) |             | not null |
| royalty_share  | float      |              | not null |

### Table: artists
| Column        | Data Type   | Constraints  | Nullable |
|---------------|-------------|--------------|----------|
| album_id      | int         | PK, not null |          |
| real_name     | nvarchar(100) |            | not null |
| artist_name   | nvarchar(200) |            | null     |
| role          | nvarchar(100) |            | not null |
| country       | nvarchar(100) |            | not null |
| city          | nvarchar(100) |            | not null |
| email         | nvarchar(200) |            | not null |
| zip_code      | nvarchar(50)  |            | not null |

<br>

## Exploratory Data Analysis (EDA)
1.	Check Data Types <br>
•	Examining if data types in each column is appropriate and consistent with data they store. <br>

2.	Checking for Null Values and Explore Uniqueness & Keys<br>
•	Examining each table for null values, especially in crucial columns. Deciding whether nulls are allowed and handle them appropriately.<br>
•	Understand the uniqueness of values in key columns like song_id, album_id, and others. Ensure the uniqueness constraints are met.<br>

3.	Distribution of Quantitative Data<br>
•	Exploring: royalty_sales, albums, artists, songs<br>
•	Investigating the distribution of quantitative data like quantity, payable_amt_due, and royalty_share. Use summary statistics and visualizations.<br>

4.	Full Stack <br>
•	Answering questions about the data. <br><br>


<!-- Used [datasets](./source_data/csv/) for this case study
- <strong> </strong>: amazon_2024_valentines_best_sellers.csv  -->

