# Methods to manipulate time series data

## Convert dataframe to a series

- Using .squeeze()

```python
  df.squeeze().pct_change()
```

## Rolling Window functions

- Rolling will calculate based on previous period
- Calculate rolling average

```python
  data.rolling(window='30').mean()
```

- window=30 *Business days*
- min_periods *choose value <30 to get results for first days*
- window=30D last 30 *Calendar days*

- 90 day rolling mean

```python
  r90 = data.rolling(window='90D').mean()
  df2.join(r90.add_suffix('_mean_90')).plot()
```

- .join concatenate series or dataframe along `axis 1`.

- Multiple rolling metrics

```python
  data.price.rolling('90D').agg(['mean', 'std'])
```

## Expanding window functions

- Two options in pandas:
  - `.expanding()` - just like `.rolling()`
  - `.cumsum()`, `.cumprod()`, `.cummin() / max()`

## How to caluclate a running return

- single period return r: current prices minu over last price minus 1
- multi period return: product of (1 + r) for all periods, minus 1
