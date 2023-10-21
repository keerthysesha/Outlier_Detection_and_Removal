## Ex:2 - Outlier_Detection_and_Removal

## AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## ALGORITHM:
```
STEP 1:Read the given Data.
STEP 2:Get the information about the data.
STEP 3:Detect the Outliers using IQR method and Z score.
STEP 4:Remove the outliers:
STEP 5:Plot the datas using box plot.
```
## PROGRAM:
```
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
```
### removing ouliers of bhp.csv file using IQR
```
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)
```

### removing ouliers of bhp.csv file using Zscore of 3
```
from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)
```
### Using IQR detect height outliers and print them( height_weight.csv)
```
Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)
```

### Using IQR, detect weight outliers and print them( height_weight.csv)
```
Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
## OUTPUT:

# bhp.csv:
# df.head():

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/a236ddd7-53cd-405c-9b7a-25f6d428e14e)


# df.describe():

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/01fd831c-8ca0-4963-8912-f259c721bbd6)


# df.info():

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/f6da9a28-cdff-42e8-87bf-d3d778976e47)


# df.shape

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/1aaf3dec-2db5-4237-80e6-fb5a87858337)



# BOXPLOT BEFORE REMOVING OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/74d54c8b-dbc7-4145-8985-12106b2c81f9)

# NEWDATA USING IQR

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/88270c6a-7f7a-45f6-bfe7-d82a5f509b25)


# OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/a8e2b924-3258-466d-89a8-4b2cd45d4199)


# newdata.shape

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/dc1714f1-ce5b-4214-bdf5-5d903604ce4a)


# BOXPLOT AFTER REMOVING OUTLIERS USING IQR

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/3e954296-4a5d-4378-94ee-2c07227e1bdd)


# Zscore of 3
# NEWDATA USING Zscore

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/bc95a8b1-a8ee-41d6-97f5-9cce0107d8be)


# OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/1962a7eb-64ba-4541-8a10-064ce9b2601f)


# newdata2.shape

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/f4dd5ec3-1504-47a4-b6a2-c7dedc2bc6fb)


# BOXPLOT AFTER REMOVING OUTLIERS USING Zscore

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/ab26f66a-b7c0-4036-b4d6-e42a25c0fc24)


# height_weight.csv

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/5e34338c-0208-45f5-9371-6d6f0d7039c0)


# dataset.describe()

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/c04c46a5-07ea-4cfc-b2a4-a0c68ca63929)


# dataset.info()

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/9f942fd2-355a-43e2-831a-b7bc16481409)


# BOXPLOT BEFORE REMOVING OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/e62afc28-7448-45e4-af6e-f67fd5584711)


# HEIGHT OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/b40157d1-b587-4a08-9fb1-4ff2f4cb10a6)


# DATASET AFTER REMOVING HEIGHT OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/14179ba5-6f67-47bf-a33a-f6ee9e4db657)


# BOXPLOT AFTER REMOVING HEIGHT OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/0c8efb2b-e7cb-4f8e-9924-622c49655b38)


# WEIGHT OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/08229dbe-15d2-4afd-b08a-f2e02191eaf2)


# DATASET AFTER REMOVING WEIGHT OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/47ccc598-dee5-4157-a052-63e7898ccad4)

# BOXPLOT AFTER REMOVING WEIGHT OUTLIERS

![image](https://github.com/keerthysesha/Outlier_Detection_and_Removal/assets/125575936/6f809ace-c7de-450a-9bc9-8e148aac08d8)


RESULT:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
