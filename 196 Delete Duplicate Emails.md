### Pandas
* rank(): 排名

```Pandas
import pandas as pd

# Modify Person in place
def delete_duplicate_emails(person: pd.DataFrame) -> None:
    min_id = person.groupby('email')['id'].transform('min')
    remove_person = person[person['id'] != min_id]
    person.drop(remove_person.index, inplace=True)
    


# Modify Person in place
def delete_duplicate_emails2(person: pd.DataFrame) -> None:
    person.sort_values('id', inplace=True)
    person.drop_duplicates(subset=['email'], inplace=True)
```