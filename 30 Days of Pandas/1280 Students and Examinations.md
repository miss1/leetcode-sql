### Pandas
* pd.merge()

```Pandas
import pandas as pd

def students_and_examinations(students: pd.DataFrame, subjects: pd.DataFrame, examinations: pd.DataFrame) -> pd.DataFrame:
    df = examinations.groupby(['student_id', 'subject_name']).size().reset_index(name='attended_exams')
    all_id_sub = pd.merge(students, subjects, how='cross')
    df = pd.merge(all_id_sub, df, on=['student_id', 'subject_name'], how='left')
    df['attended_exams'] = df['attended_exams'].fillna(0).astype(int)
    df.sort_values(by=['student_id', 'subject_name'], inplace=True)
    return df[['student_id', 'student_name', 'subject_name', 'attended_exams']]
```