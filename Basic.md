# Python Basics

Setup Jupyter Lab envirnoment.

**environment.yml**

```{yml}
name: jup_env
channels:
  - conda-forge
  - bioconda
  - defaults
dependencies:
  - python=3.8
  - pandas
  - jupyterlab
```

In bash:

```{bash}
conda env create -f environment.yml
conda activate jup_env
jupyter lab      # Starts browser notebook
```


```python
print("Hello World")
```

    Hello World


## Data Types

Data has to be stored in variables. Programming is basically moving and modifying variables.



```python
i = 5            # Integers 1, 2, 3, ...
f = 1.1          # Floats 1.1, 1.1111, 3.14
d = 1/3          # Doubles  1.3333333....
s = "hello"      # Strings
print(i) 
print(f)
print(d)
print(s)
```

    5
    1.1
    0.3333333333333333
    hello


List all data objects


```python
whos
```

    Variable   Type     Data/Info
    -----------------------------
    d          float    0.3333333333333333
    f          float    1.1
    i          int      5
    s          str      hello


## Reading and Writing Files

You will probably need to read or write files, probably a csv/tsv/txt. Use the `pandas` library to crate a data.frame.



```python
import pandas as pd
data = pd.read_csv("data/small.txt")  # read from a file
data.to_csv('data/new_small.csv')     # write to a file
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
      <th>color</th>
      <th>count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>red</td>
      <td>11</td>
    </tr>
    <tr>
      <th>1</th>
      <td>white</td>
      <td>22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>blue</td>
      <td>33</td>
    </tr>
    <tr>
      <th>3</th>
      <td>green</td>
      <td>44</td>
    </tr>
    <tr>
      <th>4</th>
      <td>purple</td>
      <td>55</td>
    </tr>
  </tbody>
</table>
</div>



The `data` object is a data frame, somewhat similar to R's data.frame.


```python
type(data) 
```




    pandas.core.frame.DataFrame




```python
data.columns    # equivalent to R's names(data)

```




    Index(['color', 'count'], dtype='object')




```python
whos
```

    Variable   Type         Data/Info
    ---------------------------------
    d          float        0.3333333333333333
    data       DataFrame        color  count\n0     r<...>     44\n4  purple     55
    f          float        1.1
    i          int          5
    pd         module       <module 'pandas' from '/U<...>ages/pandas/__init__.py'>
    s          str          hello


# Define your own python functions

Use the `def` keyword to create a function that takes input and gives output. Use functions to modify, combine, and compute on variables.


```python
def hello_function(name):
    print("Hello ", name, "!")
    
hello_function("Mark")
```

    Hello  Mark !


# Define your own python classes

The key idea of object-oriented programming is grouping data and methods in a data structure called a class. The class is like a blueprint for a house (before the house is built or before the data is assigned any value). The blueprint allocates memory on the computer (you don't need to know much about this). As soon as you create an object from the class (assign values to memory), then it's called an object.

Use the `class` keyword to create a class with internal data and functions (also referred to as methods):


```python
class MyPerson:
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def getAge(self):
        return("I am " + str(self.age) + " old.")
```


```python
mark = MyPerson("Mark", 40)         # Instantiate a class to create an object
mark.age                            # Access object data
mark.getAge()                       # Call a function of the object
```




    'I am 40 old.'



Python is an object-oriented language, so the general analysis pipeline is (1) import packages (2) creating objects and (3) calling object.functions(). 

Use `dir()` to view all attributes (internal data) and methods of an object. 


```python
dir(mark)
```




    ['__class__',
     '__delattr__',
     '__dict__',
     '__dir__',
     '__doc__',
     '__eq__',
     '__format__',
     '__ge__',
     '__getattribute__',
     '__gt__',
     '__hash__',
     '__init__',
     '__init_subclass__',
     '__le__',
     '__lt__',
     '__module__',
     '__ne__',
     '__new__',
     '__reduce__',
     '__reduce_ex__',
     '__repr__',
     '__setattr__',
     '__sizeof__',
     '__str__',
     '__subclasshook__',
     '__weakref__',
     'age',
     'getAge',
     'name']



Any attributes or methods that start with an underscore or private (or internal), do not use these. Use the other attributes ("age", "getAge", "name").

## Case Study: Gapminder

[add description of dataset here with link to sources]


```python
data = pd.read_csv("data/gapminder_all.csv", index_col=0 )

