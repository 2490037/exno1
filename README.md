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
~~~
import pandas as pd  
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
~~~
# OUTPUT
<img width="932" height="788" alt="Screenshot 2026-01-31 105827" src="https://github.com/user-attachments/assets/d029166f-d48a-4f53-bad8-c42107694971" />

~~~
df.head()
~~~
# OUTPUT
<img width="951" height="283" alt="Screenshot 2026-01-31 105856" src="https://github.com/user-attachments/assets/38837885-86e4-4c67-bcd2-0ef41a5cc9fa" />

~~~
df.tail()
~~~
# OUTPUT
<img width="935" height="242" alt="Screenshot 2026-01-31 105906" src="https://github.com/user-attachments/assets/e49ce696-b6d7-48b3-91d0-75cdc52015dc" />

~~~
df.info()
~~~
# OUTPUT
<img width="807" height="389" alt="Screenshot 2026-01-31 105917" src="https://github.com/user-attachments/assets/4bc2d2aa-1d62-4472-ad76-ea0ae0f6683e" />

~~~
df.describe()
~~~
# OUTPUT
<img width="950" height="344" alt="Screenshot 2026-01-31 105925" src="https://github.com/user-attachments/assets/34e4e83c-f125-45e5-b234-bb0459a02d87" />

~~~
df.isnull().sum()
~~~
# OUTPUT
<img width="395" height="503" alt="Screenshot 2026-01-31 105936" src="https://github.com/user-attachments/assets/84112705-c5dd-4a3d-b936-3afa7e446c37" />

~~~
df.isnull().any()
~~~
# OUTPUT
<img width="671" height="495" alt="Screenshot 2026-01-31 105949" src="https://github.com/user-attachments/assets/9d3364cb-9724-4b7c-b071-f4c87ea0009c" />

~~~
df.dropna()
~~~
# OUTPUT
<img width="991" height="497" alt="Screenshot 2026-01-31 105957" src="https://github.com/user-attachments/assets/b5372460-03fd-4461-a5ed-dc17e2043a1a" />

~~~
df.fillna(0)
~~~
# OUTPUT
<img width="1077" height="750" alt="Screenshot 2026-01-31 110132" src="https://github.com/user-attachments/assets/c92dad55-8599-4345-8cd0-6f2e88bf5c8c" />

~~~
df.fillna(method='ffill')
~~~
# OUTPUT
<img width="1394" height="782" alt="Screenshot 2026-01-31 110157" src="https://github.com/user-attachments/assets/68a9b307-eb16-4808-95f0-d5a47ff084ef" />

~~~
df.fillna({'GENDER':'MALE','NAME':'SRI'})
~~~
# OUTPUT
<img width="1070" height="750" alt="Screenshot 2026-01-31 110209" src="https://github.com/user-attachments/assets/ef1d6c91-d81e-4a68-bbcb-ba1216a7581a" />

~~~
ir=pd.read_csv("/content/iris.csv")

ir
~~~
# OUTPUT
<img width="795" height="467" alt="Screenshot 2026-01-31 110218" src="https://github.com/user-attachments/assets/8f08a911-758e-4ddb-bd16-7c03aa60d5cd" />

~~~
ir.describe()
~~~
# OUTPUT
<img width="690" height="326" alt="Screenshot 2026-01-31 110228" src="https://github.com/user-attachments/assets/b8a3f554-937d-4e0c-bcaa-7f659f40e141" />

~~~
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
~~~
# OUTPUT
<img width="790" height="545" alt="Screenshot 2026-01-31 110235" src="https://github.com/user-attachments/assets/066b3558-7666-422e-9dd9-568b8c03194c" />

~~~
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
(IQR)=Q3-Q1
print(IQR)
~~~
# OUTPUT
<img width="541" height="146" alt="Screenshot 2026-01-31 110242" src="https://github.com/user-attachments/assets/75ad7efc-85c9-472e-b48b-3f52b976115c" />

~~~
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
~~~
# OUTPUT
<img width="697" height="267" alt="Screenshot 2026-01-31 110248" src="https://github.com/user-attachments/assets/6aa28794-8572-41dc-bb9c-55dfcb9b4b1e" />

~~~
ran=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
~~~
# OUTPUT
<img width="781" height="518" alt="Screenshot 2026-01-31 110257" src="https://github.com/user-attachments/assets/bc600a30-dd92-40f3-a356-7c278ea5840f" />

~~~
sns.boxplot(x='sepal_width',data=ran)
~~~
# OUTPUT
<img width="736" height="507" alt="Screenshot 2026-01-31 110306" src="https://github.com/user-attachments/assets/c6213908-9b32-4cca-9568-fc9557b3e041" />

~~~
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['petal_length']))
z
~~~
# OUTPUT
<img width="857" height="630" alt="Screenshot 2026-01-31 110315" src="https://github.com/user-attachments/assets/940d2c44-1785-48fb-a810-e3508e2aecb5" />
~~~
ir1=ir[z<3]
ir1
~~~
# OUTPUT

<img width="763" height="525" alt="Screenshot 2026-01-31 110328" src="https://github.com/user-attachments/assets/020cfab1-6d38-4db9-920a-70884479a996" />

# Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
