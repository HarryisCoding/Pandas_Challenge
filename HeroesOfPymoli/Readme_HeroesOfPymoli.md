

```python
# Read CSV
import pandas as pd
file_path = 'data/purchase_data.json'
hp1_df = pd.read_json(file_path)
hp1_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>




```python
file_path = 'data/purchase_data2.json'
hp2_df = pd.read_json(file_path)
hp2_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20</td>
      <td>Male</td>
      <td>93</td>
      <td>Apocalyptic Battlescythe</td>
      <td>4.49</td>
      <td>Iloni35</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>12</td>
      <td>Dawne</td>
      <td>3.36</td>
      <td>Aidaira26</td>
    </tr>
    <tr>
      <th>2</th>
      <td>17</td>
      <td>Male</td>
      <td>5</td>
      <td>Putrid Fan</td>
      <td>2.63</td>
      <td>Irim47</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17</td>
      <td>Male</td>
      <td>123</td>
      <td>Twilight's Carver</td>
      <td>2.55</td>
      <td>Irith83</td>
    </tr>
    <tr>
      <th>4</th>
      <td>22</td>
      <td>Male</td>
      <td>154</td>
      <td>Feral Katana</td>
      <td>4.11</td>
      <td>Philodil43</td>
    </tr>
  </tbody>
</table>
</div>




```python
hp_df = hp1_df.append(hp2_df)
hp_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Player Count
```


```python
# df['column'].unique() (shows every element of the series that appears only once)
# hp_df['SN'].unique()
Total_Number_of_Players = len(hp_df['SN'].unique())
Total_Number_of_Players
pc = {'Total Players': [Total_Number_of_Players]}
p_df = pd.DataFrame(pc)
p_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>612</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Purchasing Analysis (Total)
#•Number of Unique Items
#•Average Purchase Price
#•Total Number of Purchases
#•Total Revenue
```


```python
#df['column'].value_counts() (counts the unique values in a column)
hp_df['SN'].value_counts().head()
hp_df['Item Name'].value_counts().head()
```




    Final Critic                            14
    Stormcaller                             12
    Arcane Gem                              12
    Betrayal, Whisper of Grieving Widows    11
    Crucifer                                10
    Name: Item Name, dtype: int64




```python
# Number of Unique Items
Number_of_Unique_Items = len(hp_df['Item Name'].value_counts())
Number_of_Unique_Items
```




    180




```python
# Total Number of Purchases
Total_Number_of_Purchases = len(hp_df)
Total_Number_of_Purchases
```




    858




```python
# Total Revenue
Total_Revenue = hp_df['Price'].sum()
Total_Revenue
```




    2514.4299999999967




```python
# Average Purchase Price
Average_Purchase_Price = Total_Revenue / Total_Number_of_Purchases
Average_Purchase_Price
```




    2.9305710955710915




```python
pa = {'Number of Unique Items': [Number_of_Unique_Items],
      'Average Price': [Average_Purchase_Price],
      'Number of Purchases': [Total_Number_of_Purchases],
      'Total Revenue': [Total_Revenue]}
pa_df = pd.DataFrame(pa)
#pa_df
```


```python
# Gender Demographics
#•Percentage and Count of Male Players
#•Percentage and Count of Female Players
#•Percentage and Count of Other / Non-Disclosed
```


```python
gd_df = hp_df.groupby('Gender')['SN'].nunique()
gd_df
```




    Gender
    Female                   112
    Male                     498
    Other / Non-Disclosed      9
    Name: SN, dtype: int64




```python
u_hp_df = hp_df.drop_duplicates(['SN'], keep = 'last')
#u_hp_df.head()
```


```python
# Percentage and Count of Male Players
gender = u_hp_df['Gender'].value_counts()
gender
```




    Male                     494
    Female                   109
    Other / Non-Disclosed      9
    Name: Gender, dtype: int64




```python
u_hp_df['Gender'].value_counts().sum()
```




    612




```python
male_players = gender[0]
male_players
```




    494




```python
total_players = u_hp_df['Gender'].value_counts().sum()
percentage_male_player = male_players / total_players
percentage_male_player
```




    0.80718954248366015




```python
# Percentage and Count of Female Players
female_players = gender[1]
female_players
```




    109




```python
total_players = u_hp_df['Gender'].value_counts().sum()
# percentage_female_player = "{:.2%}".format(female_players / total_players)
percentage_female_player = female_players / total_players
percentage_female_player
```




    0.1781045751633987




```python
# Percentage and Count of Other / Non-Disclosed
Other_NonDisclosed_players = gender[2]
Other_NonDisclosed_players
```




    9




```python
total_players = u_hp_df['Gender'].value_counts().sum()
# percentage_Other_NonDisclosed_player = "{:.2%}".format(female_players / total_players)
percenttage_other_nondisclosed_player = Other_NonDisclosed_players / total_players
percenttage_other_nondisclosed_player
```




    0.014705882352941176




```python
gender_index = ["Male", "Female", "Other/NonDisclosed"]
Percentage_of_Players = [percentage_male_player, percentage_female_player, percenttage_other_nondisclosed_player]
Total_Count = [male_players, female_players, Other_NonDisclosed_players]
gd = {'Percentage of Players': Percentage_of_Players,
      'Total Count': Total_Count,}
gd_df = pd.DataFrame(gd, index=gender_index)
gd_df['Percentage of Players'] = gd_df['Percentage of Players'].map("{:.2%}".format)
gd_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Percentage of Players</th>
      <th>Total Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>80.72%</td>
      <td>494</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>17.81%</td>
      <td>109</td>
    </tr>
    <tr>
      <th>Other/NonDisclosed</th>
      <td>1.47%</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Purchasing Analysis (Gender) 
# The below each broken by gender
# ● Purchase Count
# ● Average Purchase Price
# ● Total Purchase Value
# ● Normalized Totals
```


```python
g_df = hp_df.groupby('Gender').agg({'Price': 'sum','Item ID': 'count'})
#g_df
```


```python
pag_total_purchase_balue = g_df['Price']
pag_purchase_count = g_df['Item ID']
pag_apc = [(x*1.0)/y for x, y in zip(pag_total_purchase_balue, pag_purchase_count)]
g_df['Average Purchase Price'] = pd.Series(pag_apc, index=g_df.index)
#g_df
```


```python
max_price = hp_df['Price'].max()
min_price = hp_df['Price'].min()
mean_price = hp_df['Price'].mean()
Normalized_Totals = [(x- mean_price)/(max_price - min_price) for x in g_df['Price']]
Normalized_Totals
```




    [107.21613967033807, 521.46295900876009, 8.8878953955289823]




```python
pag_total_purchase_balue = g_df['Price']
pag_purchase_count = g_df['Item ID']
pag_apc = [(x*1.0)/y for x, y in zip(pag_total_purchase_balue, pag_purchase_count)]
g_df['Average Purchase Price'] = pd.Series(pag_apc, index=g_df.index)
g_df['Normalized Totals'] = pd.Series(Normalized_Totals, index=g_df.index)
g_df = g_df.rename(index=str,columns={'Price': 'Total Purchase Value', 'Item ID': 'Purchase Count'})
g_df['Average Purchase Price'] = g_df['Average Purchase Price'].map('${:,.2f}'.format)
g_df['Total Purchase Value'] = g_df['Total Purchase Value'].map('${:,.2f}'.format)
g_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Purchase Value</th>
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Normalized Totals</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>$424.29</td>
      <td>149</td>
      <td>$2.85</td>
      <td>107.216140</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>$2,052.28</td>
      <td>697</td>
      <td>$2.94</td>
      <td>521.462959</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>$37.86</td>
      <td>12</td>
      <td>$3.15</td>
      <td>8.887895</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Age Demographics
#•The below each broken into bins of 4 years (i.e. <10, 10-14, 15-19, etc.) 
#•Purchase Count
#•Average Purchase Price
#•Total Purchase Value
#•Normalized Totals
```


```python
hp_df['Age'].max()
```




    45




```python
hp_df['Age'].min()
```




    7




```python
bins = [6, 10, 14, 18, 22, 26, 30, 34, 38, 42, 45]
```


```python
group_names = ['(6,10]', '(10,14]', '(14,18]', '(18,22]', '(22,26]', '(26,30]','(30,34]','(34,38]','(38,42]','>42']
```


```python
Age_Range = pd.cut(hp_df['Age'], bins, labels=group_names)
hp_df['Age Range'] = pd.cut(hp_df['Age'], bins, labels=group_names)
Age_Range.head()
```




    0    (34,38]
    1    (18,22]
    2    (30,34]
    3    (18,22]
    4    (22,26]
    Name: Age, dtype: category
    Categories (10, object): [(6,10] < (10,14] < (14,18] < (18,22] ... (30,34] < (34,38] < (38,42] < >42]




```python
#hp_df.head()
```


```python
age_range_count = hp_df['Age Range'].value_counts()
#age_range_count
```


```python
ar_df = hp_df.groupby('Age Range').Price.sum()
#ar_df
```


```python
ar_df[1]
```




    92.749999999999986