# data[1:10, 1:5]       # <= will NOT work!
data.iloc[1:10,1:5]     # iloc = integer location
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
      <th>gdpPercap_1952</th>
      <th>gdpPercap_1957</th>
      <th>gdpPercap_1962</th>
      <th>gdpPercap_1967</th>
    </tr>
    <tr>
      <th>continent</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Africa</th>
      <td>3520.610273</td>
      <td>3827.940465</td>
      <td>4269.276742</td>
      <td>5522.776375</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>1062.752200</td>
      <td>959.601080</td>
      <td>949.499064</td>
      <td>1035.831411</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>851.241141</td>
      <td>918.232535</td>
      <td>983.653976</td>
      <td>1214.709294</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>543.255241</td>
      <td>617.183465</td>
      <td>722.512021</td>
      <td>794.826560</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>339.296459</td>
      <td>379.564628</td>
      <td>355.203227</td>
      <td>412.977514</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>1172.667655</td>
      <td>1313.048099</td>
      <td>1399.607441</td>
      <td>1508.453148</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>1071.310713</td>
      <td>1190.844328</td>
      <td>1193.068753</td>
      <td>1136.056615</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>1178.665927</td>
      <td>1308.495577</td>
      <td>1389.817618</td>
      <td>1196.810565</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>1102.990936</td>
      <td>1211.148548</td>
      <td>1406.648278</td>
      <td>1876.029643</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.loc[:,"country":"gdpPercap_1962"].head()   # loc = label based location
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
      <th>country</th>
      <th>gdpPercap_1952</th>
      <th>gdpPercap_1957</th>
      <th>gdpPercap_1962</th>
    </tr>
    <tr>
      <th>continent</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Africa</th>
      <td>Algeria</td>
      <td>2449.008185</td>
      <td>3013.976023</td>
      <td>2550.816880</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>Angola</td>
      <td>3520.610273</td>
      <td>3827.940465</td>
      <td>4269.276742</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>Benin</td>
      <td>1062.752200</td>
      <td>959.601080</td>
      <td>949.499064</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>Botswana</td>
      <td>851.241141</td>
      <td>918.232535</td>
      <td>983.653976</td>
    </tr>
    <tr>
      <th>Africa</th>
      <td>Burkina Faso</td>
      <td>543.255241</td>
      <td>617.183465</td>
      <td>722.512021</td>
    </tr>
  </tbody>
</table>
</div>



## Tidyverse flavored Python (I'll fix it later)

