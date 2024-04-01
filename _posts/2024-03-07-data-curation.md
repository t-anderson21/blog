---
layout: post
title:  "A Brief Look at Macroeconomic Trends"
date: 2024-03-27
description: A sample exploration of economic indicators available on FRED   
image: "/assets/img/image5.jpg"
display_image: false  # change this to true to display the image below the banner 
---

#### Introduction
I'm currently taking a macroeconomics class which studies general trends in the US economy and has plenty of overlap to the data science world. Macroeconomics is a branch of economics that focuses on the study of the economy as a whole, rather than individual markets. It deals with the aggregate phenomena of economic activity, such as total output, employment, inflation, and economic growth, to understand and analyze how these variables interact and influence each other at the national and global levels. 

I wanted a closer look at the overall economics indicators I keep hearing about in class as they related to the Covid-19 pandemic and the resulting lockdowns. We've talked a little about the causes and results during class of inflation at high level. Several of these words have become buzz words that we see on the news or recognize at the grocery store as prices climb. The FRED database or Federal Reserve Economic Data is a comprehensive database of economic data maintained by the Federal Reserve Bank of St. Louis which I used last summer for an internship with the government. It has important data on indicators in macroeconomics such as gross domestic product, inflation, and economic growth that provide valuable insights into the state of an economy. I choose to use FRED as a public resource for economic data, accessed using an API key, to gather data on these economic indicators. The five I selected for now are gross domestic product (GDP) or total value of goods & services in the US, inflation or the natural rise and fall of prices, the civilian labor force participation rate, the unemployment rate, and consumer price index (CPI).  I also included Real GDP which is GDP inflation adjusted value of the US output as a comparison to GDP.

Here's the link if you'd like to explore the available data: [Link to FRED database](https://fred.stlouisfed.org)

#### Data Access

First step after deciding I wanted to focus on economic data was to get an API key for FRED. To obtain an API key from the Federal Reserve Economic Data (FRED), you need to sign up for an account on the FRED website. Once you have registered an account, you can navigate to the FRED API section and request an API key. The API key allows you to access FRED's vast collection of economic data programmatically, enabling you to retrieve datasets, perform analysis, and integrate economic indicators into your applications or projects. Simply follow the instructions provided on the FRED website to obtain your unique API key, which you can then use to authenticate your requests to the FRED API.

Most FRED data is reported quarterly so I kept that the same across each variable. I also keep each variable as over time same time period, from 1948 to present.

```
pip install numpy
```
Once you've loaded the necessary libraries, copy and paste your API key into a separate .txt file named "api_key.txt". It did take me a few tries and fighting with syntax to get the API key to work correctly.
```
# Only reference API file
with open('api_key.txt', 'r') as file:
    api_key = file.read().strip()

# Initialize the Fred object with your API key
fred = Fred(api_key=api_key)

# Example: Get data for Real GDP, not GDP
gdp_data = fred.get_series('GDPC1')
gdp_df = pd.DataFrame({'Date': gdp_data.index, 'GDP': gdp_data.values})

# Filter real GDP data to include only data from 1948 to present
realgdp_df = gdp_df[gdp_df['Date'].dt.year >= 1948]
```

Specify which type of data you'd like to access. I started by downloading the entire GPD dataset (this one is not adjusted for inflation):

```
# Example: Get data for nominal GDP
nominal_gdp_data = fred.get_series('GDP')

# Convert nominal GDP data to DataFrame
nominal_gdp_df = pd.DataFrame({'Date': nominal_gdp_data.index, 'Nominal GDP': nominal_gdp_data.values})

# Filter nominal GDP data to include only data from 1948 to present
nominal_gdp_df = nominal_gdp_df[nominal_gdp_df['Date'].dt.year >= 1948]

# Display the DataFrame
print(nominal_gdp_df)
```
If this was sucessful here's what the header of what my data looked like:

![Nominal GDP Head](assets/img/NominalGDP Header.png)
assets/img/NominalGDP Header.png


#### Analysis (so far)

I created a full dataset with 6 variables, using a merge command on the date variable since all the data I accessed is quarterly. This allowed me to keep the same range of data, from 1948 to present. I'll probably do more later with focusing on shorter periods of times to see what trends look like around recessions.

```
# Merge all DataFrames on the 'Date' column
full_df = cpi_df.merge(nominal_gdp_df, on='Date').merge(realgdp_df, on='Date').merge(unemployment_df, on='Date').merge(civpart_df, on='Date')

# Save full_df as CSV
full_df.to_csv('full_data.csv', index=False)
```

Here is a brief description of the various indicators I included:

| Variables    | Description / Data type                                  |
| ------------ | ---------------------------------------------------------|
| Date         | (datetime) Format is YYYY/MM/DD                          |
| CPI          | (float) average change over time in the prices for a market basket of consumer goods and services |
| Nominal GDP  | (numeric) the total value of all goods and services produced within a country's borders without adjusting for inflation  |
| GDP          | (numeric) total measure of the total value of goods & services produced within a country's borders, adjusted for inflation |
| Unemployment | (float) the percentage of the labor force that is unemployed and actively seeking employment |
| CIVPART      | (float) the percentage of the civilian labor force either employed or actively seeking employment |


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

#### Conclusion
It is important to remember numbers represent real lives and their impact is crucial in understanding the significance of economic indicators and statistics. While numbers themselves may seem abstract, they are deeply intertwined with real-life experiences and have tangible impacts on individuals, communities, and societies. Economic indicators provide insights into the health and performance of an economy. Behind these numbers lie stories of individuals seeking employment, families struggling to make ends meet, businesses striving to thrive, and policymakers making decisions that shape the lives of millions. For instance, a rise in the unemployment rate signifies job losses, financial strain, and uncertainty for individuals and families. It can lead to challenges in meeting basic needs, increased stress levels, and disruptions in communities. As part of the class, I had to watch the most recent annoucement from the Federal Reserve so I'm trying to pay more attention to what's happening with the US economy. It'll be interesting to see shifts as a result of the upcoming election and the likely politiking.

My challenge to the reader: try to access one economic indicator of choice, and analyze one recent trend,.


#### Sources
[Project folder](https://github.com/t-anderson21/blog-project/tree/main)

[Link to FRED data for CIVPART](https://fred.stlouisfed.org/series/CIVPART)

[Link to data for real GDP](https://fred.stlouisfed.org/series/GDPC1)
