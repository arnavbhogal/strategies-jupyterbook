Consecutive Up/Down Strategy

Definition:
The Consecutive Up/Down Strategy is a rule-based trading strategy that checks whether the price has moved up or down continuously for a fixed number of bars (time units). If the price closes higher than the previous close for several consecutive bars, the strategy assumes upward momentum. Similarly, consecutive lower closes indicate downward momentum. The strategy is based on the idea that short-term movement often continues briefly once it starts.

Source references

www.tradingview.com/pine-script-docs/

www.investopedia.com/terms/m/momentum.asp

www.investopedia.com/terms/t/timeseriesanalysis.asp

## Pine Script implementation
//@version=5
strategy("Consecutive Up/Down Strategy", overlay=true)

consecutiveBarsUp = input(3, "Consecutive bars up")
consecutiveBarsDown = input(3, "Consecutive bars down")

price = close
ups = 0.0
ups := price > price[1] ? nz(ups[1]) + 1 : 0

dns = 0.0
dns := price < price[1] ? nz(dns[1]) + 1 : 0

if ups >= consecutiveBarsUp
    strategy.entry("Long", strategy.long)

if dns >= consecutiveBarsDown
    strategy.entry("Short", strategy.short)


## Pros (Detailed Analysis)

Very simple logic: Uses basic comparison between current and previous prices

No complex indicators: Does not rely on moving averages or oscillators

Fast execution: Minimal calculations make it suitable for quick decision-making

Momentum-based: Captures short bursts of continuous movement

Easy to understand: Can be explained without financial background

Flexible settings: Number of consecutive bars can be adjusted easily

## Cons (Detailed Analysis)

High false signals: Consecutive moves often happen near the end of a short-term run

No risk management: Does not include stop-loss or profit targets

Ignores move size: Small price changes are treated the same as large ones

Sideways market weakness: Generates frequent wrong entries in choppy markets

No strength confirmation: Assumes momentum without validating it

Overtrading risk: Can enter trades repeatedly during volatile periods

## Weaknesses & Improvements

## 3 Defined Weaknesses:

Whipsaws: Rapid direction changes lead to repeated losses

No magnitude filter: Cannot differentiate strong moves from weak noise

Risk exposure: No built-in loss protection

## 3 Defined Improvements:

Volatility filter: Require minimum price movement before entry

Momentum confirmation: Combine with RSI or volume increase

Risk management: Add stop-loss and trailing exits


## Conclusion

The Consecutive Up/Down Strategy is a straightforward momentum-based approach that looks for continuous price movement over a short period. It is easy to understand and implement, making it suitable for beginners and non-financial users. However, the strategy is vulnerable to false signals and lacks safety mechanisms. By adding movement filters, confirmation indicators, and basic risk management, the strategy becomes more stable and practical for real-world use.