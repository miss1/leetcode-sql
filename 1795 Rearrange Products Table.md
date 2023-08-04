### Pandas
* pd.concat([a, b, c])
* melt()

```Pandas
import pandas as pd

def rearrange_products_table(products: pd.DataFrame) -> pd.DataFrame:
    a = products.loc[products['store1'].notna(), ['product_id', 'store1']]
    a['store'] = 'store1'
    a.rename(columns={'store1': 'price'}, inplace=True)
    a = a[['product_id', 'store', 'price']]

    b = products.loc[products['store2'].notna(), ['product_id', 'store2']]
    b['store'] = 'store2'
    b.rename(columns={'store2': 'price'}, inplace=True)
    b = b[['product_id', 'store', 'price']]

    c = products.loc[products['store3'].notna(), ['product_id', 'store3']]
    c['store'] = 'store3'
    c.rename(columns={'store3': 'price'}, inplace=True)
    c = c[['product_id', 'store', 'price']]
    
    return pd.concat([a, b, c])
    
    

def rearrange_products_table(products: pd.DataFrame) -> pd.DataFrame:
    df = products.melt(id_vars='product_id', var_name='store', value_name='price')
    df = df.dropna(axis=0)
    return df
```