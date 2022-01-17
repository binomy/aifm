# Managing portfolio risk

## How do variance and correlation relate to portfolio risk?

- The correlation between asset 1 and 2 is denoted by $\rho_{1,2}$, and tells us to which extend assets move together
- The **portfolio variance** takes into account the individual assets' **variances**, the weigths of the assets in the portfolio $(W_1, W_2)$, as well as their correlation to each other.
- The **Standard deviation** ($\sigma$) is equal to the square root of the variance, both are a measure of volatility.

## Calculating portfolio variance

$$
\sigma^2_{pf} = W^2_1{\sigma^2_1}\space + W^2_2\sigma^2_2\space + 2W_1W_2\rho_{1,2}\sigma_1\sigma_2
$$

- $\rho_{1,2}\sigma_1\sigma_2$ is called as covariance between asset 1 and 2
- The covariance can also be written as $\sigma_{1,2}$

- What we need to calculate in python is
  - *Portfolio variance = Weights transposed * (Covariance matrix * Weigths)*

## Portfolio variance in python

```python
# Calculate daily returns from prices
daily_returns = df.pct_change()

# construct a covariance matrix for the daily returns data
cov_matrix_d = daily_returns.cov()
```

- Annualise the volataility by multiplying by 250 - which is the number of trading days.

```python
cov_matrix_d = (daily_returns.cov())*250

weights = np.array([0.2, 0.2, 0.2, 0.2, 0.2])

port_variance = np.dot(weights.T, np.dot(cov_matrix_a, weights))
```