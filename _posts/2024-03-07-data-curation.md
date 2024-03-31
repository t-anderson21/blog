---
layout: post
title:  "Macroeconomic Data Trends"
date: 2024-03-27
description: A sample exploration of data available on FRED   
image: "/assets/img/image5.jpg"
display_image: false  # change this to true to display the image below the banner 
---

## Introduction
I'm currently taking a macroeconomics class which studies general trends in the US economy. 

I wanted to look over at the overall economics indicators as it related to the Covid-19 pandemic and the resulting lockdowns. We've talked a little about the causes and results during class, but everyone remembers 

Most FRED data is reported quarterly so I kept that the same across each variable. I also keep each variable as over time same time period, from 1948 to present.

Macroeconomics is a branch of economics that focuses on the study of the economy as a whole, rather than individual markets. It deals with the aggregate phenomena of economic activity, such as total output, employment, inflation, and economic growth, to understand and analyze how these variables interact and influence each other at the national and global levels.


Key indicators in Macroeconomics such as Gross Domestic Product (GDP), inflation, and economic growth stand out as fundamental measures that provide valuable insights into the state of an economy. I used Federal Reserve Economic Data or (FRED) as a public resource for economic data, accessed using an API key, to gather data on economic indicators. The five I selected for now are gross domestic product (GDP) or total value of goods & services in the US, inflation or the natural rise and fall of prices, the civilian labor force participation rate, and ___  

I also included Real GDP which is GDP inflation adjusted value of the US output.

## PROCESS



ANALYSIS (so far)
Gross Domestic Product (GDP):
GDP represents the total monetary value of all goods and services produced within a country's borders over a specific period, typically a year or a quarter. It serves as a comprehensive measure of an economy's output and represents the size and scale of economic activity. GDP can be broken down into different components, including consumption, investment, government spending, and net exports, offering insights into the contributions of various sectors to overall economic output.
Inflation:
Inflation refers to the rate at which the general level of prices for goods and services rises over time, resulting in a decrease in the purchasing power of money. Moderate inflation is generally considered healthy for an economy, as it encourages consumption and investment while discouraging hoarding of cash. However, high or unpredictable inflation can erode consumer purchasing power, disrupt economic planning, and lead to inefficiencies in resource allocation. Central banks closely monitor inflation and often target a specific inflation rate as part of their monetary policy objectives.
Economic Growth:
Economic growth reflects the expansion of an economy's production capacity over time, resulting in an increase in the level of real output and income. Sustainable economic growth is essential for improving living standards, reducing poverty, and fostering long-term prosperity. Factors such as technological innovation, capital accumulation, labor productivity, and institutional reforms contribute to economic growth. Policymakers use various tools and policies to promote economic growth, including fiscal policies (government spending and taxation) and monetary policies (interest rates and money supply).
In summary, GDP, inflation, and economic growth are key indicators in macroeconomics that provide valuable insights into the performance and dynamics of economies. By analyzing these indicators, economists and policymakers can assess economic conditions, identify potential challenges, and formulate appropriate policies to promote stability, prosperity, and sustainable growth.

The full_df dataset comprises various economic indicators from the FRED database. It includes data for the Consumer Price Index (CPI), nominal Gross Domestic Product (GDP), real GDP, the unemployment rate, and the civilian labor force participation rate. Each row represents a specific date, and the columns provide the corresponding values for these indicators. This dataset spans from 1948 to the present, providing a rich resource for analyzing and understanding trends in inflation, economic growth, labor market dynamics, and workforce participation over time.


The correlation between CPI and Unemployment Rate: -0.2951189169112918

The correlation between Civpart and Unemployment rate for the last 5 years: -0.7833513902786559

Thankfully we can see both of these rates are returning to pre-pandemic levels. I think its safe to say we are reaching a 'soft' land and avoiding any true recession effects, but maybe that's a topic for later I can try to prove using this data.

/assets/img/image5.jpg

/assets/img/unemployment_rate_trends.png

/assets/img/civpart_line.png
## Conclusion
It is important to remember numbers represent real lives and their impact is crucial in understanding the significance of economic indicators and statistics. While numbers themselves may seem abstract, they are deeply intertwined with real-life experiences and have tangible impacts on individuals, communities, and societies. Economic indicators provide insights into the health and performance of an economy. Behind these numbers lie stories of individuals seeking employment, families struggling to make ends meet, businesses striving to thrive, and policymakers making decisions that shape the lives of millions. For instance, a rise in the unemployment rate signifies job losses, financial strain, and uncertainty for individuals and families. It can lead to challenges in meeting basic needs, increased stress levels, and disruptions in communities. As part of the class, I had to watch the most recent annoucement from the Federal Reserve so I'm trying to pay more attention to what's happening with the US economy. It'll be interesting to see shifts as a result of the upcoming election and the likely politiking.

Challenge: ....  Analyze the Trends and Implications of Economic Indicators


#### Sources
[Link to Project folder](https://github.com/t-anderson21/blog-project/tree/main)

[Link to FRED database](https://fred.stlouisfed.org/series)
