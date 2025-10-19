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
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt 
import seaborn as sns
df = pd.read_csv(r"C:\Users\acer\Downloads\titanic_dataset (3).csv")  
print("\nFirst 5 Rows:")
print(df.head())
```

<img width="897" height="582" alt="Screenshot 2025-10-16 084834" src="https://github.com/user-attachments/assets/ae0511bb-80cd-49c5-aa8d-3b1615d19cf0" /> 

```
print("\nMissing Values:")
print(df.isnull().sum()) 
```

<img width="277" height="398" alt="Screenshot 2025-10-16 084952" src="https://github.com/user-attachments/assets/2ed65575-f2f3-4163-94ef-9be8cbd3af00" /> 

```
print("\nSummary Statistics:")
print(df.describe(include='all').T)
```

<img width="850" height="749" alt="Screenshot 2025-10-16 085159" src="https://github.com/user-attachments/assets/b1fd82e2-c6c3-4e68-96d5-41975c899e39" /> 

```
plt.figure(figsize=(6,4))
sns.countplot(x='Survived', data=df) 
plt.title("Survival Count (0 = Not Survived, 1 = Survived)")
plt.show()
```

<img width="918" height="616" alt="Screenshot 2025-10-16 085358" src="https://github.com/user-attachments/assets/f105b043-b63b-4304-8395-774277095fe9" /> 

```
plt.figure(figsize=(6,4))
sns.countplot(x='Sex', data=df) 
plt.title("Passenger Gender Distribution")
plt.show() 
```

<img width="984" height="638" alt="Screenshot 2025-10-16 085508" src="https://github.com/user-attachments/assets/6c6936e9-5c88-4dd8-8ed6-0da935ae0114" /> 

```
plt.figure(figsize=(6,4))
sns.countplot(x='Pclass', data=df) 
plt.title("Passenger Class Distribution")
plt.show() 
```

<img width="1033" height="616" alt="Screenshot 2025-10-16 085639" src="https://github.com/user-attachments/assets/c16506de-e7e3-4da9-bcb1-d05e49a23f89" />

```
plt.figure(figsize=(6,4))
sns.countplot(x='Sex', hue='Survived', data=df, palette='pastel')
plt.title("Survival Rate by Gender")
plt.show() 
```

<img width="994" height="646" alt="Screenshot 2025-10-16 085758" src="https://github.com/user-attachments/assets/e6d4218d-a77d-4a08-ad3c-14b30c0fee46" /> 

```
plt.figure(figsize=(6,4))
sns.countplot(x='Pclass', hue='Survived', data=df, palette='cool')
plt.title("Survival Rate by Passenger Class")
plt.show() 
```

<img width="997" height="627" alt="Screenshot 2025-10-16 085951" src="https://github.com/user-attachments/assets/a109c63d-3f58-4bfb-8149-1872498e9e07" /> 

```
plt.figure(figsize=(8,4))
sns.histplot(df[df['Survived']==1]['Age'].dropna(), color='green', label='Survived', kde=True)
sns.histplot(df[df['Survived']==0]['Age'].dropna(), color='red', label='Not Survived', kde=True)
plt.legend()
plt.title("Age Distribution by Survival")
plt.show() 
```

<img width="1191" height="610" alt="Screenshot 2025-10-16 090142" src="https://github.com/user-attachments/assets/6cf853aa-f1bd-461c-bd28-5a04c87e3c06" /> 

```
plt.figure(figsize=(8,6))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='Blues')
plt.title("Correlation Heatmap")
plt.show() 
```

<img width="1183" height="751" alt="Screenshot 2025-10-16 090324" src="https://github.com/user-attachments/assets/5d8f3669-123d-411e-a732-886b765969cf" /> 

```
print("\nSurvival rate by gender:")
print(df.groupby('Sex')['Survived'].mean()) 
```

<img width="1115" height="158" alt="Screenshot 2025-10-16 090512" src="https://github.com/user-attachments/assets/217e53ff-ff55-4d06-a8b8-3e67fed86585" /> 

```
print("\nSurvival rate by class:")
print(df.groupby('Pclass')['Survived'].mean()) 
```

<img width="1015" height="181" alt="Screenshot 2025-10-16 090707" src="https://github.com/user-attachments/assets/224a2fc7-0c2f-4fbd-b5bb-955d48dc108d" /> 

```
print("\nAverage Age by Class:")
print(df.groupby('Pclass')['Age'].mean()) 
```

<img width="1000" height="188" alt="Screenshot 2025-10-16 090912" src="https://github.com/user-attachments/assets/05f2c245-d1bc-4821-8802-bd81f95b2638" /> 

```
numeric_cols = df.select_dtypes(include=[np.number]).columns
for col in numeric_cols:
    plt.figure(figsize=(6,2))
    sns.boxplot(x=df[col], color='skyblue')
    plt.title(f"Boxplot of {col}")
    plt.show() 
```

<img width="1297" height="744" alt="Screenshot 2025-10-16 091104" src="https://github.com/user-attachments/assets/08f1a2cc-2e65-4b4d-9c7a-b1c5962f3d92" /> 

<img width="1374" height="751" alt="Screenshot 2025-10-16 091137" src="https://github.com/user-attachments/assets/83d2a1c4-c8e8-46bc-a954-81aa80d4cade" /> 

<img width="1082" height="900" alt="Screenshot 2025-10-16 091320" src="https://github.com/user-attachments/assets/7b0a941c-054b-404d-936d-4656d6531871" /> 


# RESULT
        we performed exploratory data analysis on the given data set 
