---
layout: post
title:  "Visualizing Using Streamlit: The Price of a Bite"
date: 2025-04-11
description: Is there a cross-country road trip in your future? Maybe pack a lunch. This blog tackles key insights relating to how economic factors like minimum wage, cost of living, and household income influence the price of a standard meal. Look for the interactive Streamlit app for deeper exploration, and unpack what fast food prices reveal about broader regional economics.

---
<p class="intro"><span class="dropcap">W</span>
ith all the economic uncertainty as of late, we're all asking ourselves the same question: <i>Can I still afford Chick-fil-A?</i> It turns out there are several factors that influence the rising prices of our favorite fast food items—factors that vary across regions and all 50 states. As for whether you can still afford that frosted lemonade..? Well, you might need to run your own analysis.</p>

<p>
Using those handy-dandy data curation abilities, I put together a dataset with key economic factors and various fast food items. Although we might have our own guesses and hypotheses for why things happen, truly understanding the world around us requires some good ol' data manipulation and quality EDA.
 </p>

### Motivation:
The motivating question I used to guide my curation and EDA was this:

<b>How do state-level minimum wage, cost of living, median household income, and other factors impact the average price of a standard fast food meal across the U.S.?</b>

### Highlights:

### Streamlit App:
#### Purpose:
Post clearly explains the app’s purpose, aligning it with the dataset and audience, and effectively describes its features and value for exploring the data.

#### Features:
Post provides a detailed and engaging description of the app’s features, visualizations, and interactivity, including specific examples of how users can explore the data and gain insights.	

* overall
* region
* state vs food vs factor
* factor vs food

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
And now, the moment we've all been waiting for: EDA! Using basic Python, I was able to create a matrix object and find the average correlations among all the states for each column.  

<dl>
  <dt>Dataset Overview</dt>
  <dd>My data contained 50 rows and 13 columns. All 50 states were included, along with 7 economic factors: average income, median income, cost of living, minimum wage, GDP, GDP growth, and unemployment rate. The five fast food restaurant items included a Domino's medium cheese pizza, a McDonald's Happy Meal and Big Mac, Chick-fil-A sandwich, and Taco Bell combo.
  </dd>
  <dt>High Correlations</dt>
  <dd>1. Chick-fil-A Chicken Sandwich & Taco Bell Combo Meal (0.992)</dd>
  <dd>These two variables are highly correlated, meaning that in states where the price of one is higher, the price of the other tends to be similarly high. This suggests that the prices of fast food items from different chains (Chick-fil-A and Taco Bell) move together.</dd>
   <dd>2. McDonald's Big Mac & Chick-fil-A Chicken Sandwich (0.968)</dd>
   <dd>Similarly, the Big Mac and Chick-fil-A Chicken Sandwich also have a very strong positive correlation, indicating that the prices of these two fast food items are closely aligned across states.</dd>
  <dt>Moderate Correlations</dt>
  <dd>1. Cost of Living & McDonald's Big Mac (0.782)</dd>
  <dd>Cost of living is moderately correlated with the price of a Big Mac, which suggests that states with a higher cost of living tend to also have more expensive fast food" → "Cost of living is moderately correlated with the price of a Big Mac, which suggests that states with a higher cost of living also tend to have more expensive fast food.</dd>
  <dt>Low or No Correlation</dt>
  <dd>1. Unemployment Rate & Fast Food Prices</dd>
  <dd>The unemployment rate has weak correlations with fast food prices. For instance, the correlation with McDonald's Big Mac (0.238) and Chick-fil-A Chicken Sandwich (0.217) are not very high" → "The unemployment rate has weak correlations with fast food prices. For instance, the correlation with a McDonald's Big Mac (0.238) and a Chick-fil-A Chicken Sandwich (0.217) is not very high.</dd>
  <dt>Interesting Observations</dt>
  <dd> Cost of Living has strong correlations with fast food prices (e.g., Chick-fil-A Chicken Sandwich: 0.816), which aligns with the idea that higher living costs often lead to higher prices across goods and services, including food.</dd>
  <dd>Minimum Wage correlates moderately with fast food prices (e.g., McDonald's Big Mac: 0.626), indicating that higher wages may lead to higher fast food prices, possibly due to higher labor costs in states with higher minimum wages.</dd>
  <dt>Visualization: Heatmap</dt>
  <img src="{{site.url}}/{{site.baseurl}}/assets/img/correlation_between_economic_factors_and_restaurant_prices.png" alt="welppp"/>
  <dd> To best understand this visualization, look at the top-right or bottom-left corners. In these areas, one can observe how these economic factors relate to our fast food of choice. It looks like economics really does play a role in the price of our french fries. 😭</dd>
</dl>

### Conclusion:
Post includes a summary or conclusion with a question or challenge to encourage comments	


<a href="https://github.com/gbean4/blog3_streamlit.git" target="_blank">GitHub Repository</a>

<a href="https://www.youtube.com/watch?v=d7fnzDQ5qM8" target="_blank">Streamlit Crash Course: From Zero to Data App</a>