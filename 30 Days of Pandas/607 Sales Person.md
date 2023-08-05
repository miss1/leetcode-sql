### Pandas
* pd.merge()

```Pandas
import pandas as pd

def sales_person(sales_person: pd.DataFrame, company: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    order_company = pd.merge(orders, company, how='left', on='com_id')
    order_company = order_company[order_company['name'] == 'RED']
    df = sales_person[~sales_person['sales_id'].isin(order_company['sales_id'])]
    return df[['name']]
```