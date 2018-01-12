
Observed Trend1:
Charter School has better overall passing rate, and average math and reading score compared to district school.

Observed Trend2:
The school performed best is Shelton High School(charter) whose math passing rate is 100% and reading passing rate is 100%
The school performed worst is Figueroa High School(district) whose math passing rate is 88.43% and reading passing rate is 100%

Observed Trend3:
Schools who spend more on their students on average dosen't mean their students have better reading and math score.


```python
import pandas as pd
```


```python
filename1 = 'data/schools_complete.csv'
schools1 = pd.read_csv(filename1)
schools = schools1.rename(index=str, columns={"name": "school"})
schools
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
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
  </tbody>
</table>
</div>




```python
filename2 = 'data/students_complete.csv'
students = pd.read_csv(filename2)
students.head()
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
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
ap_df = pd.merge(schools, students, how='outer', on=['school'])
ap_df.head()
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
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
# District Summary

# Create a high level snapshot (in table form) of the district's key metrics, including:
# Total Schools
# Total Students
# Total Budget
# Average Math Score
# Average Reading Score
# % Passing Math
# % Passing Reading
# Overall Passing Rate (Average of the above two)
```


```python
dist_df = ap_df.loc[ap_df['type'] == 'District']
dist_df.head()
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
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
Total_Schools = schools.loc[schools['type'] == 'District'].count()['school']
Total_Students = dist_df.count()['name']
Total_Budget = schools.loc[schools['type'] == 'District'].sum()['budget']
Average_Math_Score = dist_df['math_score'].mean()
Average_Reading_Score = dist_df['reading_score'].mean()
dist_df[dist_df.reading_score >= 60].count()['reading_score']
dist_df.count()['reading_score']
dist_df[dist_df.math_score >= 60].count()['math_score']
dist_df.count()['math_score']
Passing_Reading = dist_df[dist_df.reading_score >= 60].count()['reading_score'] / dist_df.count()['reading_score']
Passing_Math = dist_df[dist_df.math_score >= 60].count()['math_score'] / dist_df.count()['math_score']
Overall_Passing_Rate = (Passing_Math + Passing_Reading) / 2
```


```python
School_Passing_Reading = []
School_Passing_Math = []
school_list = schools['school'].tolist()
for x in school_list:
    df = ap_df.loc[ap_df['school'] == x]
    Passing_Reading_rate = df[df.reading_score >= 60].count()['reading_score'] / df.count()['reading_score']
    Passing_Math_rate = df[df.math_score >= 60].count()['math_score'] / df.count()['math_score']
    School_Passing_Reading.append(Passing_Reading_rate)
    School_Passing_Math.append(Passing_Math_rate)
School_Overall_Passing = [(x+y)/2 for x,y in zip(School_Passing_Reading, School_Passing_Math)]
# School_Overall_Passing
```


```python
District_Summary = pd.DataFrame({'Total Schools': Total_Schools,
                                 'Total Students': Total_Students,
                                 'Total Budget': Total_Budget,
                                 'Average Math Score': Average_Math_Score,
                                 'Average Reading Score': Average_Reading_Score,
                                 '% Passing Math': Passing_Math,
                                 '% Passing Reading': Passing_Reading,
                                 'Overall Passing Rate': Overall_Passing_Rate}, index=[0])
District_Summary
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
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Overall Passing Rate</th>
      <th>Total Budget</th>
      <th>Total Schools</th>
      <th>Total Students</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.89031</td>
      <td>1.0</td>
      <td>76.987026</td>
      <td>80.962485</td>
      <td>0.945155</td>
      <td>17347923</td>
      <td>7</td>
      <td>26976</td>
    </tr>
  </tbody>
</table>
</div>




```python
# School Summary

# Create an overview table that summarizes key metrics about each school, including:
# School Name
# School Type
# Total Students
# Total School Budget
# Per School Budget
# Average Math Score
# Average Reading Score
# % Passing Math
# % Passing Reading
# Overall Passing Rate (Average of the above two)
```


