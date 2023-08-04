### Pandas
* 获取前N条数据：df.head(N)
* 获取后N条数据：df.tail(N)

```Pandas
import pandas as pd

def nth_highest_salary(employee: pd.DataFrame, N: int) -> pd.DataFrame:
    df = employee[['salary']].drop_duplicates()
    if len(df) < N:
        return pd.DataFrame({'getNthHighestSalary(2)': [None]})
    return df.sort_values('salary', ascending=False).head(N).tail(1)
```