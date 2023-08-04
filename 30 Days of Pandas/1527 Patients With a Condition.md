### Pandas
* 包含: str.contains(r'\bDIAB1', regex=True)

```Pandas
import pandas as pd

def find_patients(patients: pd.DataFrame) -> pd.DataFrame:
    return patients[patients['conditions'].str.contains(r'\bDIAB1', regex=True)]
    
    

def find_patients2(patients: pd.DataFrame) -> pd.DataFrame:
    return patients[patients['conditions'].str.startswith('DIAB1') | patients['conditions'].str.contains(' DIAB1', regex=False)] 
```