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
```
Name:MARELLA HASINI

Reg No:212223240083
```
```
import pandas as pd
exp=pd.read_csv("/content/SAMPLEIDS.csv")
exp.head()
```

![image](https://github.com/user-attachments/assets/c6a84086-88b9-4c92-87d3-0da0fef40c22)

```
exp.head(5)
```
![image](https://github.com/user-attachments/assets/623da8ea-48dc-459b-a7da-1f94de210131)

```
exp.tail(5)
```
![image](https://github.com/user-attachments/assets/bae6b6cf-2671-4bef-9f13-d3bc0ab31cf8)

```
exp.isnull().sum()
```
![image](https://github.com/user-attachments/assets/11cafd75-8dda-435a-8f46-4a2a95c62abc)

```
exp.isnull().any()
```
![image](https://github.com/user-attachments/assets/08993dca-eb25-4488-a40b-8fc1668a2838)

```
exp.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/041f0ea6-6030-4a1c-b0ca-3c6eee248b9b)

![image](https://github.com/user-attachments/assets/0984f81a-3e2e-423e-a156-30331028d7ab)

```
exp.fillna(50)
```
![image](https://github.com/user-attachments/assets/63dd4505-8952-4284-ab10-aa99b743086e)

![image](https://github.com/user-attachments/assets/b6061196-c97f-4a66-b8ca-0d67f81c1ce3)

```
exp.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/bc03a320-dd35-4d77-80a2-f98b5f4cf82a)

![image](https://github.com/user-attachments/assets/7874a207-7a1b-4943-8a84-0855441f7ff6)

```
exp.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/8aa12dfb-c830-49aa-ac4b-5e0be68e83f7)

```
lab.fillna({'GENDER':'MALE','NAME':'PRAKASH','ADDRESS':'POONAMALEE','M1':'50','M2':'89','M3':'75','M4':'82','TOTAL':'896','AVG':'89.00000'})
```
![image](https://github.com/user-attachments/assets/1b02e0ae-accb-4728-b787-5aad7d360e5e)

```
exp=pd.read_csv("/content/iris.csv")
exp
```
![image](https://github.com/user-attachments/assets/fbd1ef1a-4cda-4949-8e4c-d190fa5d6351)

```
lab.describe()
```
![image](https://github.com/user-attachments/assets/bef8f811-36ab-4e7f-bbb0-8bd8ca8e5c2b)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=lab)
```
![image](https://github.com/user-attachments/assets/ed471a98-21ef-47ec-bf23-b46f7dd75905)

```
q1=lab.sepal_width.quantile(0.25)
q3=lab.sepal_width.quantile(0.75)
iq=q3-q1
print(iq)
```
![image](https://github.com/user-attachments/assets/cbcc3301-28b0-48ea-a970-ea6053bbf32b)

```
rid=lab[((lab.sepal_width<(q1-1.5*iq))|(lab.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/d28c0937-992b-4f62-a27f-97e024e0d059)

```
depo=lab[~((lab.sepal_width<(q1-1.5*iq))|(lab.sepal_width>(q3+1.5*iq)))]
depo
```
![image](https://github.com/user-attachments/assets/537c49fc-7535-476c-9d43-2504d991b062)

```
sns.boxplot(x='sepal_width',data=depo)
```
![image](https://github.com/user-attachments/assets/e93c6054-522b-4860-baa9-c9ea904a4bb0)

```
import numpy as np
import scipy.stats as stats
z = np.abs(stats.zscore(lab.sepal_width))
z
```
![image](https://github.com/user-attachments/assets/b12bca86-3276-4bf9-bdcf-722beaaef020)

```
p=lab[z<2]
p
```
![image](https://github.com/user-attachments/assets/153084b9-b5b5-4f23-a4b8-8c43a4be9364)
# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
