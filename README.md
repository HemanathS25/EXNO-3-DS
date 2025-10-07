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

 import pandas as pd
 df=pd.read_csv("Encoding Data.csv")
 df

<img width="483" height="455" alt="image" src="https://github.com/user-attachments/assets/359f878c-0032-4f35-b653-ff1db8aa49e2" />

 from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
 pm=['Hot','Warm','Cold']
 e1=OrdinalEncoder(categories=[pm])
 e1.fit_transform(df[["ord_2"]])

<img width="238" height="246" alt="image" src="https://github.com/user-attachments/assets/93d584b9-4f6e-4d8f-b398-6710068f4798" />


 df['bo2']=e1.fit_transform(df[["ord_2"]])
 df

<img width="561" height="452" alt="image" src="https://github.com/user-attachments/assets/fc91292e-0441-4929-babb-7035d0de3989" />


 le=LabelEncoder()
 dfc=df.copy()
 dfc['ord_2']=le.fit_transform(dfc['ord_2'])
 dfc

<img width="562" height="454" alt="image" src="https://github.com/user-attachments/assets/03996d9d-5bae-4c50-8945-c831b12840a2" />


from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
df2=pd.concat([df2,enc],axis=1)
df2


<img width="712" height="464" alt="image" src="https://github.com/user-attachments/assets/0a922fe6-568d-4e24-989f-accc17969270" />


 pd.get_dummies(df2,columns=["nom_0"])


<img width="900" height="444" alt="image" src="https://github.com/user-attachments/assets/ea7e541f-bf39-4bf3-9085-1966c754790d" />



 from category_encoders import BinaryEncoder
 df=pd.read_csv("data.csv")
 df


<img width="711" height="464" alt="image" src="https://github.com/user-attachments/assets/4120f8a3-a02f-4b0d-ba51-b0f9a3873b4c" />


 be=BinaryEncoder()
 nd=be.fit_transform(df['Ord_2'])
 df

<img width="755" height="447" alt="image" src="https://github.com/user-attachments/assets/2c58ad1a-2892-40af-9628-3b34f3153f38" />


 dfb=pd.concat([df,nd],axis=1)
 dfb

<img width="989" height="446" alt="image" src="https://github.com/user-attachments/assets/42dfdc10-69bf-4c92-8b56-528cc9b43b1d" />


 from category_encoders import TargetEncoder
 te=TargetEncoder()
 CC=df.copy()
 new=te.fit_transform(X=CC["City"],y=CC["Target"])
 CC=pd.concat([CC,new],axis=1)
 CC


<img width="794" height="434" alt="image" src="https://github.com/user-attachments/assets/871e2869-4d25-48d5-be31-17d689b0bd80" />


 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("Data_to_Transform.csv")
 df


<img width="1074" height="499" alt="image" src="https://github.com/user-attachments/assets/f10a2e8c-9f21-4a6a-889a-eb2575e60bfc" />


 df.skew()

<img width="534" height="251" alt="image" src="https://github.com/user-attachments/assets/e5beab54-7f45-41bc-a0fe-56d3ee29f266" />


 np.log(df["Highly Positive Skew"])


<img width="414" height="524" alt="image" src="https://github.com/user-attachments/assets/b855cc4e-35c9-4c16-81ba-299f67cb21b4" />


 np.reciprocal(df["Moderate Positive Skew"])


<img width="456" height="584" alt="image" src="https://github.com/user-attachments/assets/24d9310f-4e52-4957-9372-5901cb4dd1be" />


 np.sqrt(df["Highly Positive Skew"])

<img width="435" height="570" alt="image" src="https://github.com/user-attachments/assets/2b778b1a-3ef6-42a7-871a-5ba2d57d218f" />


np.square(df["Highly Positive Skew"])


<img width="454" height="572" alt="image" src="https://github.com/user-attachments/assets/ac4900ef-cb30-4147-99c5-502962edcad3" />



 df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
 df

<img width="1400" height="516" alt="image" src="https://github.com/user-attachments/assets/c06c7695-8623-4e64-9fb2-06a7521a31cf" />


 df.skew()


<img width="572" height="305" alt="image" src="https://github.com/user-attachments/assets/b9f2bf8d-db13-41c2-9821-db261366db43" />


 df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
 df.skew()


<img width="559" height="335" alt="image" src="https://github.com/user-attachments/assets/4173f7db-3347-45c2-bd8f-b5af81d8962c" />



from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df

<img width="1775" height="558" alt="image" src="https://github.com/user-attachments/assets/0d70a0dc-5a69-492a-a1da-2c3d2bd59a95" />



 import seaborn as sns
 import statsmodels.api as sm
 import matplotlib.pyplot as plt
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()

<img width="876" height="561" alt="image" src="https://github.com/user-attachments/assets/8cf6c084-60e6-4c3a-80b4-0d94e183e760" />


 sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
 plt.show()


<img width="854" height="562" alt="image" src="https://github.com/user-attachments/assets/ca48332c-0ded-4040-88e0-d36b0c6c04f1" />


 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()


<img width="839" height="558" alt="image" src="https://github.com/user-attachments/assets/eccca7ec-f02d-4aaa-b987-62656f960ebe" />


 dt=pd.read_csv("titanic_dataset.csv")
 dt

<img width="1538" height="532" alt="image" src="https://github.com/user-attachments/assets/83d6a7ac-9c36-4fe5-85e7-1bf9105141a4" />


 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 dt["Age_1"]=qt.fit_transform(dt[["Age"]])
 sm.qqplot(dt['Age'],line='45')
 plt.show()

<img width="831" height="553" alt="image" src="https://github.com/user-attachments/assets/69b6b390-bd5a-4830-88da-3f7881992c61" />


sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()

<img width="853" height="560" alt="image" src="https://github.com/user-attachments/assets/baf65357-67db-40cc-bec9-6833e0bfc2d1" />




# RESULT:
 Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully
