---
title: Better graphs for academic studies with matplotlib
author: Muhittin Babaoglu
date: ''
slug: 
categories: ["scientific figures", "matplotlib"]
tags: [""]
math: true
header:
  caption: ''
  image: ''
---
Many research papers suffer from lack of neat figures to convey their key points. In order to elevate emphasis of study, vigorous and tidy illustrations are needed to employed. To print elegant looking figures for scientific studies, matplotlib offers numerious tools to enhance figures. Once the template of plots are created, every figure that is plotted with matplotlib will obey the template you've created. This is fast and well-structured approach to produce necessary figures for your study.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

df1 = pd.read_csv('x-y.csv', sep=',', header=None, names=["x", "y"]) #to get exemplary data set from an excel document

data_sets = [df1] #if you have more than one dataset to print in different figure

for item in data_sets:
    item["$x^2$"]=item["x"]**2 #create another data set which is square of x

data_sets = [df1]
```


```python
df1 #print df1 dataset
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
      <th>x</th>
      <th>y</th>
      <th>$x^2$</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13</td>
      <td>348</td>
      <td>169</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15</td>
      <td>457</td>
      <td>225</td>
    </tr>
    <tr>
      <th>2</th>
      <td>15</td>
      <td>48</td>
      <td>225</td>
    </tr>
    <tr>
      <th>3</th>
      <td>19</td>
      <td>511</td>
      <td>361</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24</td>
      <td>591</td>
      <td>576</td>
    </tr>
    <tr>
      <th>5</th>
      <td>28</td>
      <td>1049</td>
      <td>784</td>
    </tr>
    <tr>
      <th>6</th>
      <td>29</td>
      <td>766</td>
      <td>841</td>
    </tr>
    <tr>
      <th>7</th>
      <td>34</td>
      <td>1367</td>
      <td>1156</td>
    </tr>
    <tr>
      <th>8</th>
      <td>35</td>
      <td>2047</td>
      <td>1225</td>
    </tr>
    <tr>
      <th>9</th>
      <td>37</td>
      <td>1740</td>
      <td>1369</td>
    </tr>
    <tr>
      <th>10</th>
      <td>40</td>
      <td>1848</td>
      <td>1600</td>
    </tr>
    <tr>
      <th>11</th>
      <td>41</td>
      <td>2923</td>
      <td>1681</td>
    </tr>
    <tr>
      <th>12</th>
      <td>43</td>
      <td>2474</td>
      <td>1849</td>
    </tr>
    <tr>
      <th>13</th>
      <td>45</td>
      <td>2691</td>
      <td>2025</td>
    </tr>
    <tr>
      <th>14</th>
      <td>53</td>
      <td>4498</td>
      <td>2809</td>
    </tr>
    <tr>
      <th>15</th>
      <td>54</td>
      <td>4083</td>
      <td>2916</td>
    </tr>
    <tr>
      <th>16</th>
      <td>58</td>
      <td>5071</td>
      <td>3364</td>
    </tr>
    <tr>
      <th>17</th>
      <td>59</td>
      <td>4995</td>
      <td>3481</td>
    </tr>
    <tr>
      <th>18</th>
      <td>66</td>
      <td>6899</td>
      <td>4356</td>
    </tr>
    <tr>
      <th>19</th>
      <td>71</td>
      <td>7316</td>
      <td>5041</td>
    </tr>
    <tr>
      <th>20</th>
      <td>74</td>
      <td>8136</td>
      <td>5476</td>
    </tr>
    <tr>
      <th>21</th>
      <td>77</td>
      <td>9248</td>
      <td>5929</td>
    </tr>
    <tr>
      <th>22</th>
      <td>80</td>
      <td>9544</td>
      <td>6400</td>
    </tr>
    <tr>
      <th>23</th>
      <td>83</td>
      <td>10266</td>
      <td>6889</td>
    </tr>
    <tr>
      <th>24</th>
      <td>84</td>
      <td>10526</td>
      <td>7056</td>
    </tr>
    <tr>
      <th>25</th>
      <td>89</td>
      <td>12586</td>
      <td>7921</td>
    </tr>
    <tr>
      <th>26</th>
      <td>95</td>
      <td>13832</td>
      <td>9025</td>
    </tr>
    <tr>
      <th>27</th>
      <td>98</td>
      <td>15525</td>
      <td>9604</td>
    </tr>
  </tbody>
</table>
</div>




```python
result1 = plt.figure(figsize=(10,10)) #determine size of figure

result1 = plt.plot(df1["x"], df1["y"], 'b-', label='data', linewidth=1, marker='o')
result1 = plt.plot(df1["x"], df1["$x^2$"], 'r-', label='$x^2$', linewidth=1, linestyle='--')

plt.rc('font', family='Arial') #font of entire plot
plt.rc('xtick',labelsize=14) #size of values on the x-axis
plt.rc('ytick',labelsize=14) #size of values on the y-axis

plt.title("$x^2$ vs. data", fontsize=14) #title and title size 

plt.xlabel('x',fontsize=14)
plt.ylabel('y',fontsize=14)
plt.grid(False) #remove grid in the plot
plt.legend(fontsize=14)

#plt.xscale('log') #convert x-axis to log scale
#plt.yscale('log')

plt.show()
```


![plot1](../../img/plot1.png)