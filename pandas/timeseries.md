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

- single period return r: current price over last price minus 1
- multi period return: product of (1 + r) for all periods, minus 1
- for the period return: `.pct_change()`
- for basic math: `.add()`, `.sub()`, `.mul()`, `.div()`
- for cummulative product: `.cumprod()`

### Running rate of return in practice

```python
  pr = data.SP500.pct_change() # period return
  pr_plus_one = pr.add(1)
  cummulative_return = pr_plus_one.cumprod().sub(1)
  cummulative_return.mul(100).plot()
```

### Getting running min and max

```python
  data['running_min'] = data.SP500.expanding().min()
  data['running_max'] = data.SP500.expanding().max()
```

### Rolling annual rate of return

```python
  def multi_period_return(period_returns):
    return np.prod(period_returns - 1) + 1

  pr = data.SP500.pct_change() # period return
  r = pr.rolling('360D').apply(multi_period_return)
  data['Rolling 1yr Return'] = r.mul(100)
```
