# Best Way to Use Moving Average as Trading Strategies
Trend analysis is a technique used in technical analysis that attempts to predict the future stock price movements based on recently observed trend data. Trend analysis is based on the idea that what has happened in the past gives traders an idea of what will happen in the future. Moving average indicator is one of the most commonly-used trend indicators.

Below will introduce what is moving average, trading strategies and coding tutorial on TradingView pine script.  

## Moving Average
### 1. Introduction & Function
In finance, a moving average (MA) is a stock indicator that is commonly used in technical analysis. The reason for calculating the moving average of a stock is to help smooth out the price data by creating a continually updated average price. By calculating the moving average, the impacts of random, short-term fluctuations on the price of a stock over a specified time-frame are mitigated.

For example, we can introduce the simple moving average(SMA) first.
![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/SMA.png)
The period can be any positive integer. There are three different ranges.

– Short-term: The period will be from 5 to 30.

– Middle-term: The period will be from 30 to 150.

– Long-term: The period will be from 150 to 250. 

### 2. How to use Simple Moving Average
· Determine the trend

Based on the formula, Simple Moving Average you can see as “The average cost of investors buying the stock in the past number period.” Following this concept, we can determine the stock trend based on the Simple Moving Average.

Simply put, when the simple moving average is going up, we can say that market is experiencing a Bull Trend. When the simple moving average is dropping down, the market is undergoing a Bear Trend.

Bull Trend:

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/bull trend.png)

Bear Trend:

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/bear trend.png)

However, we need to point out the Simple Moving Average is a lagging indicator, which means the indicator helps us determine the trend after the price changes. Thus, the indicator mainly helps us in validating the trend, not predicting the trend.

· Consider as Support & Resistant line

Simple Moving Average can also be seen as a support line or resistance line.
During the bull trend, if the close price drops close to the simple moving average, the simple moving average can be seen as a support line that the stock price will rebound after touching the support line.
