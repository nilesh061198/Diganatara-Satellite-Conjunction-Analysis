# Exploratory Data Analysis

In exploratory data analysis, we explore and understand data 


```python
# Importing required Modules 
import pandas as pd
import numpy as np
import openpyxl
```


```python
df=pd.read_excel("TSA_Data.xlsx")
```


```python
# checking datasets first 5 entries
df.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NORAD_CAT_ID_1</th>
      <th>OBJECT_NAME_1</th>
      <th>Operational Status</th>
      <th>Object_1_Status</th>
      <th>DSE_1</th>
      <th>NORAD_CAT_ID_2</th>
      <th>OBJECT_NAME_2</th>
      <th>Column1</th>
      <th>Object_2_Status</th>
      <th>DSE_2</th>
      <th>TCA</th>
      <th>TCA_RANGE</th>
      <th>TCA_RELATIVE_SPEED</th>
      <th>MAX_PROB</th>
      <th>DILUTION</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>55363</td>
      <td>STARLINK-5648 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>0.252</td>
      <td>25157</td>
      <td>GFO [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>0.305</td>
      <td>2023-11-10 09:20:13.523</td>
      <td>0.032</td>
      <td>13.577</td>
      <td>0.026140</td>
      <td>0.014</td>
    </tr>
    <tr>
      <th>1</th>
      <td>57621</td>
      <td>STARLINK-30150 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.884</td>
      <td>31659</td>
      <td>FENGYUN 1C DEB [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>5.951</td>
      <td>2023-11-15 19:11:49.982</td>
      <td>0.010</td>
      <td>14.376</td>
      <td>0.021270</td>
      <td>0.005</td>
    </tr>
    <tr>
      <th>2</th>
      <td>55410</td>
      <td>STARLINK-5633 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>7.385</td>
      <td>34898</td>
      <td>IRIDIUM 33 DEB [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>7.013</td>
      <td>2023-11-17 03:12:47.117</td>
      <td>0.038</td>
      <td>14.588</td>
      <td>0.011630</td>
      <td>0.021</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49145</td>
      <td>STARLINK-3119 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>4.188</td>
      <td>89483</td>
      <td>UNKNOWN [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>10.194</td>
      <td>2023-11-14 07:36:15.695</td>
      <td>0.046</td>
      <td>14.019</td>
      <td>0.009261</td>
      <td>0.022</td>
    </tr>
    <tr>
      <th>4</th>
      <td>43762</td>
      <td>STPSAT-5 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.108</td>
      <td>55274</td>
      <td>STARLINK-5236 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.716</td>
      <td>2023-11-15 06:32:02.487</td>
      <td>0.072</td>
      <td>4.631</td>
      <td>0.007325</td>
      <td>0.018</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Checking datasets last five entries 
df.tail(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NORAD_CAT_ID_1</th>
      <th>OBJECT_NAME_1</th>
      <th>Operational Status</th>
      <th>Object_1_Status</th>
      <th>DSE_1</th>
      <th>NORAD_CAT_ID_2</th>
      <th>OBJECT_NAME_2</th>
      <th>Column1</th>
      <th>Object_2_Status</th>
      <th>DSE_2</th>
      <th>TCA</th>
      <th>TCA_RANGE</th>
      <th>TCA_RELATIVE_SPEED</th>
      <th>MAX_PROB</th>
      <th>DILUTION</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>68004</th>
      <td>7530</td>
      <td>OSCAR 7 (AO-7) [P]</td>
      <td>[P]</td>
      <td>Partially Operational</td>
      <td>5.381</td>
      <td>11694</td>
      <td>COSMOS 1159 [?]</td>
      <td>[?]</td>
      <td>Unknown</td>
      <td>5.324</td>
      <td>2023-11-15 06:51:48.759</td>
      <td>4.282</td>
      <td>14.230</td>
      <td>2.202000e-08</td>
      <td>2.992</td>
    </tr>
    <tr>
      <th>68005</th>
      <td>46288</td>
      <td>FLOCK 4V-8 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>7.413</td>
      <td>19822</td>
      <td>AKEBONO (EXOS-D) [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>7.024</td>
      <td>2023-11-17 03:58:54.516</td>
      <td>4.347</td>
      <td>15.485</td>
      <td>2.030000e-08</td>
      <td>3.008</td>
    </tr>
    <tr>
      <th>68006</th>
      <td>39418</td>
      <td>SKYSAT-A [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>1.376</td>
      <td>26548</td>
      <td>TIUNGSAT-1 (MO-46) [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>1.392</td>
      <td>2023-11-11 12:27:18.194</td>
      <td>3.789</td>
      <td>13.612</td>
      <td>1.997000e-08</td>
      <td>1.688</td>
    </tr>
    <tr>
      <th>68007</th>
      <td>7530</td>
      <td>OSCAR 7 (AO-7) [P]</td>
      <td>[P]</td>
      <td>Partially Operational</td>
      <td>4.784</td>
      <td>7681</td>
      <td>COSMOS 714 [?]</td>
      <td>[?]</td>
      <td>Unknown</td>
      <td>4.726</td>
      <td>2023-11-14 16:31:11.081</td>
      <td>4.515</td>
      <td>14.260</td>
      <td>1.986000e-08</td>
      <td>3.153</td>
    </tr>
    <tr>
      <th>68008</th>
      <td>46290</td>
      <td>FLOCK 4V-5 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.971</td>
      <td>25520</td>
      <td>PAN SAT (PO-34) [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>5.747</td>
      <td>2023-11-15 21:36:30.337</td>
      <td>4.808</td>
      <td>13.335</td>
      <td>1.884000e-08</td>
      <td>1.992</td>
    </tr>
  </tbody>
</table>
</div>



Counting Satelite based on oparational Status of Object 1


```python
#Getting total number of Operational Sat from Object_1
def g(df):
    return df['Object_1_Status'].value_counts()['Operational']
