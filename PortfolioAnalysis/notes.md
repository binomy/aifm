# Portfolio versus fund versus index

- portfolio and fund as used interchangeably

## Active vs passive investing

- **Passive investing**: following a benchmark as closely as possible
- **Active investing**: Taking active *bets* that are different form a benchmark
- **Long only strategies**: small deviations from a benchmark.
- **Hedgefunds**: no benchmark but total returns

## Typical portfolio strategies

- Equal weighted portfolios
- Market-cap weighted portfolios
- Risk-return optimized portfolios

## Calculating portfolio weights

- Calculate by dividing the value of a stock by total value of the portfolio

$$
weigth = {Stock's\space vlaue \above{1pt} Total\space portfolio\space value} * 100
$$

## Portfolio returns
- Changes in value over time
$$Return_t = {V_t - V_{t-1} \above{1pt} V_{t-1}}$$

## Calculating returns from pricing data

```python
weigths = np.array([0, 0.50, 0.25])

# Calculate average return for each stock
meanDailyReturns = returns.mean()

# Calculate portfolio return
portReturn = np.sum(meanDailyReturns*weights)
```
```python
# Calculating cumulative returns
# Calculate daily portfolio returns
returns['Portfolio'] = returns.dot(weigths)

# Compound the percentage returns over time
daily_cum_ret = (1+returns).cumprod()
```

