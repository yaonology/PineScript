## 1. What is the Relative Strength Index

### · Background & Formula

RSI, short for Relative Strength Index, developed by Wells Wider in 1978, is based on the principle of supply and demand. 
RSI  is an oscillator indicator. It compares buying and selling power based on the changes in stock prices over a specific period to determine future market trends and the intrinsic nature of stock prices. 
RSI uses the average price increase to represent buying power based on the relationship between demand and price. Similarly, it uses the average price drop to represent selling power.

Accordingly, the formula for RSI(N) equals (average of all closing price rises within N days / (average of all rises within N days + |average of all drops within N days|)) *100
Note: All numbers are in absolute value

RSI = 100 * Average Gain / (Average Loss + Average Gain)

## 2. What does the Relative Strength Index tell you

### · Momentum Concept

Let’s take an example. Wells Wider proved that a 14-day period is efficient to run a back-test and recommends this period. 

(2) By applying a 14-day window, we collect the last 15 days’ closing prices from day 0. 

(3) After calculating price changes of day 1 to day 14, we assign the absolute value of price change to the ‘Gain’ group if the price change is positive, otherwise, to the ‘Loss’ group. 
(Note, we only need to calculate the price changes, not the returns of each day)

(4) When we are done grouping the 14 price changes, we sum up all the numbers and divided by 14, which is the N, in each group. 

(5) Let’s say, we have an average gain of 1.0 and an average loss of 0.8. By applying the RSI formula, we get RSI=(1/(1+0.8))*100=55.55.