No_Of_Operational_Sat_1 = g(df.copy())
print("Total Number of operational Satelites are:" ,No_Of_Operational_Sat_1)
```

    Total Number of operational Satelites are: 66408
    


```python
#Getting total number of Partially Operational Sat from Object_1
def g(df):
    return df['Object_1_Status'].value_counts()['Partially Operational']
No_Of_Partially_Operational_Sat_1 = g(df.copy())
print("Total Number of Partially Operational Satelites are:" ,No_Of_Partially_Operational_Sat_1)
```

    Total Number of Partially Operational Satelites are: 1365
    


```python
#Getting total number of Standby  Sat from Object_1
def g(df):
    return df['Object_1_Status'].value_counts()['StandBy']
No_Of_StandBy_Sat_1 = g(df.copy())
print("Total Number of Stand by Satelites are:" ,No_Of_StandBy_Sat_1)
```

    Total Number of Stand by Satelites are: 100
    


```python
#Getting total number of Extended Mission   Sat from Object_1
def g(df):
    return df['Object_1_Status'].value_counts()['Extended Mission']
No_Of_Extended_Mission_Sat_1 = g(df.copy())
print("Total Number of Extended Mission Satelites are:" ,No_Of_Extended_Mission_Sat_1)
```

    Total Number of Extended Mission Satelites are: 136
    

Counting Satelite based on oparational Status of Object 2


```python
#Getting total number of  Operational Sat from Object_2
def g(df):
    return df['Object_2_Status'].value_counts()['Operational']
No_Of_Operational_Sat_2 = g(df.copy())
print("Total Number of Partially Operational Satelites are:" ,No_Of_Operational_Sat_2)
```

    Total Number of Partially Operational Satelites are: 27895
    


```python
#Getting total number of Partially Operational Sat from Object_2
def g(df):
    return df['Object_2_Status'].value_counts()['Partially Operational']
No_Of_Partially_Operational_Sat_2 = g(df.copy())
print("Total Number of Partially Operational Satelites are:" ,No_Of_Partially_Operational_Sat_2)
```

    Total Number of Partially Operational Satelites are: 491
    


```python
#Getting total number of Non Operational Sat from Object_2
def g(df):
    return df['Object_2_Status'].value_counts()['Non Operational']
No_Of_Non_Operational_Sat_2 = g(df.copy())
print("Total Number of Partially Operational Satelites are:" ,No_Of_Non_Operational_Sat_2)
```

    Total Number of Partially Operational Satelites are: 36374
    


```python
#Getting total number of Extended Mission   Sat from Object_2
def g(df):
    return df['Object_2_Status'].value_counts()['Extended Mission']
No_Of_Extended_Mission_Sat_2 = g(df.copy())
print("Total Number of Extended Mission Satelites are:" ,No_Of_Extended_Mission_Sat_2)
```

    Total Number of Extended Mission Satelites are: 3
    


```python
#Getting total number of Unknown Status   Sat from Object_2
def g(df):
    return df['Object_2_Status'].value_counts()['Unknown']
