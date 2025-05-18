# Exno:1
Data Cleaning Process

### NAME: SAJITH AHAMED F
### REG NO.: 212223240144

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
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![Screenshot 2025-03-13 102744](https://github.com/user-attachments/assets/51690ea2-12de-4ee4-b2fd-976ac39dd63c)

```
df.isnull().sum()
```
![Screenshot 2025-03-13 102750](https://github.com/user-attachments/assets/468b60c5-6b6e-4b1a-a3eb-7cb676729ddd)

```
df.isnull().any()
```
![Screenshot 2025-03-13 102756](https://github.com/user-attachments/assets/894301cc-13a4-4bc1-889f-49c0e699eefa)

```
df.dropna()
```
![Screenshot 2025-03-13 102805](https://github.com/user-attachments/assets/61c12178-b8a1-4595-ac79-eda44daaa677)

```
df.fillna(0)
```
![Screenshot 2025-03-13 102815](https://github.com/user-attachments/assets/166be8e3-9b27-4af5-b635-64794ec80de7)

```
df.fillna(method = "ffill")
```
![Screenshot 2025-03-13 102822](https://github.com/user-attachments/assets/a8f7e022-34d7-4626-9ffd-45cd7159f7ce)

```
df.fillna(method = "bfill")
```
![Screenshot 2025-03-13 102832](https://github.com/user-attachments/assets/a77a8ba0-f3b9-41f7-88e1-1424caa2c046)

```
df_dropped = df.dropna()
df_dropped
```
![Screenshot 2025-03-13 102838](https://github.com/user-attachments/assets/dafc29d9-8287-42f4-9c7f-1b67cde803b0)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot 2025-03-13 102845](https://github.com/user-attachments/assets/d6b6be13-5dc3-4dbb-9028-a141234a2bcc)

```
df.describe()
```
![Screenshot 2025-03-13 102852](https://github.com/user-attachments/assets/45c97e57-56b1-4590-b04a-0ba0db39e9da)

```
import seaborn as sns
import pandas as pd
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![Screenshot 2025-03-13 102857](https://github.com/user-attachments/assets/51f8f970-0b5f-4dda-baf8-14e29d2cb4f6)

```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![Screenshot 2025-03-13 102903](https://github.com/user-attachments/assets/4182ace4-2fcc-4a59-a7c0-165afd6c3d0f)

```
lb=q1-1.5*iqr
ub=q3+1.5*iqr
lb
```
![Screenshot 2025-03-13 102910](https://github.com/user-attachments/assets/869b9ef1-fb2c-484a-90e3-33d73a90a632)

```
ub
```
![Screenshot 2025-03-13 102915](https://github.com/user-attachments/assets/9c1cbb10-620b-4d91-a4fa-ea4b3aa63da0)

```
af=af[((af>=lb)&(af<=ub))]
af
```
![Screenshot 2025-03-13 102920](https://github.com/user-attachments/assets/0fab3b68-7066-4e9d-8fe0-ea834223f5d1)

```
af.dropna()
```
![Screenshot 2025-03-13 102926](https://github.com/user-attachments/assets/96b36319-52ff-47dd-a033-e1e7020c1ddd)

```
sns.boxplot(data=af)
```
![Screenshot 2025-03-13 102933](https://github.com/user-attachments/assets/ca0a8d54-e081-4cb7-a798-4576f4bac76b)

```
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![Screenshot 2025-03-13 103034](https://github.com/user-attachments/assets/1b8b3299-5a8e-4abb-a594-ef0dfefd8b87)

```
from scipy import stats
import numpy as np
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![Screenshot 2025-03-13 103040](https://github.com/user-attachments/assets/2c2f80ce-e63d-4415-880a-84809597e396)

```
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,258]
out=[]
def d_o(val):
    ts=3
    m=np.mean(val)
    sd=np.std(val)
    for i in val:
        z=(i-m)/sd
        if np.abs(z)>ts:
            out.append(i)
    return out
op=d_o(val)
op
```
![Screenshot 2025-03-13 103046](https://github.com/user-attachments/assets/9143f24b-dafa-4757-b45d-80047334d33a)

# Result
Thus, the Data Cleaning Process is executed Successfully.
