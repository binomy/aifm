# Alternative measures of risk

## Sortino Ratio

- Similar to the sharpe ratio, just with a different standard deviation
$$
Sortino\ Ratio = {R_p - R_f \above{1pt} \sigma_d}
$$

- $\sigma_d$ is the standard deviation of the downside.

$$
  Downside\ risk = \sqrt{{1 \above{1pt} n} \displaystyle\sum_1^n(return - target \ return)^2 f(t)}\\
  f(t) = {1 if return < target return}\\
  f(t) = 0 if return >= target return
$$

## Sortino ratio in python

```python
# Define risk free rate and target return of 0
rfr = 0
target_return = 0

# Calculate the daily return from price data
apple_returns=pd.DataFrame(apple_price.pct_change())

# Select the negative returns only
negative_returns = apple_returns.loc[apple_returns['AAPL'] < target_return]

# Calculate expected return and std dev of downside returns
expected_return = apple_returns['AAPL'].mean()
down_std = negative_returns.std()

# Calculate the sortino ratio
sortino_ratio = (expected_return - rfr)/down_stdev
```

## Maximum draw-down
- The largest percentage loss from a market peak to trough

## Maximum daily draw-down in python
```python
# Calculate the maximum value of returns using rolling().mac()
roll_max = apple_price.rolling(min_periods=1, window=250).max()

# Calculate daily draw-down from rolling max
daily_drawdown = apple_price/roll_max - 1.0

# Calculate maximum daily draw-down
max_daily_drawdown = daily_drawdown.rolling(min_periods=1, window=250).min()