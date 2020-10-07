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

### 4. Pine Script Examples
#### · Initial Settings

(1) Step one initial setting is the step we set up the strategy property, which includes “Strategy ID,” “The plot overlays the main chart or show on the separate chart pane. ”, “How much is the initial capital,” “How many percentages of capital buying the equity?”, “How much is the commission fee.”

(2) First, we need to set up the Pine Script version. Here, we are using the last version, version four.

(3) Then, we start to code the strategy property. The double quote we type “Yaonology Moving Average Tutoring,” which is the strategy id.

(4) “overlay equals true” means that the plot overlays the main chart. On the other hand, if “overlay equals false,” it means that the scheme will show on the separate chart pane.

(5) Then, we set up the initial capital, here, we code “initial_capital equals 10000” and “currency = currency.USD”, which means that we are using US$10000 as the initial capital

(6) Then, we need to determine how many shares we trade equities. Here, we code “default_qty_type equals strategy.percent_of_equity” and “default_qty_value equals a hundred,” which means that we are using the percentage type to trade the equity, and we use 100 percent of capital to buy the stakes.

(7) Finally, we set up the commission fee. Here, we code “commission_type equals strategy.commission.percent” and “commission_value = 0”, which means that we use the percentage type to calculate the commission fee, and here we set up 0% commission fee because most brokers don’t charge the commission fee currently.

//Step One: Initial Setting
//@version = 4
strategy("Yaonology Moving Average Tutoring", overlay = true, currency = currency.USD, initial_capital = 10000, default_qty_type = strategy.percent_of_equity, default_qty_value = 100, commission_type = strategy.commission.percent, commision_value = 0)

Then, we will try these three algorithms in pine script and do the backtesting.

a. Close price above/below Simple Moving Average

//Step Two: Parameter Setting
fst = input(title = "MA_Fast", defval = 20)
slw = input(title = "MA_Slow", defval = 40)
ma_fast = sma(close, fst)
ma_slow = sma(close, slw)

//Step Three: Plot
plot(ma_fast, color = color.blue)
plot(ma_fast, color = color.green)

//Step Four: Strategy Application
if close > ma_fast
    strategy.entry(id = "ma_long", long = true)
    
if ma_fast > close
    strategy.close(id = "ma_long")

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/overview_algorithm_a.png)

b. Short-term/Middle-term Simple Moving Average Crosses

//Step Two: Parameter Setting
fst = input(title = "MA_Fast", defval = 20)
slw = input(title = "MA_Slow", defval = 40)
ma_fast = sma(close, fst)
ma_slow = sma(close, slw)

//Step Three: Plot
plot(ma_fast, color = color.blue)
plot(ma_fast, color = color.green)

//Step Four: Strategy Application
if ma_fast > ma_slow
    strategy.entry(id = "ma_long", long = true)
    
if ma_slow > ma_fast
    strategy.close(id = "ma_long")

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/overview_algorithm_b.png)

c. Short-term/Middle-term Simple Moving Average Cross and Long-term Simple Moving Average is on the long-term bull trend

(5) The in-depth Simple Moving Average is “Short/Middle-term Simple Moving Average crosses and Long-term Simple Moving Average is on the long-term bull trend.”

(6) This strategy considers the Short-term, Middle-term, and Long-term. It uses the long-term Simple Moving Average to determine the long-term bull trend and then uses the short-term and middle-term to find the buying point and selling points. It can remove the fake signal when the stock is in the long-term bull trend.

//Step Two: Parameter Setting
fst = input(title = "MA_Fast", defval = 20)
slw = input(title = "MA_Slow", defval = 40)
ma_fast = sma(close, fst)
ma_slow = sma(close, slw)

//Step Three: Plot
plot(ma_fast, color = color.blue)
plot(ma_fast, color = color.green)

//Step Four: Strategy Application
if ma_slow > ma_slow[1]
    if ma_fast > ma_slow
        strategy.entry(id = "ma_long", long = true)
    
if ma_slow > ma_fast
    strategy.close(id = "ma_long")

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Moving%20Average/overview_algorithm_c.png)
