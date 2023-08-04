### Pandas
* employees.groupby(['event_day', 'emp_id'])['total_time'].sum().reset_index()

```Pandas
import pandas as pd

def total_time(employees: pd.DataFrame) -> pd.DataFrame:
    employees['total_time'] = employees['out_time'] - employees['in_time']
    employees = employees.groupby(['event_day', 'emp_id'])['total_time'].sum().reset_index()
    employees.rename(columns={'event_day': 'day'}, inplace=True)
    return employees
```