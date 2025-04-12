---
layout: post
title:  "Visualizing Using Streamlit: The Price of a Bite"
date: 2025-04-11
description: Is there a cross-country road trip in your future? Maybe pack a lunch. This blog tackles key insights relating to how economic factors like minimum wage, cost of living, and household income influence the price of a standard meal. Look for the interactive Streamlit app for deeper exploration, and unpack what fast food prices reveal about broader regional economics.

---
<p class="intro"><span class="dropcap">W</span>
ith all the economic uncertainty as of late, we're all asking ourselves the same question: <i>Can I still afford Chick-fil-A?</i> It turns out there are several factors that influence the rising prices of our favorite fast food items—factors that vary across regions and all 50 states. As for whether you can still afford that frosted lemonade..? Well, you might need to run your own analysis.</p>

<p>
Using those handy-dandy data curation skills, I put together a dataset that includes key economic factors and a variety of fast food items. Although we might have our own guesses and hypotheses about why things happen, truly understanding the world around us requires some good ol' data manipulation and quality EDA.

In the following paragraphs, I’ll walk through some highlights and trends found in the data and introduce my Streamlit app, which allows us to explore these trends in action.
 </p>

### Motivation:
The motivating question that guided my data curation and EDA was this:

<b>How do state-level minimum wage, cost of living, median household income, and other factors impact the average price of a standard fast food meal across the U.S.?</b>

This question also helped shape my analysis, influencing what I looked for in the data. Additional economic factors included in the analysis—but not listed in the question—were: average income, cost of living index, gross domestic product (GDP), GDP growth rate, and unemployment rate.

The fast food items I compared were a Domino’s medium cheese pizza, McDonald’s Happy Meal and Big Mac, a Chick-fil-A sandwich, and a Taco Bell combo meal.

### Highlights:




### Streamlit App:

<a href="https://fast-food-analysis.streamlit.app/" target="_blank">Streamlit App: Fast Food Analysis</a>


#### Purpose:
Post clearly explains the app’s purpose, aligning it with the dataset and audience, and effectively describes its features and value for exploring the data.

#### Features:
Post provides a detailed and engaging description of the app’s features, visualizations, and interactivity, including specific examples of how users can explore the data and gain insights.	

* overall
* region
* fast food and economics by state
* factor vs food

Heatmap: Overall Correlation
<img src="{{site.url}}/{{site.baseurl}}/assets/img/correlation_between_economic_factors_and_restaurant_prices.png" alt="welppp"/>

Heatmap: Region Correlation (South and Northeast)
<img src="{{site.url}}/{{site.baseurl}}/assets/img/heatmap_region.jpg" alt="welppp"/>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/heatmap_region_northeast.jpg" alt="welppp"/>

Choropleth map: Fast Food and Exonomics by State
<img src="{{site.url}}/{{site.baseurl}}/assets/img/chloropeth_food.jpg" alt="welppp"/>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/chloropeth_factor.jpg" alt="welppp"/>

Scatterplot: Fast Food vs. Factor
<img src="{{site.url}}/{{site.baseurl}}/assets/img/scatter_plot.jpg" alt="welppp"/>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/scatter_plot_wisconsin.jpg" alt="welppp"/>


### Conclusion:
Post includes a summary or conclusion with a question or challenge to encourage comments	


<a href="https://github.com/gbean4/blog3_streamlit.git" target="_blank">GitHub Repository</a>

<a href="https://www.youtube.com/watch?v=d7fnzDQ5qM8" target="_blank">Streamlit Crash Course: From Zero to Data App</a>