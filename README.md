# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
      from google.colab import drive
drive.mount('/content/drive')

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

ls drive/MyDrive/titanic_dataset.csv

df=pd.read_csv('drive/MyDrive/titanic_dataset.csv')
df
![Screenshot 2024-12-12 143731](https://github.com/user-attachments/assets/ee794a5d-cee9-41ad-a5c3-ae9c6bf00edf)

df.info()
![Screenshot 2024-12-12 143831](https://github.com/user-attachments/assets/429cc9db-2748-4112-93fb-aebe72354995)

df.set_index('PassengerId',inplace=True)
df.describe()
![Screenshot 2024-12-12 143911](https://github.com/user-attachments/assets/f3aa9244-1099-4fde-a9ad-97d516c75c18)

df.shape
![Screenshot 2024-12-12 143934](https://github.com/user-attachments/assets/3f17e60e-c85d-4b7c-b8c6-f068d641c944)

df.nunique()
![Screenshot 2024-12-12 143944](https://github.com/user-attachments/assets/b129da84-55c5-43c8-ba98-fcc757e36ef3)


df['Survived'].value_counts()
![Screenshot 2024-12-12 144022](https://github.com/user-attachments/assets/7a278b27-06b4-455f-a1c8-235cc8fa9f86)

per=(df['Survived'].value_counts()/df.shape[0]*100).round(2)
per
![Screenshot 2024-12-12 144027](https://github.com/user-attachments/assets/35a2bb47-2dec-4052-bf33-38b11dc8aa90)

sns.countplot(data=df,x='Survived')

![Screenshot 2024-12-12 144115](https://github.com/user-attachments/assets/54e3eeb3-3d1f-4809-8412-c4f17fd62861)
df
![Screenshot 2024-12-12 144136](https://github.com/user-attachments/assets/2e2102d3-7b9d-40ae-851a-649224a50b04)

df.Pclass.unique()
![Screenshot 2024-12-12 144237](https://github.com/user-attachments/assets/caaf771d-9cee-4087-b8f4-efa547b4fe85)

df.rename(columns={'Sex':'Gender'},inplace=True)

sns.catplot(x='Gender',col='Survived',kind='count',data=df,height=5,aspect=.7)
![Screenshot 2024-12-12 144313](https://github.com/user-attachments/assets/fc20936c-efda-4da5-8e51-6476c61ffcd1)

sns.catplot(x='Survived',hue='Gender',data=df,kind='count')
![Screenshot 2024-12-12 144320](https://github.com/user-attachments/assets/9188ce2b-9f2b-422b-a1b1-4792d388ed49)
df.boxplot(column='Age',by='Survived')
![Screenshot 2024-12-12 144434](https://github.com/user-attachments/assets/e97b4087-0b34-4c0f-8559-a1ee56a6f4be)

sns.scatterplot(x=df['Age'],y=df['Fare'])
![Screenshot 2024-12-12 144444](https://github.com/user-attachments/assets/2a096009-9e68-4577-9b09-6b66450bed55)
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)
![Screenshot 2024-12-12 144527](https://github.com/user-attachments/assets/74901eeb-8f0e-45bc-a98c-44558b10ed91)

sns.catplot(data=df,col='Survived',x='Gender',hue='Pclass',kind='count')
![Screenshot 2024-12-12 144538](https://github.com/user-attachments/assets/64152499-b4e1-4e16-88c8-c4088dd90d22)

numeric_df=df.select_dtypes(include=np.number)
corr=numeric_df.corr()
sns.heatmap(corr,annot=True)
![Screenshot 2024-12-12 144615](https://github.com/user-attachments/assets/735c24de-d058-41a2-b8e4-99965c9a7e6b)

sns.pairplot(df)
![Screenshot 2024-12-12 144627](https://github.com/user-attachments/assets/1efbc719-5f5f-439e-a8f5-2a010547a243)

# RESULT
      exp no2 was successfully completed
