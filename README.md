# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
    
 # Code:
import numpy as np  

import pandas as pd

from scipy import stats

import seaborn as sns

df = pd.read_csv("bhp.csv")

print(df)

1.Remove outliers using IQR
median = df['price_per_sqft'].quantile(0.5)
Q1 = df['price_per_sqft'].quantile(0.25)
Q3 = df['price_per_sqft'].quantile(0.75)
IQR = Q3-Q1
df1=df[((df['price_per_sqft']>=Q1-1.5*IQR)&(df['price_per_sqft']<=Q3+1.5*IQR))]
print(df1)

3.Use zscore of 3 to remove outliers. This is quite similar to IQR and you will get
exact same result
from scipy import stats
z=np.abs(stats.zscore(df1['price_per_sqft']))
df1=df1[(z<3)]
print(df1)

(4) for the data set height_weight.csv
import numpy as np
import pandas as pd
from scipy import stats
import seaborn as sns
df = pd.read_csv("height_weight.csv")
print(df)

(i) Using IQR detect weight outliers and print them
median=df['weight'].quantile(0.5)
Q1 = df['weight'].quantile(0.25)
Q3 = df['weight'].quantile(0.75)
IQR = Q3-Q1
df1=df[((df['weight']>=Q1-1.5*IQR)&(df['weight']<=Q3+1.5*IQR))]
print(df1)

(ii) Using IQR, detect height outliers and print them
median=df['height'].quantile(0.5)
Q1 = df['height'].quantile(0.25)
Q3 = df['height'].quantile(0.75)
IQR = Q3-Q1
low=Q1-1.5*IQR
high=Q3+1.5*IQR
df1=df[((df['height']>=low)&(df['height']<=high))]
print(df1)

# Output:
![image](https://user-images.githubusercontent.com/95179990/227202897-cdfb3fc6-0538-4d31-9c27-e0c554a69deb.png)
![image](https://user-images.githubusercontent.com/95179990/227203827-22d70253-f5b9-4b28-a656-b981d6df6e06.png)
![image](https://user-images.githubusercontent.com/95179990/227203957-074396e0-07c8-4f23-990a-e025feee533e.png)
![image](https://user-images.githubusercontent.com/95179990/227204107-1380ef41-1b7a-476e-ba2d-447260b4548a.png)
![image](https://user-images.githubusercontent.com/95179990/227204454-43c780b6-1d88-45de-af63-531fe39d6051.png)
![image](https://user-images.githubusercontent.com/95179990/227204815-51bafd22-e480-4255-8b72-f4bf4f05765d.png)

![image](https://user-images.githubusercontent.com/95179990/227204747-950f9833-38c0-44c2-b7f2-f5183d164889.png)





