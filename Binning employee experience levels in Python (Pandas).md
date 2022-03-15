
##Binning employee experience levels in Python (Pandas)

Below is a snippet from a table that contains information about employees that work at Company XYZ:

| **employee\_name** | **employee\_id** | **date\_joined** | **age** | **yrs\_of\_experience** |
| --- | --- | --- | --- | --- |
| Andy | 123456 | 2015-02-15 | 45 | 24 |
| Beth | 789456 | 2014-02-15 | 36 | 15 |
| Cindy | 654123 | 2017-05-16 | 34 | 14 |
| Dale | 963852 | 2018-01-15 | 25 | 4 |

Company XYZ is looking to create a report that groups the experience of its employees into 3 simple categories, with the following bins (inclusive):

- 0-5 Low
- 6-15 Medium
- 16+ High

Additionally, you can assume the data is clean and there are no employees with negative or non-numerical years of experience.

Write code in Python (using Pandas) to create a new column in the dataframe, called &#39;experience\_binned&#39;, that groups employees as requested above.


## Solution:


```python:
import pandas as pd
df= pd.read_excel("/content/iqs3.xlsx")
df['date_joined']=pd.to_datetime(df['date_joined']).dt.date
df['experience_in_company']=(pd.datetime.now().date()-df['date_joined']).astype('timedelta64[Y]').astype('int')
df['total_experience']= df['yrs_of_experience']+df['experience_in_company']
df["experience_binned"]=pd.cut(df['total_experience'],[0,5,15,100],labels=["Low","Medium","High"])
df
```
