### Pandas

```Pandas
import pandas as pd

def food_delivery(delivery: pd.DataFrame) -> pd.DataFrame:
    df = delivery[delivery['order_date'] == delivery['customer_pref_delivery_date']]
    percentage = round(len(df) * 100 / len(delivery), 2)
    return pd.DataFrame({'immediate_percentage': [percentage]})
```