```python
df = ap_df.groupby('school').mean().sort_values(by=['School ID'])
df['type'] = schools['type'].tolist()
df['Per Student Budget'] = ap_df.groupby(['school']).mean()['budget']/ap_df.groupby(['school']).count()['budget']
df['Total Students'] = ap_df.groupby(['school']).count()['name']
df['% Passing Math'] = School_Passing_Math
df['% Passing Reading'] = School_Passing_Reading
df['% Overall Passing Rate'] = School_Overall_Passing
df = df.rename(index=str, columns={"reading_score": "Average Reading Score", 
                                   "math_score": "Average Math Score",
                                   "type": "School Type",
                                   "budget": "Total School Budget"})
school_summary = df[['School Type', 'Total Students', 'Total School Budget', 
                     'Per Student Budget', 'Average Math Score', 'Average Reading Score', 
                     '% Passing Math', '% Passing Reading', '% Overall Passing Rate']]
school_summary
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
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>school</th>
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
      <th>Huang High School</th>
      <td>District</td>
      <td>2917</td>
      <td>1910635.0</td>
      <td>655.0</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>0.888584</td>
      <td>1.0</td>
      <td>0.944292</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>1884411.0</td>
      <td>639.0</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>0.884368</td>
      <td>1.0</td>
      <td>0.942184</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600.0</td>
      <td>600.0</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>District</td>
      <td>4635</td>
      <td>3022020.0</td>
      <td>652.0</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>0.890831</td>
      <td>1.0</td>
      <td>0.945415</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>917500.0</td>
      <td>625.0</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574.0</td>
      <td>578.0</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356.0</td>
      <td>582.0</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>District</td>
      <td>4976</td>
      <td>3124928.0</td>
      <td>628.0</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>0.895297</td>
      <td>1.0</td>
      <td>0.947649</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>Charter</td>
      <td>427</td>
      <td>248087.0</td>
      <td>581.0</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>962</td>
      <td>585858.0</td>
      <td>609.0</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400.0</td>
      <td>583.0</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>3999</td>
      <td>2547363.0</td>
      <td>637.0</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>0.885471</td>
      <td>1.0</td>
      <td>0.942736</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>District</td>
      <td>4761</td>
      <td>3094650.0</td>
      <td>650.0</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>0.891829</td>
      <td>1.0</td>
      <td>0.945915</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>District</td>
      <td>2739</td>
      <td>1763916.0</td>
      <td>644.0</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>0.893027</td>
      <td>1.0</td>
      <td>0.946513</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130.0</td>
      <td>638.0</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Top Performing Schools (By Passing Rate)

# Create a table that highlights the top 5 performing schools based on Overall Passing Rate. Include:
# School Name
# School Type
# Total Students
# Total School Budget
# Per School Budget
# Average Math Score
# Average Reading Score
# % Passing Math
# % Passing Reading
# Overall Passing Rate (Average of the above two)
```


```python
school_summary.nlargest(5, '% Overall Passing Rate')
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
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>school</th>
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
      <th>Shelton High School</th>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600.0</td>
      <td>600.0</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>917500.0</td>
      <td>625.0</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574.0</td>
      <td>578.0</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356.0</td>
      <td>582.0</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>Charter</td>
      <td>427</td>
      <td>248087.0</td>
      <td>581.0</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Bottom Performing Schools (By Passing Rate)
# Create a table that highlights the bottom 5 performing schools based on Overall Passing Rate. 
# Include all of the same metrics as above.
```


```python
school_summary.nsmallest(5, '% Overall Passing Rate')
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
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>school</th>
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
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>1884411.0</td>
      <td>639.0</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>0.884368</td>
      <td>1.0</td>
      <td>0.942184</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>3999</td>
      <td>2547363.0</td>
      <td>637.0</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>0.885471</td>
      <td>1.0</td>
      <td>0.942736</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>District</td>
      <td>2917</td>
      <td>1910635.0</td>
      <td>655.0</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>0.888584</td>
      <td>1.0</td>
      <td>0.944292</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>District</td>
      <td>4635</td>
      <td>3022020.0</td>
      <td>652.0</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>0.890831</td>
      <td>1.0</td>
      <td>0.945415</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>District</td>
      <td>4761</td>
      <td>3094650.0</td>
      <td>650.0</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>0.891829</td>
      <td>1.0</td>
      <td>0.945915</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Math Scores by Grade

# Create a table that lists the average Math Score for students of 
# each grade level (9th, 10th, 11th, 12th) at each school.
```


```python
#grade = [9th, 10th, 11th, 12th]
m_grade9th = []
m_grade10th = []
m_grade11th = []
m_grade12th = []
for x in school_list:
    df = ap_df[ap_df['school'] == x]
    ms= df[df['grade'] == '9th'].mean()['math_score']
    m_grade9th.append(ms)
    ms= df[df['grade'] == '10th'].mean()['math_score']
    m_grade10th.append(ms)
    ms= df[df['grade'] == '11th'].mean()['math_score']
    m_grade11th.append(ms)
    ms= df[df['grade'] == '12th'].mean()['math_score']
    m_grade12th.append(ms)
```


```python
m_df = pd.DataFrame({'9th': m_grade9th,
                     '10th': m_grade10th,
                     '11th': m_grade11th,
                     '12th': m_grade12th}, index=school_list)
Math_Scores = m_df[['9th','10th','11th','12th']]
Math_Scores
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
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Huang High School</th>
      <td>77.027251</td>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.420755</td>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.438495</td>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.085578</td>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.787402</td>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.625455</td>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.264706</td>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.859966</td>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>77.187857</td>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.590022</td>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Reading Scores by Grade

# Create a table that lists the average Reading Score for students of 
# each grade level (9th, 10th, 11th, 12th) at each school.
```


