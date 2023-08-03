### Pandas
* 去重：df.drop_duplicates(subset=['author_id'], inplace=True)
* 排序：df.sort_values(by=['author_id'], inplace=True)
* 重命名：df.rename(columns={'author_id': 'id'}, inplace=True)

```Pandas
import pandas as pd

def article_views(views: pd.DataFrame) -> pd.DataFrame:
    df = views[views['author_id'] == views['viewer_id']]

    # Only preserve rows that contain unique 'author_id'.
    df.drop_duplicates(subset=['author_id'], inplace=True)

    # Sort the DataFrame in ascending order of 'author_id'.
    df.sort_values(by=['author_id'], inplace=True)

    df.rename(columns={'author_id': 'id'}, inplace=True)
    df = df[['id']]
    return df
```