# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output:

NAME : SUDHARSANA KUMAR S R

Reg.No: 212223240162
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```

![image](https://github.com/user-attachments/assets/2b0c2d4c-d811-4b81-9455-fe855853e2d9)

df.isnull().sum()


![image](https://github.com/user-attachments/assets/34d4e035-f08e-4a74-b7e8-ee24c364c105)



df.isnull().any()


![Screenshot 2024-08-20 110815](https://github.com/user-attachments/assets/29aa8a52-ae85-4c83-af0c-53020af2bad6)


df.dropna()


![image](https://github.com/user-attachments/assets/bb4354d6-51f4-4335-b452-64f025ab828f)


df.fillna(0)


![image](https://github.com/user-attachments/assets/42428e60-2dc2-4166-9f3e-deb228cac412)


df.fillna(method = 'ffill')


![image](https://github.com/user-attachments/assets/6da1edf5-80a6-4e96-a553-c7ec4641db78)


df.fillna(method = 'bfill')


![image](https://github.com/user-attachments/assets/bfdab012-a1e2-402b-8a4b-fd7d175a3884)

```
df_dropped = df.dropna()
df_dropped
```

![image](https://github.com/user-attachments/assets/d827ed07-63f4-4d25-b7a0-7b67b5f77eb9)


df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})


![image](https://github.com/user-attachments/assets/7a79c290-301e-44a6-91a5-5e823aedbd3c)

## IQR(Inter Quartile Range)
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```

![image](https://github.com/user-attachments/assets/2e79ff09-8c59-4a6e-92f6-1fbbea31f9df)


ir.describe()


![image](https://github.com/user-attachments/assets/eecf47cb-08aa-4168-8c97-35cf6c917403)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/user-attachments/assets/0b0d2549-bd0c-41c1-8e21-dd3e67b52471)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/fbd54de6-8e05-4d14-9fa7-f080c79b1045)


```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```


![image](https://github.com/user-attachments/assets/5a9623b7-740e-4507-be58-18d1386902f4)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

![image](https://github.com/user-attachments/assets/ca937a8b-cee1-4304-8f64-67032c08e737)

sns.boxplot(x='sepal_width',data=delid)


![image](https://github.com/user-attachments/assets/c98c3833-204c-4bd4-a583-8b9355e54aa9)


## Z-Score

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

dataset=pd.read_csv("heights.csv")
dataset
```

![image](https://github.com/user-attachments/assets/84983d1f-268c-4cfa-b293-33458800bea1)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```

![image](https://github.com/user-attachments/assets/b3742686-e2d1-4b0a-b906-7600a95c58cc)

```
low = q1 - 1.5*iqr
low
```

![image](https://github.com/user-attachments/assets/ea77383c-11a6-4821-a8bd-c5005dba19f1)

```
high = q3 + 1.5*iqr
high
```

![image](https://github.com/user-attachments/assets/bea5e76f-c7f9-4bff-85e6-23cf2454d417)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![image](https://github.com/user-attachments/assets/448fd880-ceb2-42bb-86a8-a5aadc7b4fe0)

```
z = np.abs(stats.zscore(df['height']))
z
```

![image](https://github.com/user-attachments/assets/42e6ae13-a795-47a9-8d32-2c64f0a68fde)

```
df1 = df[z<3]
df1
```

![image](https://github.com/user-attachments/assets/d5fb167b-fff9-48fa-b25c-e65fd149678f)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.

