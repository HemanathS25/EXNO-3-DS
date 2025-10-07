## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
 import pandas as pd
 df=pd.read_csv("Encoding Data.csv")
 df
```
<img width="507" height="414" alt="Screenshot 2025-10-07 154932" src="https://github.com/user-attachments/assets/aeee6d7b-c900-4cbf-b990-3c48c89d40c9" />
```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])

```
<img width="252" height="196" alt="image" src="https://github.com/user-attachments/assets/be419114-4ea2-4c6d-bffd-987afccb50b2" />
```
 df['bo2']=e1.fit_transform(df[["ord_2"]])
 df
```
<img width="524" height="413" alt="image" src="https://github.com/user-attachments/assets/7c9db8c8-eed6-4671-a6ac-9ba3be2057ca" />
```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
<img width="563" height="418" alt="image" src="https://github.com/user-attachments/assets/30ae1028-df9e-4af8-bff8-64e673715ba7" />
```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
df2=pd.concat([df2,enc],axis=1)
df2
```

<img width="618" height="432" alt="image" src="https://github.com/user-attachments/assets/04750d7f-b24b-4773-b18b-6786ab83dd12" />
```
 pd.get_dummies(df2,columns=["nom_0"])
```

<img width="821" height="365" alt="image" src="https://github.com/user-attachments/assets/8cacc8f4-75b9-404f-bc89-43543d74feba" />
```
pip install --upgrade category_encoders

```

<img width="1352" height="365" alt="image" src="https://github.com/user-attachments/assets/c1c5cbdb-22c1-4587-8a0c-e4832314c3cc" />
```
 from category_encoders import BinaryEncoder
 df=pd.read_csv("data.csv")
 df
```

<img width="728" height="411" alt="image" src="https://github.com/user-attachments/assets/e2626830-4042-4d50-8d47-6f0985acc196" />
```
 be=BinaryEncoder()
 nd=be.fit_transform(df['Ord_2'])
 df
```

<img width="662" height="412" alt="image" src="https://github.com/user-attachments/assets/22c26c31-9505-4b3b-bcd5-532777b1d620" />
```
 dfb=pd.concat([df,nd],axis=1)
 dfb
```

<img width="796" height="432" alt="image" src="https://github.com/user-attachments/assets/61e0294e-1c6b-4dce-bf94-6ac5e3ba2c42" />
```
 from category_encoders import TargetEncoder
 te=TargetEncoder()
 CC=df.copy()
 new=te.fit_transform(X=CC["City"],y=CC["Target"])
 CC=pd.concat([CC,new],axis=1)
 CC
```

<img width="687" height="418" alt="image" src="https://github.com/user-attachments/assets/5c96cf80-c71d-4eb1-aebc-69a83c062f01" />
```
 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("Data_to_Transform.csv")
 df

```

<img width="979" height="468" alt="image" src="https://github.com/user-attachments/assets/0210127f-8ffb-4b16-b438-56d90eccad77" />
```
 df.skew()
```

<img width="443" height="212" alt="image" src="https://github.com/user-attachments/assets/f141e6a9-a86d-4ed6-95f4-3220a470a75a" />
```
 np.log(df["Highly Positive Skew"])
```

<img width="398" height="461" alt="image" src="https://github.com/user-attachments/assets/28888d88-4eff-41c1-848a-11658f583e8e" />
```
np.reciprocal(df["Moderate Positive Skew"])
```

<img width="399" height="462" alt="image" src="https://github.com/user-attachments/assets/b5c992f5-79d7-41af-adfd-41f12850e534" />
```
 np.sqrt(df["Highly Positive Skew"])
```

<img width="427" height="467" alt="image" src="https://github.com/user-attachments/assets/f934fc32-9a9c-4ead-8d40-04217a6abe41" />
```
 np.square(df["Highly Positive Skew"])
```

<img width="393" height="451" alt="image" src="https://github.com/user-attachments/assets/f6acecba-0f21-4a2c-aedf-b0acb722f7bc" />
```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```

<img width="1082" height="469" alt="image" src="https://github.com/user-attachments/assets/840df137-6ff3-4ed0-af87-5996b8aaced5" />
```
 df.skew()
```

<img width="413" height="244" alt="image" src="https://github.com/user-attachments/assets/6d3bcc0b-6cca-4a64-95c6-af637450ef90" />
```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()
```

<img width="448" height="288" alt="image" src="https://github.com/user-attachments/assets/acdbdd2e-9cb5-4b03-9b07-b5896aad442f" />
```
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal')
 df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 df
```

<img width="1514" height="513" alt="image" src="https://github.com/user-attachments/assets/c886c070-31b3-4ea9-8984-8be66ab64648" />
```
 import seaborn as sns
 import statsmodels.api as sm
 import matplotlib.pyplot as plt
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()
```

<img width="748" height="457" alt="image" src="https://github.com/user-attachments/assets/46f972db-b78a-4137-9468-cc55b66b9431" />
```
 sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
 plt.show()
```

<img width="745" height="454" alt="image" src="https://github.com/user-attachments/assets/907e4056-497b-4d14-8ed2-0cf3445d34d7" />
```
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()
```

<img width="833" height="458" alt="image" src="https://github.com/user-attachments/assets/b96e3150-d505-4087-ac6a-991a442d6a02" />
```
 df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
 sm.qqplot(df["Highly Negative Skew"],line='45')
 plt.show()
```

<img width="754" height="450" alt="image" src="https://github.com/user-attachments/assets/431b77a8-e022-48ec-ae0c-a26f5a0b2d17" />
```
dt=pd.read_csv("titanic_dataset.csv")
dt
```

<img width="1335" height="481" alt="image" src="https://github.com/user-attachments/assets/54503587-c0a8-4700-ab30-3b438231d591" />
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt["Age_1"]=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt['Age'],line='45') 
plt.show()
```

<img width="740" height="455" alt="image" src="https://github.com/user-attachments/assets/3caa1f86-afab-447a-b58f-c96f0b717e84" />
```
 sm.qqplot(df["Highly Negative Skew_1"],line='45')
 plt.show()
```

<img width="827" height="460" alt="image" src="https://github.com/user-attachments/assets/47cbc271-6283-4761-a098-17bb7ec951a6" />

# RESULT:

 Thus the given data, Feature Encoding, Transformation process and save the data to a file
 was performed successfully

       