| R tidyverse command | Python command |
|:--|:--|
|group_by | groupby |
|summarize(avg = mean(col1)) | mean() agg()|
|mutate(newcol=col1+col2) | assign(newcol = lambda data.frame ...|
|pivot_longer | is there a melt equivalent? for merging datasets? |
| ungroup | .. not needed?|
| subset(col > 80) | rslt_df = dataframe.loc[dataframe['col'] > 80] |
| select(c(col1, col2)) | dataframe.loc['col1':'col2']




```python
data = pd.read_csv("data/gapminder_all.csv", index_col=0)
summarydata = data.groupby("country").mean().head()
summarydata
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
      <th>gdpPercap_1952</th>
      <th>gdpPercap_1957</th>
      <th>gdpPercap_1962</th>
      <th>gdpPercap_1967</th>
      <th>gdpPercap_1972</th>
      <th>gdpPercap_1977</th>
      <th>gdpPercap_1982</th>
      <th>gdpPercap_1987</th>
      <th>gdpPercap_1992</th>
      <th>gdpPercap_1997</th>
      <th>...</th>
      <th>pop_1962</th>
      <th>pop_1967</th>
      <th>pop_1972</th>
      <th>pop_1977</th>
      <th>pop_1982</th>
      <th>pop_1987</th>
      <th>pop_1992</th>
      <th>pop_1997</th>
      <th>pop_2002</th>
      <th>pop_2007</th>
    </tr>
    <tr>
      <th>country</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Afghanistan</th>
      <td>779.445314</td>
      <td>820.853030</td>
      <td>853.100710</td>
      <td>836.197138</td>
      <td>739.981106</td>
      <td>786.113360</td>
      <td>978.011439</td>
      <td>852.395945</td>
      <td>649.341395</td>
      <td>635.341351</td>
      <td>...</td>
      <td>10267083.0</td>
      <td>11537966.0</td>
      <td>13079460.0</td>
      <td>14880372.0</td>
      <td>12881816.0</td>
      <td>13867957.0</td>
      <td>16317921.0</td>
      <td>22227415.0</td>
      <td>25268405</td>
      <td>31889923</td>
    </tr>
    <tr>
      <th>Albania</th>
      <td>1601.056136</td>
      <td>1942.284244</td>
      <td>2312.888958</td>
      <td>2760.196931</td>
      <td>3313.422188</td>
      <td>3533.003910</td>
      <td>3630.880722</td>
      <td>3738.932735</td>
      <td>2497.437901</td>
      <td>3193.054604</td>
      <td>...</td>
      <td>1728137.0</td>
      <td>1984060.0</td>
      <td>2263554.0</td>
      <td>2509048.0</td>
      <td>2780097.0</td>
      <td>3075321.0</td>
      <td>3326498.0</td>
      <td>3428038.0</td>
      <td>3508512</td>
      <td>3600523</td>
    </tr>
    <tr>
      <th>Algeria</th>
      <td>2449.008185</td>
      <td>3013.976023</td>
      <td>2550.816880</td>
      <td>3246.991771</td>
      <td>4182.663766</td>
      <td>4910.416756</td>
      <td>5745.160213</td>
      <td>5681.358539</td>
      <td>5023.216647</td>
      <td>4797.295051</td>
      <td>...</td>
      <td>11000948.0</td>
      <td>12760499.0</td>
      <td>14760787.0</td>
      <td>17152804.0</td>
      <td>20033753.0</td>
      <td>23254956.0</td>
      <td>26298373.0</td>
      <td>29072015.0</td>
      <td>31287142</td>
      <td>33333216</td>
    </tr>
    <tr>
      <th>Angola</th>
      <td>3520.610273</td>
      <td>3827.940465</td>
      <td>4269.276742</td>
      <td>5522.776375</td>
      <td>5473.288005</td>
      <td>3008.647355</td>
      <td>2756.953672</td>
      <td>2430.208311</td>
      <td>2627.845685</td>
      <td>2277.140884</td>
      <td>...</td>
      <td>4826015.0</td>
      <td>5247469.0</td>
      <td>5894858.0</td>
      <td>6162675.0</td>
      <td>7016384.0</td>
      <td>7874230.0</td>
      <td>8735988.0</td>
      <td>9875024.0</td>
      <td>10866106</td>
      <td>12420476</td>
    </tr>
    <tr>
      <th>Argentina</th>
      <td>5911.315053</td>
      <td>6856.856212</td>
      <td>7133.166023</td>
      <td>8052.953021</td>
      <td>9443.038526</td>
      <td>10079.026740</td>
      <td>8997.897412</td>
      <td>9139.671389</td>
      <td>9308.418710</td>
      <td>10967.281950</td>
      <td>...</td>
      <td>21283783.0</td>
      <td>22934225.0</td>
      <td>24779799.0</td>
      <td>26983828.0</td>
      <td>29341374.0</td>
      <td>31620918.0</td>
      <td>33958947.0</td>
      <td>36203463.0</td>
      <td>38331121</td>
      <td>40301927</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 36 columns</p>
</div>




```python

```
