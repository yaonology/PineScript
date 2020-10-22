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
    default_qty_type = strategy.precent_of_equity, default_qty_value = 100,
    currency = currency.USD, initial_capital = 10000,
    commission_type = strategy.commission.percent, commission_value = 0)
    
### · Step Two: Parameter Setting
(1) Step Two Parameter Setting is the step we set up the RSI parameter. 

(2) By using the built-in function ‘rsi’ and indicating that we are using the closing price of the last 14 days, we can easily get the RSI indicators, which we label as ‘r’.

     //Step Two: Parameter Setting
     r = rsi(close, 14)
     
### · Step Three: Plotting

(1) Now let’s plot what we just got.

(2) Plot brackets r comma color equals color dot blue means we will be plotting RSI in blue.

    //Step Three: Plotting
    plot(r, color = color.blue)
    
### · Step Four: Strategy Entry and Strategy Close

#### RSI Overbought and Oversold

(1) In the previous section, we discussed in theory how to pick buying and selling points with RSI indicators using the overbought and oversold area. Here, we are replicating the strategy by pine script.

(2) We use the if statements to tell the system when to buy and when to sell. If r is larger than 30 and the previous r is smaller than 30 are the conditions of buying the stock. 

(3) When these conditions are met, we tell the system to buy stock. Strategy dot entry brackets id equals quote kd comma long equals true is the expression we use to buy the stock. Id equals quote kd means whenever a transaction happens there will be a small label called kd beside it.

(4) Long equals true means we are buying the stock when the conditions above are met.

(5) Remember, you must press tab before all lines to be executed by if statement.

(6) Next, we define when to sell the stock. We sell when observing RSI crosses down in the overbought area, where r is smaller than 70 and the previous r is larger than 70.

(7) Strategy dot close brackets id equals quote id means we are telling the system to sell the stock when conditions mentioned above are met. Again, we add a label called kd to each selling transaction. Remember, the id under buying instruction and selling instruction must match, otherwise there’ll be an error.

(8) Also, we don’t need the long equals true part anymore, as we are selling, or shorting, not longing the stock any more.

    //Step Four: Strategy Entry And Strategy Close
    if (r > 30 and r[1] < 30)
        strategy.entry(id = "kd", long = true)
        
    if (r < 70 and r[1] > 70)
        strategy.close(id = "kd") 
        
 |  | **Net Profit** | **Precent Profitable** | **Profit Factor** | **Max Drawdown** | 
| --- | --- | ---| --- | --- |
| **RSI Overbought and Oversold** | 105.66% | 85.11% | 2.129 | 39.13% |

(9) This is the historical cumulative result we get by applying KD strategy only to SPY data.

#### RSI Bull and Bear Zone

(1) Now, let’s develop the RSI bull and bear trend strategy.

(2) we now define our buying condition as the following: if we see RSI is larger than 60 and the previous RSI is smaller than 60, we buy the stock.

(3) on the other hand, if we see RSI is smaller than 40 and the previous RSI is larger than 40, we sell the stock

(4) By comparing the two strategies’ back-test results, we could see that RSI overbought and oversold strategy is better than the RSI bull and bear zone strategy!

    //Step Four: Strategy Entry And Strategy Close
    if (r > 60 and r[1] < 60)
        strategy.entry(id = "kd", long = true)
        
    if (r < 40 and r[1] > 40)
        strategy.close(id = "kd") 
        
|  | **Net Profit** | **Precent Profitable** | **Profit Factor** | **Max Drawdown** | 
| --- | --- | ---| --- | --- |
| **RSI Overbought and Oversold** | 105.66% | 85.11% | 2.129 | 39.13% |
| **RSI Bull and Bear Zone** | 87.81% | 39.24% | 1.467 | 40.15% |

#### RSI Against Market

(1) Finally, let’s have a look at what happenes if we use an against market strategy.

(2) In the overbought and oversold strategy, we buy the stock if RSI reaches the oversold area and sell the stock if the RSI reaches the overbought area. 

(3) Now, we buy the stock if RSI leaves the overbought area and wait to sell the stock until RSI leaves the oversold area. 

(4) The logic is that when RSI leaves the overbought area, it means the selling power is increasing to drive the price down. We buy the stock when the selling power is large enough to drag RSI out of the overbought area. But now the price may be high because more people are selling the stock in the market. Against the market, we buy the stock anyway.

(5) Then, we wait even though RSI drops into the oversold area. We wait until the buying power is increasing high enough to drag RSI out of the oversold area when more people are buying the stock in the market. Here the stock price will reach a new high, which might be higher than our purchase price. Now, we can sell the stock.

(6) Now, you will be surprised by a much higher net profit and a significant lower max drawdown of RSI against market strategy. 

    //Step Four: Strategy Entry And Strategy Close
    if (r > 70 and r[1] < 70)
        strategy.entry(id = "rsi", long = true)
        
    if (r < 30 and r[1] > 30)
        strategy.close(id = "rsi") 
        
|  | **Net Profit** | **Precent Profitable** | **Profit Factor** | **Max Drawdown** | 
| --- | --- | ---| --- | --- |
| **RSI Overbought and Oversold** | 105.66% | 85.11% | 2.129 | 39.13% |
| **RSI Bull and Bear Zone** | 87.81% | 39.24% | 1.467 | 40.15% |        
| **RSI Against the Market** | 164.42% | 68.18% | 3.856 | 8.62% | 


