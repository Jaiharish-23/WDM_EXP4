### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07/02/2026
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

## Program 1:
```python
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

df=pd.read_csv('/content/clustervisitor.csv')

cluster={'Young':(df['Age']<=30),'Middle':((df['Age'])>30 & (df['Age']<=50)),'Old':(df['Age']>50)}
count=[]
for group,condition in cluster.items():
  visitors=df[condition]
  count.append(len(visitors))
  print(f"The Visitors on {group} are")
  print(visitors)
  print("count =",len(visitors))

```

### Output:

<img width="497" height="724" alt="image" src="https://github.com/user-attachments/assets/4c37fbfa-6809-4e00-93d8-923178c199cc" />

### Visualization:
```python
plt.figure(figsize=(8, 6))
plt.bar(['Young','Middle','Old'], count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:

<img width="935" height="575" alt="image" src="https://github.com/user-attachments/assets/5971251b-a06a-4d24-b9e4-1a9975839d37" />

## Program 2:
```python
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

df=pd.read_csv('/content/clustervisitor.csv')

cluster={'Young':(df['Age']<=30),'Middle':((df['Age'])>30 & (df['Age']<=50)),'Old':(df['Age']>50)}

df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
K=KMeans(n_clusters=4,random_state=23)
df3['cluster']=K.fit_predict(newdf)
df3

```

### Output:

<img width="352" height="818" alt="image" src="https://github.com/user-attachments/assets/39fc5507-92a0-4f9d-be43-27a7617863ba" />


### Visualization:
```python
plt.figure(figsize=(8,6))
plt.scatter(x=df3['Age'],y=df3['Income'],c= df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('Kmeans Cluster')
plt.show()
```
### Output:

<img width="771" height="463" alt="image" src="https://github.com/user-attachments/assets/e31ea2af-5950-4ed4-acb1-347926235cdf" />


### Result:

Thus, cluster and Visitor Segmentation for Navigation patterns have been implemented successfully.
