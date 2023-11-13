# ODD2023-Datascience-Ex-04
# MULTIVARIATE ANALYSIS
## AIM:
To perform Multivariate EDA on the given data set.
## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
## ALGORITHM:
### STEP 1:
Import the built-in libraries required to perform EDA and outlier removal.

### STEP 2:
Read the given CSV file (titanic dataset).

### STEP 3:
Convert the file into a DataFrame and get information about the data.

### STEP 4:
Return the objects containing counts of unique values using value_counts().

### STEP 5:
Plot the counts in the form of a Histogram or Bar Graph.

### STEP 6:
Use Seaborn to view the bar graph comparison of data.

### STEP 7:
Find the pairwise correlation of all columns in the DataFrame using dataframe.corr().

### STEP 8:
Save the final dataset into the file.
## PROGRAM:
```
Name : Sabitha P
Register Number : 212222040137
```
# CODE:
```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

dt=pd.read_csv("/content/titanic_dataset.csv")
dt

dt.info()

dt.shape

dt.set_index("PassengerId",inplace=True)

dt

dt.describe()

dt.nunique()

dt['Survived'].value_counts()

per=(dt['Survived'].value_counts()/dt.shape[0]*100).round(2)
per

#UNIVARIATE ANALYSIS
sns.countplot(data=dt,x="Survived")

fig, ax1 =plt.subplots(figsize=(5,5))
graph=sns.countplot(ax=ax1,x='Survived',data=dt)
graph.set_xticklabels(graph.get_xticklabels(),rotation=90)
for p in graph.patches:
  height=p.get_height()
  graph.text(p.get_x()+p.get_width()/2.,height+0.1,height,ha="center")

dt

dt.Pclass.unique()

dt.rename(columns={'Sex':'Gender'},inplace=True)
dt

#BIVARIATE ANALYSIS
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)

sns.catplot(x="Survived",hue="Gender",data=dt,kind="count")

fig, ax1 =plt.subplots(figsize=(8,5))
graph=sns.countplot(ax=ax1,data=dt,x='Survived',hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height=p.get_height()
  graph.text(p.get_x()+p.get_width()/2.,height+20.8,height,ha="center")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x=dt["Age"],y=dt["Fare"])

sns.jointplot(x="Age",y="Fare",data=dt)

#MULTIVARIATE ANALYSIS
fig,ax1 =plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x="Pclass",y="Age",hue="Gender",data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")

g=sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax=g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()-0.01,p.get_height()*1.02,"{0:.1f}".format(p.get_height()),color="red",rotation="horizontal",size="small")

##Co-Relation
corr=dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)

```

# OUTPUT:
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/79902a6c-c3fc-4a5d-bd61-70317717c112)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/02efd7be-0b1b-4620-8c11-929152f98f42)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/2c34e9be-9f40-4aed-96cf-ca0fd562a18a)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/7146dbb3-61b7-4d14-a564-5dbac36288f9)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/be4ba758-7c5d-4a95-b1b5-b215a20a8d0f)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/6a2bd4bf-743e-49c6-86c3-64a3b72007b7)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/bc7a61ff-8320-4848-909a-eabf52aee0fa)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/58944952-55be-4dba-9a95-0ef8e2aac872)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/9dab6afd-ee23-4791-b5ed-06bdbd0f4d4c)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/f9e76146-9883-4999-870f-56871c3891d2)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/2049ade6-f042-419d-b131-54d8ae38097e)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/c5752da9-19d6-44ed-9a9c-838044cff2e2)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/b792c82b-4474-44be-aca4-3775a7c763ec)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/7cca8901-077a-4a2f-8af1-670e976ad033)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/6428cf3f-563b-4635-a2e7-67ae4fbf2fd2)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/9ce4af19-0d83-479a-970a-453a007c8f39)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/847b1861-e8eb-44ac-890f-4bd1e44b20fc)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/2de28d22-8890-47d3-8f9e-abfa807bce45)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/edf09207-6433-4794-aad4-e84fc35cc3c5)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/b5a46ca3-9a53-42b2-9a88-a4a60437da42)
![image](https://github.com/sabithapaulraj/ODD2023-Datascience-Ex-04/assets/118343379/53af4c70-c436-4cdf-b83f-ccc4f6191bc5)

## RESULT:
Thus we have read the given dataset and performed multivariate analysis using different kinds of plots
