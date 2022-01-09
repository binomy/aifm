# Basic dataframe manipulations

## Renaming columns

- ```df.columns = ['a', 'b']```
- ```df.rename(columns = {'test': 'TEST'}, inplace=True)```

## Joint Plot - seaborn

- `sns.jointplot(x='sp500', y='nasdaq', data=data_returns)`
