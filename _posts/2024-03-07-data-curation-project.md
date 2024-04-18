---
layout: post
title:  "A Brief Look at Macroeconomic Trends"
date: 2024-03-27
description: A sample of FRED economic indicators and the impact of the COVID-19 pandemic  
image: "/assets/img/image5.jpg"
display_image: false  # change this to true to display the image below the banner 
---

### Introduction
I'm currently taking a macroeconomics class which studies general trends in the US economy and has plenty of overlap to the data science world. Macroeconomics is a branch of economics that focuses on the study of the economy as a whole, rather than individual markets. It deals with the aggregate phenomena of economic activity, such as total output, employment, inflation, and economic growth, to understand and analyze how these variables interact and influence each other at the national and global levels. 

I wanted a closer look at the overall economics indicators I keep hearing about in class as they related to the Covid-19 pandemic and the resulting lockdowns. We've talked a little about the causes and results during class of inflation at high level. Several of these words have become buzz words that we see on the news or recognize at the grocery store as prices climb. The FRED database or Federal Reserve Economic Data is a comprehensive database of economic data maintained by the Federal Reserve Bank of St. Louis which I used last summer for an internship with the government. I choose to use FRED as a public resource for economic data, accessed using an API key, to gather data on these economic indicators. The five I selected for now are gross domestic product (GDP), the civilian labor force participation rate, the unemployment rate, and consumer price index (CPI).  I also included real GDP or inflation adjusted GDP.

Here's the link if you'd like to explore similar data: [Link to FRED database](https://fred.stlouisfed.org)

#### Data Access
First step after deciding I wanted to focus on economic data was to get an API key for FRED. You need to sign up for a free account on the FRED website. Once you have registered an account, you can navigate to the FRED API section and request an API key. The API key allows you to access FRED's vast data collection for free, and enabling you to retrieve datasets, perform analysis, and integrate economic indicators into your projects. Simply follow the instructions provided on the FRED website to obtain your unique API key, which you can then use to authenticate your requests to the FRED API. Most FRED data is reported quarterly so I kept that the same across each variable. I then filtered each variable to be from 1948 to present.

Once you've loaded the necessary libraries, copy and paste your API key into a separate .txt file named "api_key.txt". It did take me a few tries and fighting with syntax to get the API key to work correctly. (see data_project.ipynb in my project folder for help)
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

Specify which type of data you'd like to access. I started by downloading the nominal GPD dataset (this one is not adjusted for inflation):

```
# Example: Get data for GDP
nominal_gdp_data = fred.get_series('GDP')

# Convert nominal GDP data to DataFrame
nominal_gdp_df = pd.DataFrame({'Date': nominal_gdp_data.index, 'Nominal GDP': nominal_gdp_data.values})

# Filter nominal GDP data to include only data from 1948 to present
nominal_gdp_df = nominal_gdp_df[nominal_gdp_df['Date'].dt.year >= 1948]
```
Here's what the header of what my data looks like:

![Figure]({{site.url}}/{{site.baseurl}}/assets/img/NominalGDPHeader.png)

#### Analysis (so far)
I created a full dataset with 6 variables, using a merge command on the date variable since all the data I accessed is quarterly. This allowed me to keep the same range of data, from 1948 to present. I'll probably do more later with focusing on shorter periods of times to see what trends look like around recessions.

```
# Merge all DataFrames on the 'Date' column
full_df = cpi_df.merge(nominal_gdp_df, on='Date').merge(realgdp_df, on='Date').merge(unemployment_df, on='Date').merge(civpart_df, on='Date')
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

The full_df dataset comprises various economic indicators from the FRED database. It includes data for the Consumer Price Index (CPI), nominal Gross Domestic Product (GDP), real GDP, the unemployment rate, and the civilian labor force participation rate. Each row represents a specific date, and the columns provide the corresponding values for these indicators. GDP, inflation, unemployment rate, etc. are key indicators in macroeconomics that provide valuable insights into the performance and dynamics of economies. By analyzing these indicators, economists and policymakers can assess economic conditions, identify potential challenges, and formulate appropriate policies to promote stability, prosperity, and sustainable growth.

I found that the correlation between CPI and Unemployment Rate of -0.2951189169112918 which suggests a weak negative correlation between these two variables. There is some level of trade-off between inflation and unemployment in the economy, as suggested by the Phillips curve concept (something I learned about last week!). The correlation between Civpart and Unemployment rate for the last 5 years is -0.7833513902786559 and indicates a strong negative correlation between these two variables. This  implies that changes in labor force participation can have a substantial impact on the unemployment rate and vice versa. For example, an increase in labor force participation may lead to lower unemployment rates as more people enter or re-enter the labor market. Thankfully we can see both of these rates are returning to pre-pandemic levels.

#### A Closer Look at the Pandemic
![Figure]({{site.url}}/{{site.baseurl}}/assets/img/unemployment.png)
![Figure]({{site.url}}/{{site.baseurl}}/assets/img/civpart_line.png)

The two graphs depict the immediate impact of the pandemic on unemployment rates. While there was a noticeable decline in the Civilian Labor Force Participation Rate (Civpart), it wasn't as significant as anticipated, amounting to approximately 3%. Conversely, there was a stark and rapid increase in the unemployment rate, reaching around 10%. Reflecting on the government's response, it's clear that these economic indicators underscore the challenges faced during times of crisis. I'd like a closer look at role of inflation in the near future.

### Conclusion
It is important to remember numbers represent real lives and their impact is crucial in understanding the significance of economic indicators and statistics. Economic indicators provide insights into the health and performance of an economy. Behind these numbers lie stories of individuals seeking employment, families struggling to make ends meet, businesses striving to thrive, and policymakers making decisions that shape the lives of millions. For instance, a rise in the unemployment rate signifies job losses, financial strain, and uncertainty for individuals and families. As part of the class, I had to watch the most recent annoucement from the Federal Reserve so I'm trying to pay more attention to what's happening to the US economy. It'll be interesting to see shifts as a result of the upcoming election and accompanying politiking.

My challenge to the reader: try to access one economic indicator of choice, and analyze one recent trend which you've heard about on the news.

Here is a link to the app I created using StreamLit: [Economic Indicators App](https://economic-indicators-stat386.streamlit.app/Correlations)

#### Sources
[Project folder](https://github.com/t-anderson21/blog-project/tree/main)

[Link to FRED data for CIVPART](https://fred.stlouisfed.org/series/CIVPART)

[Link to data for real GDP](https://fred.stlouisfed.org/series/GDPC1)
