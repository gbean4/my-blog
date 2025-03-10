---
layout: post
title:  "Unlock the Power of Data: An Easy Introduction to SQL"
date:   2025-02-04
description: This post is designed to define basic SQL functions and guide you through your first SQL query as you enter the world of data science.  

---

<p class="intro"><span class="dropcap">T</span>here I was, Fall 2022, sitting in a large lecture hall in the basement of the Utah State business college. Unsure of my life’s path and my career opportunities, I was a hesitant bioengineering major in a random data science class, just trying to make it work—when suddenly my world was changed. Changed by what, you may ask? The beauty of SQL. </p>

### Introduction:
To put it simply, SQL (or Structured Query Language) is a programming language used for storing and processing information in a relational database. It’s exceptionally helpful in pulling and processing large amounts of data, even pieces of related data, for your use and interpretation. Luckily for us, it's easy to learn and use to answer all of our deepest data science questions. 

We'll start by:
* setting up a simple dataset in your IDE of choice
* defining key elements of SQL and SQL queries
* practicing helpful SQL fuctions for data analysis

### Set Up:
There are many IDE options for your use! Most are user friendly and allows you to query what you need. Some options include:
* MySQL
* DBeaver (I use this IDE in the code below)
* PostgreSQL
* SQLite
* or an online SQL sandbox (like DB Fiddle)

If you're new to setting up IDE's and coding environments, use this video for step by step support!

<a href="https://www.youtube.com/watch?v=FWPMtHEYdFA" target="_blank">DBeaver: Setting up an Easy-to-Use SQL Editor for Data Management</a>

Once you have your SQL environment open, paste the following code and run! This code initializes your database and will allow you to practice with the examples as we go along. 
{%- highlight SQL -%}
CREATE TABLE Movies (
    MovieID INT PRIMARY KEY,
    Title VARCHAR(100),
    Genre VARCHAR(50),
    ReleaseYear INT,
    Director VARCHAR(100),
    IMDbRating DECIMAL(2,1),
    BoxOfficeRevenue DECIMAL(15,2)); 

INSERT INTO Movies (MovieID, Title, Genre, ReleaseYear, Director, IMDbRating, BoxOfficeRevenue)
VALUES
(1, 'The Shawshank Redemption', 'Drama', 1994, 'Frank Darabont', 9.3, 28341469),
(2, 'The Godfather', 'Crime', 1972, 'Francis Ford Coppola', 9.2, 246120974),
(3, 'The Dark Knight', 'Action', 2008, 'Christopher Nolan', 9.0, 1004558444),
(4, 'Pulp Fiction', 'Crime', 1994, 'Quentin Tarantino', 8.9, 213928762),
(5, 'Forrest Gump', 'Drama', 1994, 'Robert Zemeckis', 8.8, 678226466),
(6, 'Inception', 'Sci-Fi', 2010, 'Christopher Nolan', 8.8, 836848102),
(7, 'The Matrix', 'Sci-Fi', 1999, 'Lana Wachowski, Lilly Wachowski', 8.7, 467222728),
(8, 'The Lord of the Rings: The Return of the King', 'Fantasy', 2003, 'Peter Jackson', 9.0, 1146030912),
(9, 'Interstellar', 'Sci-Fi', 2014, 'Christopher Nolan', 8.7, 773439417),
(10, 'Gladiator', 'Action', 2000, 'Ridley Scott', 8.5, 460583960),
(11, 'The Lion King', 'Animation', 1994, 'Roger Allers, Rob Minkoff', 8.5, 968511805),
(12, 'Titanic', 'Romance', 1997, 'James Cameron', 7.9, 2264550681),
(13, 'Saving Private Ryan', 'War', 1998, 'Steven Spielberg', 8.6, 482349603),
(14, 'The Silence of the Lambs', 'Thriller', 1991, 'Jonathan Demme', 8.6, 272742922),
(15, 'Avatar', 'Sci-Fi', 2009, 'James Cameron', 7.9, 2924000000);
{%- endhighlight -%}

##### Code Explanation:
If the code above confuses you, no worries! I got you. SQL's purpose is data retrieval, manipulation, and management. This means you'll start all your queries either initializing a database and inserting values or retrieving a database from some other source. The CREATE TABLE function initializes your table (called 'Movies') with keys, or column names. 'MovieID' is considered the PRIMARY KEY (meaning the special name given to each record) because each row will have a unique value.
The second function (starting with INSERT INTO) creates records and inserts them into the 'Movies' table we just created.

