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
import numpy as np
import pandas as pd
data=pd.read_csv("SAMPLEIDS.csv")
data
```
<img width="1102" height="844" alt="image" src="https://github.com/user-attachments/assets/ac509b3a-138f-4ab3-8149-134206b97716" />

```
data.head(4)
```
<img width="1101" height="213" alt="image" src="https://github.com/user-attachments/assets/624c1661-e944-4f19-8d38-ebaae14257e6" />

```
data.tail(7)
```
<img width="1055" height="318" alt="image" src="https://github.com/user-attachments/assets/13a5e11d-523b-4150-85e5-cc82912d103b" />

```
data.isnull()
```
<img width="999" height="838" alt="image" src="https://github.com/user-attachments/assets/3ac1513d-b1d1-45a6-8e52-d02ece9a857a" />

```
data.notnull()
```
<img width="907" height="854" alt="image" src="https://github.com/user-attachments/assets/8900e0a5-70af-4613-8784-b0ada9944862" />

```
data.isnull().sum()
```
<img width="343" height="281" alt="image" src="https://github.com/user-attachments/assets/4b3ce705-5c1d-46fa-8e6b-aa7049204c5d" />

```
data.isnull().any()
```
<img width="366" height="280" alt="image" src="https://github.com/user-attachments/assets/317cd533-21f0-46c8-b66f-5f5a0f4b0013" />

```
data.dropna(axis=1)
```
<img width="537" height="835" alt="image" src="https://github.com/user-attachments/assets/965074c3-dd03-45e1-827d-7f05a79f8d9a" />

```
data.dropna(axis=0)
```
<img width="1038" height="547" alt="image" src="https://github.com/user-attachments/assets/05779604-7e18-424a-bc79-5a272c086750" />

```
data.fillna(0)
```
<img width="1183" height="840" alt="image" src="https://github.com/user-attachments/assets/e4080386-dfb2-43bc-b2f3-e8fee3cbee45" />

```
data.fillna(method="ffill")
```
<img width="1057" height="842" alt="image" src="https://github.com/user-attachments/assets/3d172b09-12a2-4075-b74d-7714349bf7e9" />

```
data.bfill()
```
<img width="1016" height="849" alt="image" src="https://github.com/user-attachments/assets/3f2a1b17-8f17-4378-8721-8aa1cfce9aae" />

```
data.fillna({'REGNO':0, 'NAME':'PRAVEEN'})
```
<img width="1019" height="830" alt="image" src="https://github.com/user-attachments/assets/23908f44-415b-47b9-a36f-beff1b28f57e" />

```
ir=pd.read_csv("iris.csv")
ir
```
<img width="737" height="476" alt="image" src="https://github.com/user-attachments/assets/b87538fa-a354-4698-b520-82b1ff1debed" />

```
ir.describe()
```
<img width="648" height="357" alt="image" src="https://github.com/user-attachments/assets/205b64d2-fb96-4686-abf2-6702fc0cf863" />

```
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)
```

<img width="888" height="579" alt="image" src="https://github.com/user-attachments/assets/1417052c-c5ca-4d88-97fc-86ef172056a8" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="122" height="30" alt="image" src="https://github.com/user-attachments/assets/b77a2690-c7ec-4e4b-a8ed-7b4ee2b3b6ea" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="438" height="115" alt="image" src="https://github.com/user-attachments/assets/2328de16-b9bf-4a82-9956-a02d1ccb70f0" />

```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```
<img width="901" height="493" alt="image" src="https://github.com/user-attachments/assets/956b3570-c2c8-4cfe-87da-a37eb81e121e" />

```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="517" height="256" alt="image" src="https://github.com/user-attachments/assets/2df8c554-48a8-446c-b9a2-819aeab88583" />

```
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```
<img width="539" height="274" alt="image" src="https://github.com/user-attachments/assets/6f2ecfe1-0f49-49b8-ac9b-ea90a4df2329" />


# Result
 Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.         
