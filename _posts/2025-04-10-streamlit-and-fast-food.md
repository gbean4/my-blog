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

This question also helped shape my analysis, influencing what I looked for in the data. Additional economic factors included in the analysis—but not listed in the question—were: average income, cost of living index, gross domestic product (GDP), GDP growth rate, and unemployment rate. The fast food items I compared were a Domino’s medium cheese pizza, McDonald’s Happy Meal and Big Mac, a Chick-fil-A sandwich, and a Taco Bell combo meal.

### Highlights:

<dl>
<dt>Average Income and Fast Food</dt>
<dd>One of the most notable trends in the data is the strong correlation between average income and fast food prices. The average correlation coefficient between national average income and the price of fast food items ranges from 0.76 to 0.86, with Domino’s cheese pizza being an outlier at 0.47. This lower correlation is likely due to pizza generally being more expensive than a burger or sandwich.</dd>
<dd>This trend is most clearly observed in scatter plots comparing average income to individual food item prices. Each plot shows a slight upward linear trend, indicating a positive relationship. <i>(See the scatter plots in the Streamlit section for visuals.)</i>
</dd>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/kid_with_fries.jpg" alt="welppp"/>


<dt>Fast Foods Compared to Each Other</dt>
<dd>Another key insight from the data is the strong relationship between fast food restaurants and each other. This is most clearly shown in a correlation heatmap by region <i>(also featured in the next section)</i>. In the South, West, Northeast, and much of the Midwest, there is a high correlation between McDonald’s and Chick-fil-A prices. In some regions, this correlation is as high as 1:1.</dd>
<dd>Based on the heatmap and correlation values, the trend suggests that—regardless of the underlying factors, whether income-related or untracked variables like supply and demand—fast food prices tend to increase in tandem across restaurants.</dd>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/restaurants.jpg" alt="welppp"/>
</dl>


### Streamlit App: <a href="https://fast-food-analysis.streamlit.app/" target="_blank">Fast Food Analysis</a>

#### Purpose:
The major benefit of using a Streamlit application to explore the data is its ability to reveal trends from multiple perspectives. In my Streamlit app, I focused on four different types of visualizations: an overall correlation heatmap, a regional correlation heatmap, choropleth maps for fast food items and economic factors, and a general scatter plot to track trends. Feel free to click the link above and explore how each factor impacts your favorite chain restaurants.

#### Features:

##### Heatmap: Overall Correlation
<img src="{{site.url}}/{{site.baseurl}}/assets/img/correlation_between_economic_factors_and_restaurant_prices.png" alt="welppp"/>

The overall correlation heatmap is just what it sounds like, but in case of confusion, the Streamlit includes a brief explanation to help guide interpretation and highlight where to look for meaningful relationships. This map represents the average of each economic factor and fast food price across all 50 states.

##### Heatmap: Region Correlation (South and Northeast)
<img src="{{site.url}}/{{site.baseurl}}/assets/img/heatmap_region_south.jpg" alt="welppp"/>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/heatmap_region_northeast.jpg" alt="welppp"/>

While the overall map provides a useful high-level summary, the regional maps reveal how these relationships vary across the country. The most noticeable differences appear between the South and Northeast. Since the Northeast tends to have a wider range of household incomes and cost of living, and the South a narrower range, the regional heatmaps reflect these contrasts.

##### Choropleth map: Fast Food and Exonomics by State
<img src="{{site.url}}/{{site.baseurl}}/assets/img/chloropeth_food.jpg" alt="welppp"/>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/chloropeth_factor.jpg" alt="welppp"/>

The choropleth maps are especially interesting for observing state-level trends. By selecting a specific food item and economic factor, one can compare how similar or different the two maps appear. Maps with similar color patterns suggest a positive relationship, while noticeable differences in coloring indicate a weaker or nonexistent trend.


##### Scatterplot: Fast Food vs. Factor
<img src="{{site.url}}/{{site.baseurl}}/assets/img/scatter_plot.jpg" alt="welppp"/>
<img src="{{site.url}}/{{site.baseurl}}/assets/img/scatter_plot_wisconsin.jpg" alt="welppp"/>


Although not as numerically precise, the scatter plots reveal positive linear trends—or the absence of them—within the data. Users can select an economic factor and a fast food item to explore how, as economic factors increase in more expensive states, fast food prices tend to rise as well. Scatter plots are also useful for identifying outliers. For example, in the second plot, there is a clear linear trend between average income and McDonald’s Happy Meal prices—except in the state of Wisconsin. This is valuable information, as outliers suggest that additional, untracked factors may be influencing the data.

### Conclusion:
In my data, the trends and correlations indicate that economic factors do, in fact, impact fast food prices. This is evident across all states and regions, especially when comparing areas with higher costs of living or average incomes. My motivating question reflects the concern that when economic conditions worsen, the fast food industry may follow suit. From the strong correlation between average income and fast food prices to the regional differences highlighted in the heatmaps, the data shows just how closely our economic environment is tied to what ends up on our tray.

The Streamlit application’s graphs and maps are incredibly useful for observing these trends and experimenting with different parameters to compare specific factors. I encourage you to continue exploring the app—and maybe even apply it to your own data questions!

Below are links to my GitHub repository and a tutorial to help you get started on your own Streamlit adventures. Happy coding!

<a href="https://github.com/gbean4/blog3_streamlit.git" target="_blank">GitHub Repository</a>

<a href="https://www.youtube.com/watch?v=d7fnzDQ5qM8" target="_blank">Streamlit Crash Course: From Zero to Data App</a>