### Definitions:
Okay! Now that your datatable is set up and your IDE is running, we can start to query the data. Each SQL query has a few elements we want to keep in mind. The only two required elements are SELECT and FROM, as without these, your code won't know what to grab and from where (respectively).  

<dl>
  <dt>SELECT (Required)</dt>
  <dd>Lists the fields that contain data of interest
  </dd>
  <dt>FROM (Required)</dt>
  <dd>Lists the tables that contain the fields listed in the SELECT clause.</dd>
  <dt>WHERE</dt>
  <dd>Specifies field criteria that must be met by each record to be included in the results.</dd>
  <dt>ORDER BY</dt>
  <dd>Specifies how to sort the results.</dd>
  <dt>GROUP BY</dt>
  <dd> Lists fields that are not summarized in the SELECT clause.</dd>
  <dt>HAVING</dt>
  <dd>Specifies conditions that apply to fields that are summarized in the SELECT statement.</dd>
</dl>

For example, if you wanted to query all your data to view in one table, you could use the following code:
{%- highlight SQL -%}
SELECT *
FROM Movies; #all SQL queries end with ';'
{%- endhighlight -%}
If you run this in your IDE, you will see the something like this:

<img src="{{site.url}}/{{site.baseurl}}/assets/img/Screenshot3.jpg" alt="welppp"/>

### Practice
Yay! This is great. Your SQL environment is running as it should and your database is ready for further queries. 

An important part of SQL programming is asking the right questions. With all that data, it pays to know what you're looking for and what patterns you're trying to observe. 

Let's say you want to see all records categorized as "Sci-Fi" in the column "Genre". Let's also say you want to organize it by "BoxOfficeRevenue" from least to greatest revenues because you only watch indie films. We can do that! (Look back at the definitions if you need a hint.)

{%- highlight SQL -%}
SELECT *
FROM Movies 
WHERE Genre = "Sci-Fi"
ORDER BY BoxOfficeRevenue ASC;
{%- endhighlight -%}
<figure>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/Screenshot4.jpg" alt="welppp"/>
<figcaption>Using WHERE and ORDER BY allows us to select specific records based on a condition and organize them by our chosen parameter. As a bonus, the ASC indicates we want ascending order, least to greatest!</figcaption>
</figure>

Alright, you're an expert. What if we want to find some aggregated values, such as a SUM, MEAN, or MAX? These aggregated functions are performed in the SELECT clause and can even be renamed according to the aggregation they represent. This is where GROUP BY and HAVING come into play. GROUP BY allows us to group our data based on the keys not used in the SELECT aggregation functions, while HAVING basically acts as a WHERE clause for fields in GROUP BY. 

The code below uses both GROUP BY and HAVING in querying the data. Look over the code and see if you can guess the shape and set up of the resulting table. 
{%- highlight SQL -%}
SELECT Genre, SUM(BoxOfficeRevenue) AS TotalRevenue 
FROM Movies
GROUP BY Genre
HAVING IMDbRating > 8;
{%- endhighlight -%}
<figure>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/Screenshot5.jpg" alt="welppp"/>
<figcaption>The above code sums up revenues based on the genre, as well as only showing records with a rating above 8/10. How cool!!</figcaption>
</figure>

### Conclusion
Although SQL is simple for coders experienced in other languages, it is essential for working with structured data stored in relational databases, as we experimented with earlier. As you progress in your data science journey, look to SQL for data access and retrieval as you filter and manipulate your data. Further learning will teach you how to clean and preprocess unprepared data while being able to handle millions of records efficiently. As a final note, it's also very very fun. 

Now that you've been introduced to SQL and have had some practice, keep playing with your data, add more records, or create your own tables! If you are interested in learning more advanced functions, prioritizing your results, or using fragmanted datatables pieced together, look to the links below! 

<a href="https://www.geeksforgeeks.org/sql-advanced-functions/" target="_blank">Advanced Functions</a>

<a href="https://www.geeksforgeeks.org/rank-function-in-sql-server/" target="_blank">RANK() Function in SQL Server</a>

<a href="https://www.geeksforgeeks.org/sql-join-set-1-inner-left-right-and-full-joins/" target="_blank">SQL Joins (Inner, Left, Right and Full Join)</a>

Happy coding!

#### And Remember:
{%- highlight SQL -%}
SELECT *
FROM World
WHERE "Someone"
LIKE "%You%";
...
/>no results
{%- endhighlight -%}
Meaning: when querying the World, there's only 1 result like you ;)