```python
r_grade9th = []
r_grade10th = []
r_grade11th = []
r_grade12th = []
school_list = schools['school'].tolist()
for x in school_list:
    df = ap_df[ap_df['school'] == x]
    rs9 = df[df['grade'] == '9th'].mean()['reading_score']
    r_grade9th.append(rs9)
    rs10 = df[df['grade'] == '10th'].mean()['reading_score']
    r_grade10th.append(rs10)
    rs11 = df[df['grade'] == '11th'].mean()['reading_score']
    r_grade11th.append(rs11)
    rs12 = df[df['grade'] == '12th'].mean()['reading_score']
    r_grade12th.append(rs12)
```


```python
df = pd.DataFrame({'9th': r_grade9th,
                   '10th': r_grade10th,
                   '11th': r_grade11th,
                   '12th': r_grade12th}, index=school_list)
Reading_Scores = df[['9th','10th','11th','12th']]
Reading_Scores
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
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Huang High School</th>
      <td>81.290284</td>
      <td>81.512386</td>
      <td>81.417476</td>
      <td>80.305983</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.198598</td>
      <td>81.408912</td>
      <td>80.640339</td>
      <td>81.384863</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>84.122642</td>
      <td>83.441964</td>
      <td>84.373786</td>
      <td>82.781671</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.866860</td>
      <td>80.660147</td>
      <td>81.396140</td>
      <td>80.857143</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.369193</td>
      <td>83.706897</td>
      <td>84.288089</td>
      <td>84.013699</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.939778</td>
      <td>84.021452</td>
      <td>83.764608</td>
      <td>84.317673</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.676136</td>
      <td>84.253219</td>
      <td>83.788382</td>
      <td>84.287958</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>81.303155</td>
      <td>80.907183</td>
      <td>80.945643</td>
      <td>80.912451</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.677165</td>
      <td>83.324561</td>
      <td>83.815534</td>
      <td>84.698795</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.807273</td>
      <td>83.612000</td>
      <td>84.335938</td>
      <td>84.591160</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.833333</td>
      <td>83.812757</td>
      <td>84.156322</td>
      <td>84.073171</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.993127</td>
      <td>80.629808</td>
      <td>80.864811</td>
      <td>80.376426</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>81.260714</td>
      <td>80.773431</td>
      <td>80.616027</td>
      <td>81.227564</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>80.632653</td>
      <td>81.262712</td>
      <td>80.403642</td>
      <td>80.662338</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.728850</td>
      <td>84.254157</td>
      <td>83.585542</td>
      <td>83.831361</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Scores by School Spending

# Create a table that breaks down school performances based on average Spending Ranges (Per Student). 
# Use 4 reasonable bins to group school spending. Include in the table each of the following:
# Average Math Score
# Average Reading Score
# % Passing Math
# % Passing Reading
# Overall Passing Rate (Average of the above two)
```


```python
schools['Per Student Budget']=school_summary['Per Student Budget'].tolist()
schools
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
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
total_ap_df = pd.merge(schools, students, how='outer', on=['school'])
total_ap_df.head()
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
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
bins = [577, 598, 618, 638, 658]
group_names = ['(577,598]', '(598,618]', '(618,638]', '(638,658]']
```


```python
Spending_Range = pd.cut(total_ap_df['Per Student Budget'], bins, labels=group_names)
total_ap_df['Spending Range(Per Student)'] = pd.cut(total_ap_df['Per Student Budget'], bins, labels=group_names)
#Spending_Range
```


```python
SR_Passing_Reading = []
SR_Passing_Math = []
group_names = ['(577,598]', '(598,618]', '(618,638]', '(638,658]']
for x in group_names:
    df = total_ap_df.loc[total_ap_df['Spending Range(Per Student)'] == x]
    Passing_Reading_rate = df[df.reading_score >= 60].count()['reading_score'] / df.count()['reading_score']
    Passing_Math_rate = df[df.math_score >= 60].count()['math_score'] / df.count()['math_score']
    SR_Passing_Reading.append(Passing_Reading_rate)
    SR_Passing_Math.append(Passing_Math_rate)
SR_Overall_Passing = [(x+y)/2 for x,y in zip(SR_Passing_Reading, SR_Passing_Math)]
```


