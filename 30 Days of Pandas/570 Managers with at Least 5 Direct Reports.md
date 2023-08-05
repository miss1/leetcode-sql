### Pandas
* pd.merge()

```Pandas
import pandas as pd

def find_managers(employee: pd.DataFrame) -> pd.DataFrame:
    df = employee.groupby('managerId').size().reset_index(name='count')
    df = df[df['count'] >= 5]
    merge_info = pd.merge(df, employee, how='inner', left_on='managerId', right_on='id')
    return merge_info[['name']]
```