No_Of_Unknown_Sat_2 = g(df.copy())
print("Total Number of Extended Mission Satelites are:" ,No_Of_Unknown_Sat_2)
```

    Total Number of Extended Mission Satelites are: 3246
    


```python
#sorting data to get the satelite who has maximum probability forconjunction
data=df.sort_values(by='MAX_PROB', ascending=False)
data
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NORAD_CAT_ID_1</th>
      <th>OBJECT_NAME_1</th>
      <th>Operational Status</th>
      <th>Object_1_Status</th>
      <th>DSE_1</th>
      <th>NORAD_CAT_ID_2</th>
      <th>OBJECT_NAME_2</th>
      <th>Column1</th>
      <th>Object_2_Status</th>
      <th>DSE_2</th>
      <th>TCA</th>
      <th>TCA_RANGE</th>
      <th>TCA_RELATIVE_SPEED</th>
      <th>MAX_PROB</th>
      <th>DILUTION</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>55363</td>
      <td>STARLINK-5648 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>0.252</td>
      <td>25157</td>
      <td>GFO [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>0.305</td>
      <td>2023-11-10 09:20:13.523</td>
      <td>0.032</td>
      <td>13.577</td>
      <td>2.614000e-02</td>
      <td>0.014</td>
    </tr>
    <tr>
      <th>1</th>
      <td>57621</td>
      <td>STARLINK-30150 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.884</td>
      <td>31659</td>
      <td>FENGYUN 1C DEB [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>5.951</td>
      <td>2023-11-15 19:11:49.982</td>
      <td>0.010</td>
      <td>14.376</td>
      <td>2.127000e-02</td>
      <td>0.005</td>
    </tr>
    <tr>
      <th>2</th>
      <td>55410</td>
      <td>STARLINK-5633 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>7.385</td>
      <td>34898</td>
      <td>IRIDIUM 33 DEB [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>7.013</td>
      <td>2023-11-17 03:12:47.117</td>
      <td>0.038</td>
      <td>14.588</td>
      <td>1.163000e-02</td>
      <td>0.021</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49145</td>
      <td>STARLINK-3119 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>4.188</td>
      <td>89483</td>
      <td>UNKNOWN [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>10.194</td>
      <td>2023-11-14 07:36:15.695</td>
      <td>0.046</td>
      <td>14.019</td>
      <td>9.261000e-03</td>
      <td>0.022</td>
    </tr>
    <tr>
      <th>4</th>
      <td>43762</td>
      <td>STPSAT-5 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.108</td>
      <td>55274</td>
      <td>STARLINK-5236 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.716</td>
      <td>2023-11-15 06:32:02.487</td>
      <td>0.072</td>
      <td>4.631</td>
      <td>7.325000e-03</td>
      <td>0.018</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>68004</th>
      <td>7530</td>
      <td>OSCAR 7 (AO-7) [P]</td>
      <td>[P]</td>
      <td>Partially Operational</td>
      <td>5.381</td>
      <td>11694</td>
      <td>COSMOS 1159 [?]</td>
      <td>[?]</td>
      <td>Unknown</td>
      <td>5.324</td>
      <td>2023-11-15 06:51:48.759</td>
      <td>4.282</td>
      <td>14.230</td>
      <td>2.202000e-08</td>
      <td>2.992</td>
    </tr>
    <tr>
      <th>68005</th>
      <td>46288</td>
      <td>FLOCK 4V-8 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>7.413</td>
      <td>19822</td>
      <td>AKEBONO (EXOS-D) [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>7.024</td>
      <td>2023-11-17 03:58:54.516</td>
      <td>4.347</td>
      <td>15.485</td>
      <td>2.030000e-08</td>
      <td>3.008</td>
    </tr>
    <tr>
      <th>68006</th>
      <td>39418</td>
      <td>SKYSAT-A [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>1.376</td>
      <td>26548</td>
      <td>TIUNGSAT-1 (MO-46) [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>1.392</td>
      <td>2023-11-11 12:27:18.194</td>
      <td>3.789</td>
      <td>13.612</td>
      <td>1.997000e-08</td>
      <td>1.688</td>
    </tr>
    <tr>
      <th>68007</th>
      <td>7530</td>
      <td>OSCAR 7 (AO-7) [P]</td>
      <td>[P]</td>
      <td>Partially Operational</td>
      <td>4.784</td>
      <td>7681</td>
      <td>COSMOS 714 [?]</td>
      <td>[?]</td>
      <td>Unknown</td>
      <td>4.726</td>
      <td>2023-11-14 16:31:11.081</td>
      <td>4.515</td>
      <td>14.260</td>
      <td>1.986000e-08</td>
      <td>3.153</td>
    </tr>
    <tr>
      <th>68008</th>
      <td>46290</td>
      <td>FLOCK 4V-5 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.971</td>
      <td>25520</td>
      <td>PAN SAT (PO-34) [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>5.747</td>
      <td>2023-11-15 21:36:30.337</td>
      <td>4.808</td>
      <td>13.335</td>
      <td>1.884000e-08</td>
      <td>1.992</td>
    </tr>
  </tbody>
</table>
<p>68009 rows × 15 columns</p>
</div>




```python
#sorting data to get the satelite who has minimum probability forconjunction
data_=df.sort_values(by='MAX_PROB', ascending=True)
data_
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NORAD_CAT_ID_1</th>
      <th>OBJECT_NAME_1</th>
      <th>Operational Status</th>
      <th>Object_1_Status</th>
      <th>DSE_1</th>
      <th>NORAD_CAT_ID_2</th>
      <th>OBJECT_NAME_2</th>
      <th>Column1</th>
      <th>Object_2_Status</th>
      <th>DSE_2</th>
      <th>TCA</th>
      <th>TCA_RANGE</th>
      <th>TCA_RELATIVE_SPEED</th>
      <th>MAX_PROB</th>
      <th>DILUTION</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>68008</th>
      <td>46290</td>
      <td>FLOCK 4V-5 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.971</td>
      <td>25520</td>
      <td>PAN SAT (PO-34) [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>5.747</td>
      <td>2023-11-15 21:36:30.337</td>
      <td>4.808</td>
      <td>13.335</td>
      <td>1.884000e-08</td>
      <td>1.992</td>
    </tr>
    <tr>
      <th>68007</th>
      <td>7530</td>
      <td>OSCAR 7 (AO-7) [P]</td>
      <td>[P]</td>
      <td>Partially Operational</td>
      <td>4.784</td>
      <td>7681</td>
      <td>COSMOS 714 [?]</td>
      <td>[?]</td>
      <td>Unknown</td>
      <td>4.726</td>
      <td>2023-11-14 16:31:11.081</td>
      <td>4.515</td>
      <td>14.260</td>
      <td>1.986000e-08</td>
      <td>3.153</td>
    </tr>
    <tr>
      <th>68006</th>
      <td>39418</td>
      <td>SKYSAT-A [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>1.376</td>
      <td>26548</td>
      <td>TIUNGSAT-1 (MO-46) [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>1.392</td>
      <td>2023-11-11 12:27:18.194</td>
      <td>3.789</td>
      <td>13.612</td>
      <td>1.997000e-08</td>
      <td>1.688</td>
    </tr>
    <tr>
      <th>68005</th>
      <td>46288</td>
      <td>FLOCK 4V-8 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>7.413</td>
      <td>19822</td>
      <td>AKEBONO (EXOS-D) [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>7.024</td>
      <td>2023-11-17 03:58:54.516</td>
      <td>4.347</td>
      <td>15.485</td>
      <td>2.030000e-08</td>
      <td>3.008</td>
    </tr>
    <tr>
      <th>68004</th>
      <td>7530</td>
      <td>OSCAR 7 (AO-7) [P]</td>
      <td>[P]</td>
      <td>Partially Operational</td>
      <td>5.381</td>
      <td>11694</td>
      <td>COSMOS 1159 [?]</td>
      <td>[?]</td>
      <td>Unknown</td>
      <td>5.324</td>
      <td>2023-11-15 06:51:48.759</td>
      <td>4.282</td>
      <td>14.230</td>
      <td>2.202000e-08</td>
      <td>2.992</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>43762</td>
      <td>STPSAT-5 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.108</td>
      <td>55274</td>
      <td>STARLINK-5236 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.716</td>
      <td>2023-11-15 06:32:02.487</td>
      <td>0.072</td>
      <td>4.631</td>
      <td>7.325000e-03</td>
      <td>0.018</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49145</td>
      <td>STARLINK-3119 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>4.188</td>
      <td>89483</td>
      <td>UNKNOWN [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>10.194</td>
      <td>2023-11-14 07:36:15.695</td>
      <td>0.046</td>
      <td>14.019</td>
      <td>9.261000e-03</td>
      <td>0.022</td>
    </tr>
    <tr>
      <th>2</th>
      <td>55410</td>
      <td>STARLINK-5633 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>7.385</td>
      <td>34898</td>
      <td>IRIDIUM 33 DEB [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>7.013</td>
      <td>2023-11-17 03:12:47.117</td>
      <td>0.038</td>
      <td>14.588</td>
      <td>1.163000e-02</td>
      <td>0.021</td>
    </tr>
    <tr>
      <th>1</th>
      <td>57621</td>
      <td>STARLINK-30150 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>5.884</td>
      <td>31659</td>
      <td>FENGYUN 1C DEB [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>5.951</td>
      <td>2023-11-15 19:11:49.982</td>
      <td>0.010</td>
      <td>14.376</td>
      <td>2.127000e-02</td>
      <td>0.005</td>
    </tr>
    <tr>
      <th>0</th>
      <td>55363</td>
      <td>STARLINK-5648 [+]</td>
      <td>[+]</td>
      <td>Operational</td>
      <td>0.252</td>
      <td>25157</td>
      <td>GFO [-]</td>
      <td>[-]</td>
      <td>Non Operational</td>
      <td>0.305</td>
      <td>2023-11-10 09:20:13.523</td>
      <td>0.032</td>
      <td>13.577</td>
      <td>2.614000e-02</td>
      <td>0.014</td>
    </tr>
  </tbody>
</table>
<p>68009 rows × 15 columns</p>
</div>




```python

```