```python
ar_pc = []
ar_pt = []
ar_apc = []
ar_nt = []
for x in range(10):
    pc = age_range_count[x]
    ar_pc.append(pc)
for x in range(10):
    tc = ar_df[x]
    ar_pt.append(tc)
ar_apc = [(x*1.0)/y for x, y in zip(ar_pt, ar_pc)]
for x in range(10):
    n = (ar_pt[x] - - mean_price)/(max_price - min_price)
    ar_nt.append(n)
#ar_nt
```


```python
age_df = hp_df.groupby('Age Range').agg({'Price': 'sum'})
age_df['Purchase Count'] = pd.Series(ar_pc, index=age_df.index)
age_df['Average Purchase Price'] = pd.Series(ar_pc, index=age_df.index)
age_df['Normalized Totals'] = pd.Series(ar_pc, index=age_df.index)
age_df = age_df.rename(columns={'Price': 'Total Purchase Value'})
age_df['Average Purchase Price'] = age_df['Average Purchase Price'].map('${:,.2f}'.format)
age_df['Total Purchase Value'] = age_df['Total Purchase Value'].map('${:,.2f}'.format)
age_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Purchase Value</th>
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Normalized Totals</th>
    </tr>
    <tr>
      <th>Age Range</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>(6,10]</th>
      <td>$110.44</td>
      <td>37</td>
      <td>$37.00</td>
      <td>37</td>
    </tr>
    <tr>
      <th>(10,14]</th>
      <td>$92.75</td>
      <td>34</td>
      <td>$34.00</td>
      <td>34</td>
    </tr>
    <tr>
      <th>(14,18]</th>
      <td>$349.73</td>
      <td>122</td>
      <td>$122.00</td>
      <td>122</td>
    </tr>
    <tr>
      <th>(18,22]</th>
      <td>$736.54</td>
      <td>251</td>
      <td>$251.00</td>
      <td>251</td>
    </tr>
    <tr>
      <th>(22,26]</th>
      <td>$675.63</td>
      <td>230</td>
      <td>$230.00</td>
      <td>230</td>
    </tr>
    <tr>
      <th>(26,30]</th>
      <td>$198.76</td>
      <td>67</td>
      <td>$67.00</td>
      <td>67</td>
    </tr>
    <tr>
      <th>(30,34]</th>
      <td>$151.41</td>
      <td>51</td>
      <td>$51.00</td>
      <td>51</td>
    </tr>
    <tr>
      <th>(34,38]</th>
      <td>$122.78</td>
      <td>42</td>
      <td>$42.00</td>
      <td>42</td>
    </tr>
    <tr>
      <th>(38,42]</th>
      <td>$69.86</td>
      <td>22</td>
      <td>$22.00</td>
      <td>22</td>
    </tr>
    <tr>
      <th>&gt;42</th>
      <td>$6.53</td>
      <td>2</td>
      <td>$2.00</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Top Spenders
#•Identify the the top 5 spenders in the game by total purchase value, then list (in a table):
#•SN
#•Purchase Count
#•Average Purchase Price
#•Total Purchase Value
```


```python
tops_df = hp_df.groupby('SN').agg({'Price': 'sum','Item ID': 'count'})
top5_df = tops_df.nlargest(5, 'Price')
top5_df = top5_df.rename(columns={'Price': 'Total Purchase Value', 'Item ID': 'Purchase Count'})
top5_df['Total Purchase Value'] = top5_df['Total Purchase Value'].map('${:,.2f}'.format)
#top5_df
```


```python
top5 = list(top5_df.index.values)
top5
```




    ['Undirrala66', 'Aerithllora36', 'Saedue76', 'Sondim43', 'Mindimnya67']




```python
top5c_df = hp_df['SN'].value_counts()
top5c_df.head()
```




    Undirrala66      5
    Saedue76         4
    Mindimnya67      4
    Aerithllora36    4
    Ila44            4
    Name: SN, dtype: int64




```python
t5_pt = top5_df['Total Purchase Value'].tolist()
t5_pt
```




    [17.06, 15.1, 13.56, 13.02, 12.739999999999998]




```python
t5_pc = top5_df['Purchase Count'].tolist()
t5_pc
```




    [5, 4, 4, 4, 4]




```python
t5_apc = [(x*1.0)/y for x, y in zip(t5_pt, t5_pc)]
t5_apc
```




    [3.412, 3.775, 3.39, 3.255, 3.1849999999999996]




