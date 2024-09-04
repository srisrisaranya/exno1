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
**DATA CLEANING
```
```
import pandas as pd
data=pd.read_csv('//content/SAMPLEIDS.csv')
data.head()
```
![image](https://github.com/user-attachments/assets/e77abcf8-19d2-441c-b688-ed2ed36e2181)

```
data = pd.get_dummies(data)
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/ac09c1d4-d9e4-4fa8-841a-41e3e9c2f0d1)
![image](https://github.com/user-attachments/assets/1133b602-c117-4c7a-9304-46595fa6bd41)

```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/b2a7544b-84c5-4a9a-96b0-1b711bd6f29b)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/999d6d6b-7a34-479d-b721-46b3258a44a7)

```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/e70e4922-03ff-470a-9ebf-eb60812ccb12)

```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/aad0862a-a1a8-4a09-8b4c-8751559d4d87)

```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/a2fc18ab-635a-41d0-9949-51cfcdc15a12)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/9c29b056-f500-4365-afed-09631b1187dd)

```
df.fillna({'GENDER':'FEMALE','NAME':'SABEEHA','ADDRESS':'CHITTOOR','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/3d88fff2-9fa0-4c2b-81cb-8364dae1bd60)
```
**IQR(Inter Quartile Range)
```
```
import pandas as pd
ir = pd.read_csv('//content/iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/e3f85f2e-33c5-4c0b-9c68-7746bf687817)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/d42be625-ad5d-4a5a-9c2a-33f6ad7c50a7)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/7042d2c9-fc31-4090-9bcc-58a1fdd78174)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq = c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/a509489b-fb8c-4204-8862-d60ad310e5ff)
```
rid = ir[((ir.sepal_width < (c1 - 1.5 * iq)) | (ir.sepal_width > (c3 + 1.5 * iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/b3fcf995-ade7-4ac5-be96-2529c8d97a69)

```
delid =ir[~((ir.sepal_width < (c1 - 1.5 * iq)) | (ir.sepal_width > (c3 + 1.5 * iq)))]
delid
```
![image](https://github.com/user-attachments/assets/4930e4d7-e5ed-48c3-a766-cc855ac76ecf)
```
sns.boxplot(x='sepal_width', data=delid)
```
![image](https://github.com/user-attachments/assets/c0fcf1eb-365b-40a6-9637-df5e3630dfd0)
```
**Z-SCORE
```
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset = pd.read_csv('/content/heights.csv')
dataset
```
![image](https://github.com/user-attachments/assets/4214796d-fe15-4c0e-97df-df7f90dd842d)
```
df = pd.read_csv('/content/heights.csv')
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)

iqr = q3 - q1
iqr
```
![image](https://github.com/user-attachments/assets/4e599c17-2338-4826-bdde-fb6b36693b82)

```
low = q1 - 1.5 * iqr
low
```
![image](https://github.com/user-attachments/assets/b32919f0-c456-4eab-bb79-7c99ecef39e5)
```
high = q3 + 1.5 * iqr
high
```
![image](https://github.com/user-attachments/assets/8ca6d4ba-3957-4888-a3c6-67f824540756)

```
df1 = df[(df['height'] >= low) & (df['height'] <= high)]
df1
```
![image](https://github.com/user-attachments/assets/e472358f-7390-4af3-9119-9f2ad2ef045c)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/f5476b38-8b01-4905-b044-96ef168d5e21)
```
df1 = df[(z < 3)]
df1
```
![image](https://github.com/user-attachments/assets/a57f006a-fe7a-4acf-8462-9ab99c08b3c7)



# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