```python
sr_df = total_ap_df.groupby('Spending Range(Per Student)').mean()
sr_df['% Passing Math'] = SR_Passing_Math
sr_df['% Passing Reading'] = SR_Passing_Reading
sr_df['% Overall Passing Rate'] = SR_Overall_Passing
sr_df = sr_df.rename(index=str, columns={"reading_score": "Average Reading Score", 
                                         "math_score": "Average Math Score"})
sr_summary = sr_df[['Average Math Score', 'Average Reading Score', '% Passing Math', 
                 '% Passing Reading', '% Overall Passing Rate']]

sr_summary
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
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>Spending Range(Per Student)</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>(577,598]</th>
      <td>83.363065</td>
      <td>83.964039</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>(598,618]</th>
      <td>83.529196</td>
      <td>83.838414</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>(618,638]</th>
      <td>78.608710</td>
      <td>81.657476</td>
      <td>0.918944</td>
      <td>1.0</td>
      <td>0.959472</td>
    </tr>
    <tr>
      <th>(638,658]</th>
      <td>77.002111</td>
      <td>80.991112</td>
      <td>0.890006</td>
      <td>1.0</td>
      <td>0.945003</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Scores by School Size

# Repeat the above breakdown, but this time group schools based on a reasonable approximation of school size 
# (Small, Medium, Large).

```


```python
sz_bins = [0, 1000, 2000, 5000]
sz_group_names = ['Small(<1000)', 'Medium(1000,2000)', 'Large(2000,5000)']
```


```python
Size_Range = pd.cut(total_ap_df['size'], sz_bins, labels=sz_group_names)
total_ap_df['School Size'] = pd.cut(total_ap_df['size'], sz_bins, labels=sz_group_names)
#Size_Range
```


```python
SZ_Passing_Reading = []
SZ_Passing_Math = []
SZ_group_names = ['Small(<1000)', 'Medium(1000,2000)', 'Large(2000,5000)']
for x in SZ_group_names:
    df = total_ap_df.loc[total_ap_df['School Size'] == x]
    Passing_Reading_rate = df[df.reading_score >= 60].count()['reading_score'] / df.count()['reading_score']
    Passing_Math_rate = df[df.math_score >= 60].count()['math_score'] / df.count()['math_score']
    SZ_Passing_Reading.append(Passing_Reading_rate)
    SZ_Passing_Math.append(Passing_Math_rate)
SZ_Overall_Passing = [(x+y)/2 for x,y in zip(SZ_Passing_Reading, SZ_Passing_Math)]
```


```python
sz_df = total_ap_df.groupby('School Size').mean()
sz_df['% Passing Math'] = SZ_Passing_Math
sz_df['% Passing Reading'] = SZ_Passing_Reading
sz_df['% Overall Passing Rate'] = SZ_Overall_Passing
sz_df = sz_df.rename(index=str, columns={"reading_score": "Average Reading Score", 
                                         "math_score": "Average Math Score"})
sz_summary = sz_df[['Average Math Score', 'Average Reading Score', '% Passing Math', 
                 '% Passing Reading', '% Overall Passing Rate']]

sz_summary
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
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>School Size</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small(&lt;1000)</th>
      <td>83.828654</td>
      <td>83.974082</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>Medium(1000,2000)</th>
      <td>83.372682</td>
      <td>83.867989</td>
      <td>1.000000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>Large(2000,5000)</th>
      <td>77.477597</td>
      <td>81.198674</td>
      <td>0.898869</td>
      <td>1.0</td>
      <td>0.949434</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Scores by School Type

# Repeat the above breakdown, but this time group schools based on school type (Charter vs. District).
```


```python
ST_Passing_Reading = []
ST_Passing_Math = []
ST_group_names = ['Charter', 'District']
for x in ST_group_names:
    df = total_ap_df.loc[total_ap_df['type'] == x]
    Passing_Reading_rate = df[df.reading_score >= 60].count()['reading_score'] / df.count()['reading_score']
    Passing_Math_rate = df[df.math_score >= 60].count()['math_score'] / df.count()['math_score']
    ST_Passing_Reading.append(Passing_Reading_rate)
    ST_Passing_Math.append(Passing_Math_rate)
ST_Overall_Passing = [(x+y)/2 for x,y in zip(ST_Passing_Reading, ST_Passing_Math)]
```


```python
st_df = total_ap_df.groupby('type').mean()
st_df['% Passing Math'] = ST_Passing_Math
st_df['% Passing Reading'] = ST_Passing_Reading
st_df['% Overall Passing Rate'] = ST_Overall_Passing
st_df = st_df.rename(index=str, columns={"reading_score": "Average Reading Score", 
                                         "math_score": "Average Math Score"})
st_summary = st_df[['Average Math Score', 'Average Reading Score', '% Passing Math', 
                 '% Passing Reading', '% Overall Passing Rate']]
st_summary
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
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>83.406183</td>
      <td>83.902821</td>
      <td>1.00000</td>
      <td>1.0</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>District</th>
      <td>76.987026</td>
      <td>80.962485</td>
      <td>0.89031</td>
      <td>1.0</td>
      <td>0.945155</td>
    </tr>
  </tbody>
</table>
</div>


