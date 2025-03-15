---
layout: post
title:  "Data Curation: The Economics of Fast Food Prices"
date: 2025-03-14
description: Is your Happy Meal overpriced? Let's find out. Read about the correlation between various state economic factors and fast food prices in the US-- and how you can curate similar data yourself! 

---
<p class="intro"><span class="dropcap">D</span>o you ever look at the rising cost of your Taco Bell combo, channel your inner grumpy old man, and wonder aloud, "Why is this so expensive? Back in my day, it was only $0.75." No? Yeah, me neither. However, it is an interesting question to ask: how are our favorite fast food items priced, and why do they change? Although there's probably an in-depth socio-economic answer, we can look at the recent economic data across each state and the respective food prices to better understand what might factor into those McCosts.

All jokes aside, though, there's a lot of value—for the average consumer as well as business owners—in knowing how to get the best product for your buck.
 </p>

### Motivating Question:
In all good data analysis and curation, there starts an in-depth and answerable question. A well-crafted question guides the analysis and defines the bounds of your research. The question I asked myself was this:

<b>How do state-level minimum wage, cost of living, median household income, and other factors impact the average price of a standard fast food meal across the U.S.?</b>

As you will see later in the data, each state has its own economic needs and capabilities, and their effects are seen in the fluctuating prices of chain restaurants. It's a concern with many elements, and (as we love to hear) best broken down through data analysis. As we go along, feel free to ponder how you might personalize this curation or apply it to your own sciency questions.

### Ethical Considerations and Data Collection Methods:
Before we go any further, it should be said that ethically gathered information is essential! In my analysis, I used public datasets found on an online database (<a href="https://worldpopulationreview.com/" target="_blank">DBeaver: World Population Review</a>) and on a financial services company's compiled data from the Forbes and the U.S. Census Bureau (<a href="https://www.sofi.com/learn/content/average-salary-in-us/" target="_blank">Average US Salary by State</a>). I collected the latter dataset through web scraping while adhering to website policies.

### Getting Started with Your Data:
After you have your data science question and are adhering to local data scraping policies and laws, you're ready to compile your data. You can do so using the following techniques:

* Public datasets (I used these)
* APIs
* Web scraping (this too)

(Note: There are other methods, but these are the simplest and more our pace.)

Also, be sure that your data has a common column or factor, such as 'state', to ensure the final dataset can merge using a similar index. You'll thank me later. After collecting my datasets, I merged them into one to better observe correlations. Feel free to have fun with it, just make sure your dataset is clean and labeled so you don't get lost in the sauce. Here is my merging code in case you need to compare. 

{%- highlight Python -%}
#combine all df into one on state
combined_df = medavgdf.merge(livingcostdf, on='state', how='outer') \
                      .merge(minwagedf, on='state', how='outer') \
                      .merge(gdpdf, on='state', how='outer') \
                      .merge(gdpgrowthdf, on='state', how='outer') \
                      .merge(unemploymentdf, on='state', how='outer') \
                      .merge(fastfooddf, on='state', how='outer')

combined_df = combined_df[combined_df['state'] != "District of Columbia"].rename(columns={"Average": "AverageIncome", "Median": "MedianIncome"})
combined_df = combined_df.sort_values(by='state').reset_index(drop=True)
combined_df.to_csv('fast_food_analysis.csv', index=False)
combined_df
{%- endhighlight -%}

### EDA Highlights:
Okay! Now that your datatable is set up and your IDE is running, we can start to query the data. Each SQL query has a few elements we want to keep in mind. The only two required elements are SELECT and FROM, as without these, your code won't know what to grab and from where (respectively).  


#### Interesting Findings

### 

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