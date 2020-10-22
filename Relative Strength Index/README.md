## 1. What is the Relative Strength Index

### · Background & Formula

RSI, short for Relative Strength Index, developed by Wells Wider in 1978, is based on the principle of supply and demand. 

RSI  is an oscillator indicator. It compares buying and selling power based on the changes in stock prices over a specific period to determine future market trends and the intrinsic nature of stock prices. 

RSI uses the average price increase to represent buying power based on the relationship between demand and price. Similarly, it uses the average price drop to represent selling power.

Accordingly, the formula for RSI(N) equals (average of all closing price rises within N days / (average of all rises within N days + |average of all drops within N days|)) *100. 
(Note: All numbers are in absolute value)

RSI = 100 * Average Gain / (Average Loss + Average Gain)

## 2. What does the Relative Strength Index tell you

### · Momentum Concept

Let’s take an example. Wells Wider proved that a 14-day period is efficient to run a back-test and recommends this period. 

By applying a 14-day window, we collect the last 15 days’ closing prices from day 0. 

After calculating price changes of day 1 to day 14, we assign the absolute value of price change to the ‘Gain’ group if the price change is positive, otherwise, to the ‘Loss’ group. 
(Note, we only need to calculate the price changes, not the returns of each day)

When we are done grouping the 14 price changes, we sum up all the numbers and divided by 14, which is the N, in each group. 

Let’s say, we have an average gain of 1.0 and an average loss of 0.8. By applying the RSI formula, we get RSI=(1/(1+0.8))*100=55.55.

Picture

### · Overbought and Oversold 

Now, we have the RSI numbers, let’s see two sets of definitions which can help us judge the buy and sell points. First, overbought and oversold.

Normally, when RSI is higher than 70,  it is a good time to sell because the market is in overbought status.

When RSI is lower than 30, it is a good time to buy because the market is in oversold status.

Picture

### · Bull/Bear Trend

Beside overbought and oversold,we can also use RSI to define bull and bear trend.

When RSI is higher than 40, the market is in the bull market. In a bull market, RSI tends to remain above 40, and 40 can be seen as a support line. 

When RSI is lower than 60, the market is in the bear market. In a bear market, RSI tends to remain below 60, so 60 can be  seen as a resistance line.

Picture

## 3. Relative Strength Index Strategy

### · Overbought and Oversold

Since we have summarized the certain patterns of RSI. How could we use these patterns to develop trading strategies?

First, when we observe RSI is in the oversold area, which indicates the prices are too low. Here comes the buying point when RSI crosses over 30.

After we are in the market, we need to find the selling point. While the first time that RSI crosses over 70 from bottom is not a good point since RSI just reaches the overbought area, a better selling point is when RSI crosses down 70 from overbought area where the selling price could be high.

Picture

### · Bull/Bear Trend

Another method is to use the bull and bear trend.

We have introduced the resistance line, so we know if RSI reaches 60 and remains above 60, we have a bull trend in the market, which means many investors are buying the asset. Thus, it is a good point to buy when RSI crosses over 60 since the price is not too high here.

After price increases to some degree, it would begin to drop and so would RSI. Here the 40 support line could help us determine the selling point. When RSI drops below 40, the selling power in the market is larger than the buying power, so we could predicate a price drop of the asset, followed by the bear trend. Thus, we have a good selling point when RSI crosses down 40.

Picture

## 4. Tradingview Pine Script (Screen recording)

### · Step One: Initial Setting

(1) Step one initial setting is the step we set up the strategy property, which includes “Strategy ID”, “The plot overlays the main chart or show on the separate chart pane. ”, “How much is the initial capital”, “How many percentages of capital buying the equity?”, “How much is commission fee”

(2) First, we need to set up the Pine Script version. Here, we are using the lastest version, version four.

(3) Then, we start to code the strategy property. In double quotes, we type “Yaonology RSI Indicators Tutorial”, which is the strategy ID.

(4) “overlay=false” means that the plot will show on the separate chart pane.

(5) First, we need to determine how many shares we trade equities. Here, we code “default_qty_type equals strategy.percent_of_equity” and “default_qty_value equals a hundred”, which means that we are using the percentage type to trade the equity, and we use 100 percent of capital to trade the equities.

(6) Then, we set up the initial capital, here, we code “initial_capital = 10000” and “currency = currency.USD”, which means that we are using US$10000 as the initial capital.

(7) Finally, we set up the commission fee. Here, we code “commision_type equals strategy.commission.percent” and “commission_value = 0”, which means that we use the percentage type to calculate the commission fee, and here we set up 0% commission fee because most brokers don’t charge the commission fee currently.

    //Step One: Initial Setting
    //@version = 4
    Strategy("Yaonology RSI Indicators Tutorial", overlay=false, 
    
