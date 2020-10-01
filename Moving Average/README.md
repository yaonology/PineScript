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
#### · Determine the trend

Based on the formula, Simple Moving Average you can see as “The average cost of investors buying the stock in the past number period.” Following this concept, we can determine the stock trend based on the Simple Moving Average.

Simply put, when the simple moving average is going up, we can say that market is experiencing a Bull Trend. When the simple moving average is dropping down, the market is undergoing a Bear Trend.

Bull Trend:

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/bull_trend.png)

Bear Trend:

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/bear_trend.png)

However, we need to point out the Simple Moving Average is a lagging indicator, which means the indicator helps us determine the trend after the price changes. Thus, the indicator mainly helps us in validating the trend, not predicting the trend.

#### · Consider as Support & Resistant line

Simple Moving Average can also be seen as a support line or resistance line.
During the bull trend, if the close price drops close to the simple moving average, the simple moving average can be seen as a support line that the stock price will rebound after touching the support line.
![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/support_line_example.png)

On the other hand, if the close price rebounds close to the simple moving average in the bear trend, the simple moving average can be seen as a resistance line, and the stock price will drop after touching the resistance line.
![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/resistant_line_example.png)

#### · Create strategies

The moving average indicator is not only a handy analytic tool but also an excellent trading strategy. We will focus on its different kinds of algorithms in the next part

### 3. Create Trading Strategies
#### · Close price above/below Simple Moving Average

(1) The simplest one is that Close price above/below Simple Moving Average
When the close price is higher than the simple moving average, buy the equity.
When the close price is lower than the simple moving average, sell the equity.
(2) This strategy is straightforward to use, but we do not recommend it in a short-term period. The shorter period simple moving average, the more sensitive signal. Therefore, we recommend this simple strategy used in the middle-term and long-term period. We will compare the backtesting report later.

#### · Short-term/Middle-term Simple Moving Average Crosses

(3) The second strategy we introduce here is Short/Middle-term Simple Moving Average crosses.
When the short-term simple moving average crosses over middle-term simple moving average, buy the stock.
When the short-term simple moving average crosses under the long-term simple moving average, sell the stock.
(4) This strategy considers the short-term trend and middle/long-term. However, every asset has different time cycles and volatility. You have to use the backtesting report to find the best period for different assets.

#### · Short-term/Middle-term Simple Moving Average Cross and Long-term Simple Moving Average is on the long-term bull trend

(5) The in-depth Simple Moving Average is “Short/Middle-term Simple Moving Average crosses and Long-term Simple Moving Average is on the long-term bull trend.”
(6) This strategy considers the Short-term, Middle-term, and Long-term. It uses the long-term Simple Moving Average to determine the long-term bull trend and then uses the short-term and middle-term to find the buying point and selling points. It can remove the fake signal when the stock is in the long-term bull trend.





