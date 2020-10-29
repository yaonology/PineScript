[![Bollinger Bands PineScript TradingView Code-along Tutorial | Trading Algorithm](https://res.cloudinary.com/marcomontalbano/image/upload/v1603944020/video_to_markdown/images/youtube--entlmZFUEtA-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=entlmZFUEtA&feature=youtu.be "Bollinger Bands PineScript TradingView Code-along Tutorial | Trading Algorithm")

# Best Way to Use Bollinger Bands as Trading Strategies
Bollinger Bands are a type of statistical chart characterizing the prices and volatility over time of a financial instrument or commodity. Bollinger Bands provide a relative definition of high and low prices of a market, which can contribute to rigorous pattern recognition and is useful in comparing price actions and indicator actions to achieve systematic trading decisions. 

Below will introduce what is Bollinger Bands, trading strategies and coding tutorial on TradingView pine script.  

## Bollinger Bands 
### 1. What is the Bollinger Bands
Bollinger Bands are a technical analysis tool developed by John Bollinger in the 1980s. Bollinger Bands are a type of chart indicator for technical analysis and have become widely used by traders in many markets, including stocks, futures, and currencies. 

There are three lines that compose Bollinger Bands: A simple moving average (middle band) and an upper and lower band. By default, the middle band is the simple moving average of the past 20 days. The upper and the lower bands are 2 standard deviations from the middle band.
 
![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Bollinger%20Bands/Pictures/Bollinger_Bands_Upper_Middle_Lower.png)
 
The purpose of Bollinger Bands is to provide a relative definition of high and low prices of a market. Prices are relatively high at the upper band and low at the lower band. There are several uses for Bollinger Bands, such as determining overbought and oversold levels, as a trend following tool, and for monitoring for breakouts.

### 2. What does the Bollinger Band tell you
#### · Statistical Concept

Bollinger Bands are based on the statistical concept that there is over 95% possibility that the stock price would fall between two standard deviations from the simple moving average. 

There is a 95.45% possibility that the stock price will be between the two standard deviations, the upper and lower lines. 

If the stock price is higher than the upper band, it is a 2.275% possibility. which means that the stock price might be overbought. 

On the other hand, If the stock price is lower than the lower band, it is a 2.5% possibility, which means that the stock price might be oversold.

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Bollinger%20Bands/Pictures/Normal_Distribution.png =400x)
![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Bollinger%20Bands/Pictures/Bollinger_Bands_Probability.png =400x)

#### · Bollinger Band Percent B

Percent B reflects close price as a percentage of the lower and upper Bollinger Bands. It can easily visualize the stock price is overbought or oversold.

Percent B equals close price minus lower band over upper band minus lower band, multiply by 100. 

%B = (Price-Lower Band)/(Upper Band-Lower Band)  ×100

If the close price is higher than the upper band, percent B would be greater than 100. In this case, it is usually that the stock price is overbought

If the close price is equal to the 20-day moving average, percent B is 50. In this case, the stock price is natural.

If the close price is lower than the lower band, percent B would be lower than 0. In this case, the stock price is oversold.

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Bollinger%20Bands/Pictures/Bollinger_Bands_Percent_B.png)

#### · Bollinger Band Width

The Bollinger Band Width reflects the consolidation of stock price movements and volatility. The Bollinger Band Width can see the strength of trend (both on bull and bear trend.) The Bollinger Band Width is the difference between the upper and lower bands over the middle band.

Band Width=  (Uppper Band-Lower Band)/(Middle Band)

When the stock price volatility increases, the difference between the upper and lower band will widen, and the Bollinger Band Width will increase, which means that the strength of trend increases.

On the other hand, when the stock price volatility decreases, the difference between the upper and lower will contract, the Bollinger Band Width will decrease, which is a sign that the current trend may be ending

When the distance between the two bands is relatively narrow that is often a sign that there is no bull or bear trend.
 
![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Bollinger%20Bands/Pictures/Bollinger_Bands_Width.png)
 
The Bollinger Band Width can show the strength of the trend but cannot determine whether it is a bull or a bear trend.

### 3. Create Trading Strategies
#### · Percent B Strategy

