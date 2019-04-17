---
markup: mmark
tags: ["investing"]
categories: ["investing"]
date: 2019-04-10T00:00:00Z
published: true
title: Saving for Retirement
---

## Pop-quiz

You worked very hard and earned $1000 that you want to save for your retirement. 
You are going to retire in 20 to 40 years. What should you do?

1) Keep the money in your mattress.
2) Buy gold.
3) Buy US Treasuries.
4) Buy ETF tracking S&P500.

You can [jump to the answer](#conclusion) right away or keep reading to see the 
analysis.

## Problem Setup and Data

I would like to investigate what is the probability of a negative return on 
an investment over a fixed time horizon - holding time. Since I cannot time the 
market, I assume I randomly pick a time to invest. I will use historical data to 
see all possible returns for a given time horizon, with all possible starting 
times. The probability of negative returns will be computed from this sample 
distribution.

I will use historical data compiled by [Robert Shiller](http://www.econ.yale.edu/~shiller/data.htm).
The data contains a monthly history of S&P500, its monthly dividends, 10 year
treasury rates and the Consumer Price Index (CPI) describing inflation
from 1871 to present.

## Mattress Saving Strategy

First, I'd like to consider an old strategy where you keep the money in your 
mattress. It turns out there were periods in US history when that was not a bad 
idea. Investing by keeping money in cash works if your dollar can buy more in
the future than today. I use the Consumer Price Index (CPI) as a measure of how 
much you can buy using your money. In particular, CPI allows us to express the
value of past dollars in today's dollars:

{style="text-align: center"}![value of dollar](/images/dollar.png)

You can see that before 1900 and around 1930 the value of money had increased 
(deflation). The most recent deflation happened in 2009, although it was small 
and you cannot see it on this graph. 

Let's see how this investment strategy performs (the plot shows the mean, median,
and percentiles - 5% and 95%, of the return distribution given the length of the
holding period):

{style="text-align: center"}![mattress strategy performance](/images/mattress.png)

We can see that if we keep money in the mattress, we most probably would lose 
its value. The following plot shows the probability of losing its value given
the length of the holding period:

{style="text-align: center"}![mattress strategy loss probability](/images/p-mattress.png)

## Gold

Gold prices look a little bit better - there is no obvious down-trend and if you 
squint hard enough you can see an up-trend:

{style="text-align: center"}![gold prices](/images/gold-history.png)

Let's see how the returns are distributed:

{style="text-align: center"}![gold returns](/images/gold-rets.png)

The probability of losing value when investing in gold for different holding 
periods is shown on the plot below:

{style="text-align: center"}![gold loss probability](/images/gold-loss.png)

This is quite a bit better than keeping money in a mattress, but there is still 
a 30% probability of losing money which is quite depressing.

## Bonds

The data that I use has the history of the yield for 10 year treasury bonds. I
will consider the following saving strategy using 10 year bonds: I will buy
a 10 year bond, keep it until maturity, then buy another bond and repeat the
process until the end of holding period. If the holding period ends before the 
last 10 year bond matures, I will use its yield until the end of the holding 
period.

For example, suppose I want to start saving when I'm in January 1990. Suppose
I want to hold the saving for 25 years. Then I will buy 10 year bond with yield
specified for January 1990. This bond will maature in January 2000. Once it 
matures I receive premium and buy another 10 year bond with yield specified for
January 2000. This bond will mature in January 2010. Now I need to buy 5 year 
bond. I will assume that such bond has same yield as 10 year bond specified in
January 2010. 

Let's see how the yield of a 10 year bond changed over time:

{style="text-align: center"}![10y bond yeilds](/images/bond-hist.png)

We compute the returns of this strategy over different holding times, adjusting
for inflation:

{style="text-align: center"}![bond strategy returns](/images/bond-rets.png)

The probability of loss is a lot smaller compare to the previous strategies:

{style="text-align: center"}![bond loss probability](/images/bond-loss.png)

Even though the probability of loss is lower than with the previous two 
strategies, I was quite surprised that it was still that high. Let's take a
look at stocks and see if we can get better results.

## Stocks

The stock data has two numbers for each month: the index level and dividends.
On the news you usually hear a lot about the stock index level, but not that 
much about dividends. You can do several things with dividends - spend them, 
keep them stashed somewhere (mattress), reinvest (into index or other securities).
I will consider two strategies. With the first I will just spend my dividends, 
or in other words, I will just pay attention to the level of the index. With the 
second, more reasonable, strategy I will reinvest the dividends into the same 
index.

### No Dividend Reinvestment

The inflation adjusted value of the SP500 index changed over time as follows:

{style="text-align: center"}![inflation adjusted SP500](/images/sp500.png)

The returns of the "no dividend reinvestment" strategy are:

{style="text-align: center"}![no dividends returns](/images/sp500-nd-rets.png)

Compare this plot to the bond's returns. They are quite similar, with similar
values of returns and distribution. However, the probability of loss is twice
as much as that of the bond strategy.

{style="text-align: center"}![no dividend loss](/images/sp500-nd-loss.png)

Let's see how the results change when we reinvest the dividends.

### With Dividend Reinvestment

The returns of the strategy with reinvested dividends are:

{style="text-align: center"}![no dividends returns](/images/sp500-rets.png)

Comparing to the other strategies it is obvious that this one produces the 
highest returns. But more importantly (for the goal of saving) the distribution
is mostly located in the positive region (at least for long enough holding 
periods). Let's see what this means for the probability of loss:

{style="text-align: center"}![sp500 with dividends loss](/images/sp500-loss.png)

Holy-moly - the probability of loss is essentially 0 if we hold our portfolio
for a little longer than 20 years.

**Think how remarkable this result is:** we used stock history spanning
two world wars, the Great Depression and the Great Recession. Even if you had to 
sell your stocks at the bottom of the Great Depression, but held them for more 
than 20 years before that, you would not suffer a loss in value in your 
portfolio, you would not lose a single hard earned dollar. From the analysis 
above no other asset class could give us such certainty.

## Conclusion

As the result of the analysis above shows, the answer to the pop-quiz is (4) - 
buy S&P500, but don't forget to reinvest dividends. Let’s look at the 
probability of loss for each of these strategies on the same plot:

{style="text-align: center"}![loss for all strategies](/images/loss.png)

As a bonus we also get higher overall returns when investing in stocks. The
plot below shows the distribution of yields for the stock and bond strategies:

{style="text-align: center"}![yields](/images/yields.png)

If you look carefully enough, you can see that for holding periods of less than 
14 years the stock strategy is a lot more risky than the bond. However if your 
holding period exceeds 14 years the stock strategy is both, less risky and
yielding better returns. Also notice that in long term, the width of the yield
distribution for the stock strategy is about the same as for bonds, but overall
it is shifted up by several percent.

What does it all mean for regular folks that are trying to save for the 
retirement? Don't worry about whether the market is trending up or down, it's in 
a bubble or a recession is coming. You will never be able to time the market. 
But putting money in stocks and not touching them (other than reinvesting 
dividends) for long periods of time will ensure that your hard-earned money will
not be lost, also giving you a chance to earn quite a healthy return - no downside 
and all the upside.

## What's Next

I'm planning to continue exploration on how regular folks, "rest of us", should
invest to save for retirement. Here are some of the questions I'm planning to
cover:

* Most of the savings often come closer to retirement. I'd like to investigate
which strategy would work best in that case.

* The common advice by financial profesionals is to allocate more capital
to bonds as you approach retirement age. I'd like to explore how sound this
advice is and what would be reasonable schedule for such reallocation.

* Tax advantaged accounts (401K, IRA, Roth IRA) are quite popular means to
save for retirement. I'd like to quantify how much benefit those accounts
provide.

