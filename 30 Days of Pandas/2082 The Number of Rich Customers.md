### Pandas

```Pandas
import pandas as pd

def count_rich_customers(store: pd.DataFrame) -> pd.DataFrame:
    df = store[store['amount'] > 500]
    df.drop_duplicates(subset='customer_id', inplace=True)
    return pd.DataFrame({'rich_count': [len(df)]})
```