(1) The simplest one is that when the previous percent B is below 0 and today the percent B is back above 0, which means that the stock price is oversold, and the market investors start to buy back. Then, we buy the equity.

(2) The previous percent B is above 100% and today the percent B is back below 100%, which means that the stock price is overbought, and the market investors start to sell. Then, we sell the equity.

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Bollinger%20Bands/Pictures/Bollinger_Bands_Strategy_Percent_B.png)

#### · Percent B and Long-term Simple Moving Average
(1) The second strategy is combining percent B with Simple Moving Average. The previous percent B is below 0 and today the percent B is back above 0, which means that the stock price is oversold, and the market investors start to buy back. Also, the stock price is still in the long-term bull, 200-day simple moving average is still moving up. We buy the equity.

(2) The previous percent B is above 100% and today the percent B is back below 100%, which means that the stock price is overbought, and the market investors start to sell. Then, we sell the equity.

![Image of Yaktocat](https://github.com/yaonology/PineScript/blob/master/Bollinger%20Bands/Pictures/Bollinger_Bands_Strategy_Percent_B_and_SMA.png)

### 4. Pine Script Examples
#### · Initial Setting
(1) Initial setting is the step we set up the strategy property, which includes “Strategy ID”, “The plot overlays the main chart or show on the separate chart pane. ”, “How much is the initial capital”, “How many percentages of capital buying the equity?”, “How much is commission fee”

(2) First, we need to set up the Pine Script version. Here, we are using the last version, version four.

(3) Then, we start to code the strategy property. The double quote we type “Yaonology Bollinger Band Tutoring”, which is the strategy id.

(4) “overlay equals true” means that the plot overlays the main chart. On the other hand, if “overlay equals false”, it means that the plot will show on the separate chart pane.

(5) Then, we set up the initial capital, here, we code “initial_capital equals 10000” and “currency = currency.USD”, which means that we are using US$10000 as the initial capital

(6) Then, we need to determine how many shares we trade equities. Here, we code “default_qty_type equals strategy.percent_of_equity” and “default_qty_value equals a hundred”, which means that we are using the percentage type to trade the equity, and we use 100 percent of capital to trade the equities.

(7) Finally, we set up the commission fee. Here, we code “commision_type equals strategy.commission.percent” and “commission_value = 0”, which means that we use the percentage type to calculate the commission fee, and here we set up 0% commission fee because most brokers don’t charge the commission fee currently.

    //Step One: Initial Setting
    //@version = 4
    strategy("Yaonology Bollinger Bands Tutorial", overlay = false, currency = currency.USD, initial_capital = 10000, default_qty_type = strategy.percent_of_equity, default_qty_value = 100, commission_type = strategy.commission.percent, commision_value = 0)
    
#### · Parameter Setting
(1) Parameter Setting is the step we set up the Bollinger Band parameter. 

(2) The sma function returns the moving average. Close means the close price, and 20 means the 20 bars period.

(3) ”mdl equals sma close and 20” means we give “mal” the value of 20 days simple moving average. 

(4) The stdev function returns standard deviation. Close means the close price, and 20 means the 20 bars period.

(5) “dev equals stdev close and 20” means that we give “dev” the value of 20 days standard deviation.

(6) “upr equals mdl plus 2 times dev” means that we give “upr” the value of middle line plus 2 standard deviations. The “upr” is the value of the upper band.

(7) “lwr equals mdl minus 2 times dev” means that we give “lwr” the value of middle line minus 2 standard deviations. The “lwr” is the value of the lower band.

(8) Then, we calculate the percent B. P_B equals close price minus lower band, times 100, and over upper band minus lower band.

(9) Finally, we calculate Bollinger Band Width. BB_W equals upper band minus lower band time 100 over middle line.
 
    //Step Two: Parameter Setting
    //Bollinger Bands
    mdl = sma(close, 20)
    dev = stdev(close, 20)
    upr = mdl + 2*dev
    lwr = mdl - 2*dev
    pb = (close - lwr)*100/upr - lwr) //Percent B
    bbw = (upr - lwr)*100/mdl //Bollinger Bands Width
    
#### · Plotting
a. Plot Upper, Middle and Lower Bands

