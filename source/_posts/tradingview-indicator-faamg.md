---
title: Script for tradingview
---

There is a requirement:
>Need tradingview script to create a similar indicator like this attached indicator https://www.tradingview.com/script/XiU3SXXQ/ but will need to be able to use it for my stocks to chose and to get alerts when the 2 lines diverge & converge.
> 

Here is my solution:

```
indicator("tradingview script", overlay=true)

f=input.symbol('META')
sf = request.security(f, timeframe.period, close)

a=input.symbol('AMZN')
sa = request.security(a, timeframe.period, close)

a2=input.symbol('AAPL')
sa2 = request.security(a2, timeframe.period, close)

m=input.symbol('MSFT')
sm = request.security(m, timeframe.period, close)

g=input.symbol('GOOGL')
sg = request.security(g,timeframe.period, close)

plot(sa*0.143*2 + sf*0.072*2 + sa2*0.372*2 + sm*0.317*2 + sg*0.096*2)
```