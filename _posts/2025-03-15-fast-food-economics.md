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

<figure>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/bigmac.jpg" alt="welppp"/>
<figcaption>McDonald's Big Mac for reference. Made by Ronald himself.</figcaption>
</figure>

### Ethical Considerations and Data Collection Methods:
Before we go any further, it should be said that ethically gathered information is essential! In my analysis, I used public datasets found on an online database (<a href="https://worldpopulationreview.com/" target="_blank">DBeaver: World Population Review</a>) and on a financial services company's compiled data from the Forbes and the U.S. Census Bureau (<a href="https://www.sofi.com/learn/content/average-salary-in-us/" target="_blank">Average US Salary by State</a>). I collected the latter dataset through web scraping while adhering to website policies.

### Getting Started with Your Data:
After you have your data science question and are adhering to local data scraping policies and laws, you're ready to compile your data. You can do so using the following techniques:

* Public datasets (I used these)
* APIs
* Web scraping (this too)

(Note: There are other methods, but these are the simplest and more our pace.)

Also, be sure that your data has a common column or factor, such as 'state', to ensure the final dataset can merge using a similar index. You'll thank me later. After collecting my datasets, I merged them into one to better observe correlations. Feel free to have fun with it, just make sure your dataset is clean and labeled so you don't get lost in the sauce. Here is my merging code in case you need to compare. 

{%- highlight python -%}
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

### Exploratory Data Analysis Highlights:
And now, the moment we've all been waiting for: EDA! 
####

<dl>
  <dt>Dataset Overview</dt>
  <dd>My data was 50 rows by 13 columns. All 50 states were included, along with 7 economic factors: average income, median income, cost of living, minimum wage, GDP, GDP growth, and unemployment rate. The 5 fast food restaurant items were a Dominos medium cheese pizza, a McDonald's Happy Meal and Big Mac, Chick-fil-a sandwich, and Taco Bell combo.
  </dd>
  <dt>High Correlations</dt>
  <dd>1. Chick-fil-A Chicken Sandwich & Taco Bell Combo Meal (0.992)</dd>
  <dd>These two variables are highly correlated, meaning that in states where the price of one is higher, the price of the other tends to be similarly high. This suggests that the prices of fast food items from different chains (Chick-fil-A and Taco Bell) move together.</dd>
   <dd>2. McDonald's Big Mac & Chick-fil-A Chicken Sandwich (0.968)</dd>
   <dd>Similarly, the Big Mac and Chick-fil-A Chicken Sandwich also have a very strong positive correlation, indicating that the prices of these two fast food items are closely aligned across states.</dd>
  <dt>Moderate Correlations</dt>
  <dd>1. Cost of Living & McDonald's Big Mac (0.782)</dd>
  <dd>Cost of living is moderately correlated with the price of a Big Mac, which suggests that states with a higher cost of living tend to also have more expensive fast food, possibly due to higher labor costs and other factors.</dd>
  <dt>Low or No Correlation</dt>
  <dd>1. Unemployment Rate & Fast Food Prices</dd>
  <dd>The unemployment rate has weak correlations with fast food prices. For instance, the correlation with McDonald's Big Mac (0.238) and Chick-fil-A Chicken Sandwich (0.217) are not very high, suggesting that unemployment may not directly drive fast food prices in a state.</dd>
  <dt>Interesting Observations</dt>
  <dd> Cost of Living has strong correlations with fast food prices (e.g., Chick-fil-A Chicken Sandwich: 0.816), which aligns with the idea that higher living costs often lead to higher prices across goods and services, including food.</dd>
  <dd>Minimum Wage correlates moderately with fast food prices (e.g., McDonald's Big Mac: 0.626), indicating that higher wages may lead to higher fast food prices, possibly due to higher labor costs in states with higher minimum wages.</dd>
</dl>


<img src="{{site.url}}/{{site.baseurl}}/assets/img/correlation_between_economic_factors_and_restaurant_prices.png" alt="welppp"/>



### Conclusion and Next Steps:



<a href="https://github.com/gbean4/Post_2" target="_blank">GitHub Repository</a>

<a href="https://www.sofi.com/learn/content/average-salary-in-us/" target="_blank">Average US Salary by State</a>


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


<figure>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/Screenshot5.jpg" alt="welppp"/>
<figcaption>The above code sums up revenues based on the genre, as well as only showing records with a rating above 8/10. How cool!!</figcaption>
</figure>