(1) Plot is the step that we plot the moving average on the main chart series. However, there is a limit that we cannot plot Bollinger Bands, Percent B and Bollinger Band Width in the three different chart series.

(2) The plot function can plot a series of data on the chart. “mdl” is what data series we want to plot. “Color equals color.red” means that we plot “mdl” as a red color.

(3) “Upr” is the data series we want to plot, and color equals color.blue means that we plot ‘upr’ as a blue color. And, we give the p1 value of plot ‘upr’

(4) ‘lwr’ is the data series we want to plot, and color equals color.purple means that we plot ‘lwr’ as a purple color, And, we give the p2 value of plot ‘lwr’

(5) The “fill” function is to fill the background between two plots.

(6) Here, we fill the background between upper band and lower band
 
    //Step Three: PLot
    plot(bdl, color = color.red)
    p1 = plot(upr, color = color.blue)
    p2 = plot(lwr, color = color.purple)
    fill(p1,p2)

b. Plot Percent B and Bollinger Bands Width

(1) Then, we plot percent B and Bollinger bands width.

(2) We plot the ‘pb’ data series and give it black color

(3) We plot the ‘bbw’ data series and give it green color

    //Percent B
    plot(pb, color = color.black)
    
    //Bollinger Bands Width
    plot(bbw, color = color.green)
    
#### · Strategy Entry and Strategy Close
Strategy Entry and Strategy Close is the step that we set up a condition to buy equity and sell the equity.

a. Percent B Strategy

(1) The first strategy we use is the Percent B Strategy.  If the previous Percent B is smaller than 0 and the percent B today is greater than 0, we take it as a buying point. 

(2) If the previous Percent B is larger than 100 and the percent B today is smaller than 100, we take it as a selling point.
 
    //Step Four: Strategy Entry and Strategy Close
    if pb[1] < 0 and pb > 0
        strategy.entry(id = "BB_buy", long = true)
    
    if pb[1] > 100 and pb < 100
        strategy.close(id = "BB_buy")

|  | **Net Profit** | **Precent Profitable** | **Profit Factor** | **Max Drawdown** | 
| --- | --- | ---| --- | --- |
| **Percent B Strategy** | 397.27% | 86.11% | 3.306 | 34.37% |

b. Percent B Strategy with Long-term Simple Moving Average

(1) The second strategy is combing Percent B Strategy with Long-term Simple Moving Average. If the previous Percent B is smaller than 0 and the percent B today is greater than 0 and the 200-day simple moving average is growing, we take it as a buying point.

(2) If the previous Percent B is larger than 100 and the percent B today is smaller than 100, we take it as a selling point.
 
    //Step Four: Strategy Entry and Strategy Close
    if pb[1] < 0 and pb > 0 and sma(close, 200)>sma(close,200)[1]
        strategy.entry(id = "BB_buy", long = true)
    
    if pb[1] > 100 and pb < 100
        strategy.close(id = "BB_buy")
 
c. Percent B and Middle-term/Long-term Simple Moving Average Strategy

(1) The third strategy is combing Percent B with Middle-term/Long-term Simple Moving Average Strategy. If the closing price is smaller than lower band and the 200-day simple moving average is smaller than 60-day Simple Moving Average, we take it as a buying point.

(2) If the close price is larger than the upper band and the 200-day simple moving average is greater than 60-day Simple Moving Average, we take it as a selling point.
 
    //Step Four: Strategy Entry and Strategy Close
    if clp < lwr and sma(close, 200) < sma(close, 60)
        strategy.entry(id = "BOLL1", long = true)
    
    if clp > upr and sma(close, 200) > sma(close, 60)
        strategy.close(id = "BOLL1")

|  | **Net Profit** | **Precent Profitable** | **Profit Factor** | **Max Drawdown** | 
| --- | --- | ---| --- | --- |
| **Percent B Strategy** | 397.27% | 86.11% | 3.306 | 34.37% |
| **Percent B with Long-term SMA** | 474.74% | 90.91% | 12.856 | 13.96% |
| **Percent B with Long/Mid-term SMA** | 717.4% | 80% | 32.317 | 5.42% |


