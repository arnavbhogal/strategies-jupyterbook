## Bollinger Bands Strategy

Definition:
The Bollinger Bands Strategy is a volatility-based trading strategy that uses three lines plotted on a price chart: a middle moving average, an upper band, and a lower band. These bands expand when market volatility increases and contract when volatility decreases. The strategy assumes that prices tend to move back toward the average after touching the upper or lower bands.

## Source references

www.tradingview.com/pine-script-docs/

www.investopedia.com/terms/b/bollingerbands.asp

## Pine Script implementation
//@version=5
strategy("Bollinger Bands Strategy", overlay=true)

length = 20
mult = 2.0

basis = ta.sma(close, length)
dev = ta.stdev(close, length)

upperBand = basis + mult * dev
lowerBand = basis - mult * dev

longCondition = close < lowerBand
shortCondition = close > upperBand

if longCondition
    strategy.entry("Long", strategy.long)

if shortCondition
    strategy.entry("Short", strategy.short)

plot(basis, color=color.blue)
plot(upperBand, color=color.red)
plot(lowerBand, color=color.green)



## Pros (Detailed Analysis)

Volatility awareness: Clearly shows when the market is calm or highly active

Visual clarity: Upper and lower bands make price extremes easy to identify

Effective in sideways markets: Performs well when price moves within a range

Widely used strategy: Trusted and well-documented in technical analysis

Simple concept: Easy to understand even for users without finance background

Adaptable: Automatically adjusts to changing market volatility

## Cons (Detailed Analysis)

Poor trend performance: Generates incorrect signals during strong trends

Mean-reversion assumption: Assumes price will return to average, which is not always true

No risk management: Does not include stop-loss or profit-taking rules

False reversals: Price may ride the band instead of reversing

Parameter sensitivity: Results depend heavily on band length and deviation

Overtrading risk: Frequent signals in volatile markets

## 3 Defined Weaknesses:

Trend blindness: Cannot differentiate between trending and ranging markets

False signals: Produces misleading reversal signals during breakouts

Risk exposure: Lacks protection against large losses

## 3 Defined Improvements:

Trend filtering: Use a moving average or ADX to confirm market direction

Risk management: Add stop-loss and take-profit levels

Confirmation indicators: Combine with RSI or volume analysis


## Conclusion

The Bollinger Bands Strategy is a powerful volatility-based approach that helps identify price extremes and potential reversals. It is easy to understand and visually intuitive, making it suitable for beginners. However, it struggles during strong trending markets. By adding trend confirmation and proper risk management, the strategy becomes significantly more reliable for real-world trading.
