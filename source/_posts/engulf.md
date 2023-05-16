---
title: tradingview engulf indicator
date: 2023-05-16 10:49:43
tags: tradingview
author: Shannon
---
There is a requirement like this:

>If first 30m candle after 5pm utc is red and second 30m is green ( close above the last one ) engulfing candle I want to send an alert or draw a alert on Tradingview.

Here is my solution

```
//@version=5
indicator("Engulf Script")

t1 = time(timeframe.period, "1730-1800", "GMT+0")

currentDiff = close - open
preDiff = close[1] - open[1]
mark = 0

if t1 and preDiff < 0 and currentDiff>0 and close > open[1]
    mark := 100

plot(mark,   "Engulf Index",    color = color.green)
```