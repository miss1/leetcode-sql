### Pandas
* 获取前N条数据：df.head(N)
* 获取后N条数据：df.tail(N)

```Pandas
import pandas as pd

def second_highest_salary(employee: pd.DataFrame) -> pd.DataFrame:
    df = employee[['salary']].drop_duplicates()
    if len(df) < 2:
        return pd.DataFrame({'SecondHighestSalary': [None]})
    return df.sort_values('salary', ascending=False).head(2).tail(1).rename(columns = {'salary': 'SecondHighestSalary'})
```