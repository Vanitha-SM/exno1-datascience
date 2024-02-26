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

# Coding and Output
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/adeed988-0f22-4477-aa1f-fc0767f58229)
```
data = pd.get_dummies(data)
data.isnull().sum()
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/16a9d857-c8ed-412f-b196-7e83fbc27639)
```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/a140ef65-d5d0-4e5d-bb99-edb3ee4c67db)
```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/2aa701f0-302e-4f12-acfe-4c08d4891b83)
# IQR 
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/b6163966-c207-4ebe-b859-26fc1f31c052)
```
ir.describe()
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/790ec93f-9b41-45f8-9a3c-8eecbd7b5878)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/fa475df8-36e0-4a3d-9d95-895486097f62)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/7c7de03a-8c19-4629-adee-d2f8ddfc7550)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/c891d33a-411a-43cb-88bb-0614d0cbfbaa)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/7f10012d-255b-42c7-88fb-7f49c0bf4e3e)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/d94161ba-b61b-43aa-b3f7-3c9f352eda00)
# Z Score

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/f01f125b-7c8e-4fba-9a31-6c09ef3b6974)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)

```

# Result
Thus the given data is read,cleansed and the cleaned data is saved into the file.

