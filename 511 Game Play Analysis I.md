### Pandas

```Pandas
import pandas as pd

def game_analysis(activity: pd.DataFrame) -> pd.DataFrame:
    activity = activity.groupby('player_id')['event_date'].min().reset_index()
    activity.rename(columns={'event_date': 'first_login'}, inplace=True)
    return activity
```