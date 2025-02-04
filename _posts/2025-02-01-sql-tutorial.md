---
layout: post
title:  "Unlock the Power of Data: An Easy Introduction to SQL"
date:   2025-02-04
description: This post is designed to help define basic SQL functions and guide you through your first SQL query as you enter the world of data science. You got this!!! 

---

<p class="intro"><span class="dropcap">T</span>here I was, Fall 2022, sitting in a large lecture hall in the basement of the Utah State business college. Unsure of my life’s path and my career opportunities, I was a hesitant bioengineering major in a random data science class, just trying to make it work—when suddenly my world was changed. Changed by what, you may ask? The beauty of SQL. </p>


### Introduction:
To put it simply, SQL (or Structured Query Language) is a programming language used for storing and processing information in a relational database. It’s exceptionally helpful in pulling and processing large amounts of data, even pieces of related data, for your use and interpretation. Lucky for us newbies, it's also easy to learn and immediately use to answer all of our deepest data science questions. 

We'll start by:
* setting up a simple dataset in your IDE of choice
* defining key elements of SQL and SQL queries
* practicing helpful SQL fuctions for data query

Good Luck!!

### Set Up:
There are many IDE options for your use! Most are user friendly and will allow you to query what is needed. Some options include:
* MySQL
* DBeaver
* PostgreSQL
* SQLite
* or an online SQL sandbox (like DB Fiddle)
Once you have your SQL environment open, paste the following code and run! This code initializes your database and will allow you to practice along with the examples provided. 
{%- highlight SQL -%}
CREATE TABLE Movies (
    MovieID INT PRIMARY KEY,
    Title VARCHAR(100),
    Genre VARCHAR(50),
    ReleaseYear INT,
    Director VARCHAR(100),
    IMDbRating DECIMAL(2,1),
    BoxOfficeRevenue DECIMAL(15,2)
);

INSERT INTO Movies (MovieID, Title, Genre, ReleaseYear, Director, IMDbRating, BoxOfficeRevenue)
VALUES
(1, 'The Shawshank Redemption', 'Drama', 1994, 'Frank Darabont', 9.3, 28341469),
(2, 'The Godfather', 'Crime', 1972, 'Francis Ford Coppola', 9.2, 246120974),
(3, 'The Dark Knight', 'Action', 2008, 'Christopher Nolan', 9.0, 1004558444);
{%- endhighlight -%}

### Definitions:
If the code above confuses you, no worries! I got you. SQL's purpose is for data retrieval, manipulation, and management. This means you'll start all your queries either initializing a database and inserting values or retrieving a database from some other source. 
<dl>
  <dt>SELECT</dt>
  <dd>Lists the fields that contain data of interest.</dd>
  <dt>FROM</dt>
  <dd>Lists the tables that contain the fields listed in the SELECT clause.</dd>
  <dt>WHERE</dt>
  <dd>Specifies field criteria that must be met by each record to be included in the results.</dd>
  <dt>ORDER BY</dt>
  <dd>Specifies how to sort the results.</dd>
  <dt>GROUP BY</dt>
  <dd>In a SQL statement that contains aggregate functions, lists fields that are not summarized in the SELECT clause.</dd>
  <dt>HAVING</dt>
  <dd>In a SQL statement that contains aggregate functions, specifies conditions that apply to fields that are summarized in the SELECT statement.</dd>
</dl>


##### And Remember:

{%- highlight SQL -%}
SELECT *
FROM World
WHERE "Someone"
LIKE "%You%"
...
/>no results
{%- endhighlight -%}