```python
top5_df['Average Purchase Price'] = pd.Series(t5_apc, index=top5_df.index)
top5_df = top5_df.rename(columns={'Price': 'Total Purchase Value', 'Item ID': 'Purchase Count'})
top5_df['Total Purchase Value'] = top5_df['Total Purchase Value'].map('${:,.2f}'.format)
#top5_df['Average Purchase Price'] = top5_df['Average Purchase Price'].map('${:,.2f}'.format)
top5_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Purchase Value</th>
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
    </tr>
    <tr>
      <th>SN</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Undirrala66</th>
      <td>$17.06</td>
      <td>5</td>
      <td>3.412</td>
    </tr>
    <tr>
      <th>Aerithllora36</th>
      <td>$15.10</td>
      <td>4</td>
      <td>3.775</td>
    </tr>
    <tr>
      <th>Saedue76</th>
      <td>$13.56</td>
      <td>4</td>
      <td>3.390</td>
    </tr>
    <tr>
      <th>Sondim43</th>
      <td>$13.02</td>
      <td>4</td>
      <td>3.255</td>
    </tr>
    <tr>
      <th>Mindimnya67</th>
      <td>$12.74</td>
      <td>4</td>
      <td>3.185</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Most Popular Items
#•Identify the 5 most popular items by purchase count, then list (in a table):
#•Item ID
#•Item Name
#•Purchase Count
#•Item Price
#•Total Purchase Value
```


```python
topsi_df = hp_df[['Item ID','Item Name','Price']]
new_topsi_df = topsi_df.groupby(['Item ID','Item Name','Price']).agg({'Price': 'sum','Item ID': 'count'})
top5i_df = new_topsi_df.nlargest(5, 'Item ID')
top5i_df = top5i_df.rename(columns={'Price': 'Total Purchase Value', 'Item ID': 'Purchase Count'})
top5i_df['Total Purchase Value'] = top5i_df['Total Purchase Value'].map('${:,.2f}'.format)
#top5i_df['Price'] = top5i_df['Price'].map('${:,.2f}'.format)
top5i_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th></th>
      <th>Total Purchase Value</th>
      <th>Purchase Count</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>39</th>
      <th>Betrayal, Whisper of Grieving Widows</th>
      <th>2.35</th>
      <td>$25.85</td>
      <td>11</td>
    </tr>
    <tr>
      <th>84</th>
      <th>Arcane Gem</th>
      <th>2.23</th>
      <td>$24.53</td>
      <td>11</td>
    </tr>
    <tr>
      <th>13</th>
      <th>Serenity</th>
      <th>1.49</th>
      <td>$13.41</td>
      <td>9</td>
    </tr>
    <tr>
      <th>31</th>
      <th>Trickster</th>
      <th>2.07</th>
      <td>$18.63</td>
      <td>9</td>
    </tr>
    <tr>
      <th>34</th>
      <th>Retribution Axe</th>
      <th>4.14</th>
      <td>$37.26</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Most Profitable Items
#•Identify the 5 most profitable items by total purchase value, then list (in a table):
#•Item ID
#•Item Name
#•Purchase Count
#•Item Price
#•Total Purchase Value
```


```python
topsip_df = hp_df[['Item ID','Item Name','Price']]
new_topsip_df = topsip_df.groupby(['Item ID','Item Name','Price']).agg({'Price': 'sum','Item ID': 'count'})
top5ip_df = new_topsip_df.nlargest(5, 'Price')
top5ip_df = top5ip_df.rename(columns={'Price': 'Total Purchase Value', 'Item ID': 'Purchase Count'})
top5ip_df['Total Purchase Value'] = top5ip_df['Total Purchase Value'].map('${:,.2f}'.format)
top5ip_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th></th>
      <th>Total Purchase Value</th>
      <th>Purchase Count</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>34</th>
      <th>Retribution Axe</th>
      <th>4.14</th>
      <td>$37.26</td>
      <td>9</td>
    </tr>
    <tr>
      <th>115</th>
      <th>Spectral Diamond Doomblade</th>
      <th>4.25</th>
      <td>$29.75</td>
      <td>7</td>
    </tr>
    <tr>
      <th>32</th>
      <th>Orenmir</th>
      <th>4.95</th>
      <td>$29.70</td>
      <td>6</td>
    </tr>
    <tr>
      <th>103</th>
      <th>Singed Scalpel</th>
      <th>4.87</th>
      <td>$29.22</td>
      <td>6</td>
    </tr>
    <tr>
      <th>107</th>
      <th>Splitter, Foe Of Subtlety</th>
      <th>3.61</th>
      <td>$28.88</td>
      <td>8</td>
    </tr>
  </tbody>
</table>
</div>


