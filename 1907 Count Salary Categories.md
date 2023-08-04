### Pandas
* 行数：df.shape[0]
* 列数：df.shape[1]

```Pandas
import pandas as pd

def count_salary_categories(accounts: pd.DataFrame) -> pd.DataFrame:
    a = accounts[accounts['income'] < 20000]
    b = accounts[(accounts['income'] >= 20000) & (accounts['income'] <= 50000)]
    c = accounts[accounts['income'] > 50000]
    return pd.DataFrame({'category': ['Low Salary', 'Average Salary', 'High Salary'], 'accounts_count': [len(a), len(b), len(c)]})
```