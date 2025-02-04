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
* defining key elements of SQL and SQL queries
* setting up a simple dataset in your IDE of choice
* practicing helpful SQL fuctionsf for data query

Good Luck!!

### Definitions:
| SQL clause | What it does                                                                                                                                 | Required                       |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------|
| SELECT     | Lists the fields that contain data of interest.                                                                                              | Yes                            |
| FROM       | Lists the tables that contain the fields listed in the SELECT clause.                                                                        | Yes                            |
| WHERE      | Specifies field criteria that must be met by each record to be included in the results.                                                      | No                             |
| ORDER BY   | Specifies how to sort the results.                                                                                                           | No                             |
| GROUP BY   | In a SQL statement that contains aggregate functions, lists fields that are not summarized in the SELECT clause.                             | Only if there  are such fields |
| HAVING     | In a SQL statement that contains aggregate functions, specifies conditions that apply to fields that are summarized in the SELECT statement. | No                             |


## Definition List
<dl>
  <dt>Coffee</dt>
  <dd>Black hot drink</dd>
  <dt>Milk</dt>
  <dd>White cold drink</dd>
</dl>

## Table

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
| Header      | Title       |
| Paragraph   | Text        |

## Code Snippet

{%- highlight SQL -%}
SELECT *
FROM World
WHERE "Someone"
LIKE "%You%"
...
/>no results
{%- endhighlight -%}


## Figure with Caption

<figure>
	<img src="{{site.url}}/{{site.baseurl}}/assets/img/touring.jpg" alt=""> 
	<figcaption>Figure 1. - This is an example figcaption</figcaption>
</figure>


{%- highlight html -%}
<figure>
	{% raw %}<img src="{{site.url}}/{{site.baseurl}}/assets/img/touring.jpg" alt="">{% endraw %}
	<figcaption>Figure 1. - This is an example figcaption</figcaption>
</figure>
{%- endhighlight -%}

