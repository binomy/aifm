# Risk adjusted return

- It defines an investment's return by measuring how much risk is involved in producing that return
- It's usually a ratio
- Allows you to objectively compare across different investment options
- Tells you whether the return justifies the underlying risk

## Sharpe ratio

- sharpe ratio is the most commonly used risk adjusted return ratio
- It's calculated as follows:
$$
Sharpe ratio = {{R_p - R_f} \above{1pt} \sigma_p}
$$
- Where: $R_p$ is the portfolio return, $R_f$ is the risk free rate and $\sigma_p$ is the portfolio standard deviation

## Annualizing the volatility

- Annualized standard deviation is calculated as follows: $\sigma_a =  \sigma_m * \sqrt{T}$
- $\sigma_m$ is the measured standard deviation
- $\sigma_a$ is the annualized standard deviation
- T is the number of data points per year
  - T can be 250 when daily, 52 when weekly

## Calculating the Sharpe Ratio

```python
# Calculate the annualized standard deviation
annualized_vol = apple_returns.std()*np.sqrt(250)

# Defin the risk free ratio
risk_free = 0.01

# Calculate the sharpe ratio
sharpe_ratio_ratio = (annualized_return - risk_free) / annualized_vol
```

```python
# An example using sp500 data
# Calculate total return and annualized return from price data
total_return = (sp500_value[-1] - sp500_value[0]) / sp500_value[0]

# Annualize the total return over 4 year
annualized_return = ((1 + total_return)**(1/4))-1

# Create the returns data
returns_sp500 = sp500_value.pct_change()

# Calculate annualized volatility from the standard deviation
vol_sp500 = returns_sp500.std() * np.sqrt(250)

# Calculate the Sharpe ratio
sharpe_ratio = ((total_return - rfr) / vol_sp500)
print (sharpe_ratio)
```


