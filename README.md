# Career Data Cleaning

```python
import pandas as pd
import numpy as np
```


```python
career_data = pd.read_csv("career_data.csv", dtype={"postal_code":str})
career_data.head()
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
      <th>uniq_id</th>
      <th>crawl_timestamp</th>
      <th>job_title</th>
      <th>company_name</th>
      <th>post_date</th>
      <th>job_type</th>
      <th>inferred_salary_time_unit</th>
      <th>salary_offered</th>
      <th>job_board</th>
      <th>geo</th>
      <th>...</th>
      <th>fitness_score</th>
      <th>inferred_salary_from</th>
      <th>inferred_salary_to</th>
      <th>inferred_salary_currency</th>
      <th>is_consumed_job</th>
      <th>job_requirements</th>
      <th>contact_email</th>
      <th>test_contact_email</th>
      <th>post_date_unix_time</th>
      <th>postal_code</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>9a457ef257fecf231693a6ba08f50293</td>
      <td>2020-06-26 01:54:03 +0000</td>
      <td>Asphalt/Concrete Senior Project Manager</td>
      <td>GPAC</td>
      <td>2020-06-25</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>$99,642.00</td>
      <td>careerbuilder</td>
      <td>usa</td>
      <td>...</td>
      <td>10</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1593043200</td>
      <td>43961</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ba471e2faf6f79caf22cddebbedbc0e8</td>
      <td>2020-05-17 01:21:05 +0000</td>
      <td>Amazon Warehouse Team - Full Time</td>
      <td>Amazon Fulfillment</td>
      <td>2020-05-16</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>$58,626.00</td>
      <td>careerbuilder</td>
      <td>usa</td>
      <td>...</td>
      <td>10</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1589587200</td>
      <td>50467</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6f00bd02d63c633b5af453366f25c21e</td>
      <td>2020-06-27 04:53:42 +0000</td>
      <td>Amazon Warehouse Associate - Morning Shifts Av...</td>
      <td>Amazon Fulfillment</td>
      <td>2020-06-26</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>$67,450.00</td>
      <td>careerbuilder</td>
      <td>usa</td>
      <td>...</td>
      <td>10</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1593129600</td>
      <td>42620</td>
    </tr>
    <tr>
      <th>3</th>
      <td>8ad0d00bfa23cfd7b7c364b8ae72085f</td>
      <td>2020-06-03 01:21:32 +0000</td>
      <td>Assembly Electrical</td>
      <td>Manpower</td>
      <td>2020-06-02</td>
      <td>Full-Time</td>
      <td>/hour</td>
      <td>$47,467.00</td>
      <td>careerbuilder</td>
      <td>usa</td>
      <td>...</td>
      <td>10</td>
      <td>14.00</td>
      <td>14.00</td>
      <td>$</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1591056000</td>
      <td>97275</td>
    </tr>
    <tr>
      <th>4</th>
      <td>31753dc342a1b2a07db712454c0d5f87</td>
      <td>2020-05-23 01:19:07 +0000</td>
      <td>Graphics Designer</td>
      <td>The North West Company - U.S.</td>
      <td>2020-05-22</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>$136,684.00</td>
      <td>careerbuilder</td>
      <td>usa</td>
      <td>...</td>
      <td>10</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1590105600</td>
      <td>37765</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 30 columns</p>
</div>




```python
career_data.describe()
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
      <th>postdate_yyyymmdd</th>
      <th>duplicate_status</th>
      <th>fitness_score</th>
      <th>test_contact_email</th>
      <th>post_date_unix_time</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>3.000000e+03</td>
      <td>0.0</td>
      <td>3000.0</td>
      <td>0.0</td>
      <td>3.000000e+03</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2.020054e+07</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>1.590265e+09</td>
    </tr>
    <tr>
      <th>std</th>
      <td>6.907365e+01</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>1.811007e+06</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2.020033e+07</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>1.585526e+09</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.020051e+07</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>1.588982e+09</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2.020052e+07</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>1.590106e+09</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2.020061e+07</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>1.591834e+09</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2.020063e+07</td>
      <td>NaN</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>1.593389e+09</td>
    </tr>
  </tbody>
</table>
</div>




```python
career_data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 3000 entries, 0 to 2999
    Data columns (total 30 columns):
     #   Column                        Non-Null Count  Dtype  
    ---  ------                        --------------  -----  
     0   uniq_id                       3000 non-null   object 
     1   crawl_timestamp               3000 non-null   object 
     2   job_title                     3000 non-null   object 
     3   company_name                  3000 non-null   object 
     4   post_date                     3000 non-null   object 
     5   job_type                      2984 non-null   object 
     6   inferred_salary_time_unit     3000 non-null   object 
     7   salary_offered                3000 non-null   object 
     8   job_board                     3000 non-null   object 
     9   geo                           3000 non-null   object 
     10  job_post_lang                 3000 non-null   object 
     11  valid_through                 3000 non-null   object 
     12  postdate_yyyymmdd             3000 non-null   int64  
     13  last_expiry_check_date        3000 non-null   object 
     14  latest_expiry_check_date      3000 non-null   object 
     15  duplicate_status              0 non-null      float64
     16  postdate_in_indexname_format  3000 non-null   object 
     17  inferred_city                 2795 non-null   object 
     18  inferred_state                3000 non-null   object 
     19  inferred_country              3000 non-null   object 
     20  fitness_score                 3000 non-null   int64  
     21  inferred_salary_from          386 non-null    object 
     22  inferred_salary_to            386 non-null    object 
     23  inferred_salary_currency      339 non-null    object 
     24  is_consumed_job               27 non-null     object 
     25  job_requirements              1 non-null      object 
     26  contact_email                 1 non-null      object 
     27  test_contact_email            0 non-null      float64
     28  post_date_unix_time           3000 non-null   int64  
     29  postal_code                   3000 non-null   object 
    dtypes: float64(2), int64(3), object(25)
    memory usage: 703.2+ KB
    


```python
career_data.nunique()
```




    uniq_id                         3000
    crawl_timestamp                 2968
    job_title                       2096
    company_name                     747
    post_date                         81
    job_type                           9
    inferred_salary_time_unit         13
    salary_offered                  2967
    job_board                          1
    geo                                1
    job_post_lang                      1
    valid_through                     83
    postdate_yyyymmdd                 81
    last_expiry_check_date            76
    latest_expiry_check_date          76
    duplicate_status                   0
    postdate_in_indexname_format      10
    inferred_city                   1400
    inferred_state                    51
    inferred_country                   1
    fitness_score                      1
    inferred_salary_from             122
    inferred_salary_to               140
    inferred_salary_currency           1
    is_consumed_job                    1
    job_requirements                   1
    contact_email                      1
    test_contact_email                 0
    post_date_unix_time               81
    postal_code                     2960
    dtype: int64




```python
columns_to_drop = career_data.nunique()[career_data.nunique()==1].index
columns_to_drop
```




    Index(['job_board', 'geo', 'job_post_lang', 'inferred_country',
           'fitness_score', 'inferred_salary_currency', 'is_consumed_job',
           'job_requirements', 'contact_email'],
          dtype='object')




```python
career_data_cols_dropped = career_data.copy()
career_data_cols_dropped = career_data_cols_dropped.drop(columns=columns_to_drop)
```


```python
career_data_cols_dropped.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 3000 entries, 0 to 2999
    Data columns (total 21 columns):
     #   Column                        Non-Null Count  Dtype  
    ---  ------                        --------------  -----  
     0   uniq_id                       3000 non-null   object 
     1   crawl_timestamp               3000 non-null   object 
     2   job_title                     3000 non-null   object 
     3   company_name                  3000 non-null   object 
     4   post_date                     3000 non-null   object 
     5   job_type                      2984 non-null   object 
     6   inferred_salary_time_unit     3000 non-null   object 
     7   salary_offered                3000 non-null   object 
     8   valid_through                 3000 non-null   object 
     9   postdate_yyyymmdd             3000 non-null   int64  
     10  last_expiry_check_date        3000 non-null   object 
     11  latest_expiry_check_date      3000 non-null   object 
     12  duplicate_status              0 non-null      float64
     13  postdate_in_indexname_format  3000 non-null   object 
     14  inferred_city                 2795 non-null   object 
     15  inferred_state                3000 non-null   object 
     16  inferred_salary_from          386 non-null    object 
     17  inferred_salary_to            386 non-null    object 
     18  test_contact_email            0 non-null      float64
     19  post_date_unix_time           3000 non-null   int64  
     20  postal_code                   3000 non-null   object 
    dtypes: float64(2), int64(2), object(17)
    memory usage: 492.3+ KB
    


```python
career_data_cols_dropped = career_data_cols_dropped.dropna(axis = 1, how="all")
career_data_cols_dropped.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 3000 entries, 0 to 2999
    Data columns (total 19 columns):
     #   Column                        Non-Null Count  Dtype 
    ---  ------                        --------------  ----- 
     0   uniq_id                       3000 non-null   object
     1   crawl_timestamp               3000 non-null   object
     2   job_title                     3000 non-null   object
     3   company_name                  3000 non-null   object
     4   post_date                     3000 non-null   object
     5   job_type                      2984 non-null   object
     6   inferred_salary_time_unit     3000 non-null   object
     7   salary_offered                3000 non-null   object
     8   valid_through                 3000 non-null   object
     9   postdate_yyyymmdd             3000 non-null   int64 
     10  last_expiry_check_date        3000 non-null   object
     11  latest_expiry_check_date      3000 non-null   object
     12  postdate_in_indexname_format  3000 non-null   object
     13  inferred_city                 2795 non-null   object
     14  inferred_state                3000 non-null   object
     15  inferred_salary_from          386 non-null    object
     16  inferred_salary_to            386 non-null    object
     17  post_date_unix_time           3000 non-null   int64 
     18  postal_code                   3000 non-null   object
    dtypes: int64(2), object(17)
    memory usage: 445.4+ KB
    


```python
career_data_cols_dropped.dtypes
```




    uniq_id                         object
    crawl_timestamp                 object
    job_title                       object
    company_name                    object
    post_date                       object
    job_type                        object
    inferred_salary_time_unit       object
    salary_offered                  object
    valid_through                   object
    postdate_yyyymmdd                int64
    last_expiry_check_date          object
    latest_expiry_check_date        object
    postdate_in_indexname_format    object
    inferred_city                   object
    inferred_state                  object
    inferred_salary_from            object
    inferred_salary_to              object
    post_date_unix_time              int64
    postal_code                     object
    dtype: object




```python
career_data_cols_dropped.salary_offered
```




    0        $99,642.00
    1        $58,626.00
    2        $67,450.00
    3        $47,467.00
    4       $136,684.00
               ...     
    2995     $63,152.00
    2996    $108,575.00
    2997     $88,469.00
    2998    $102,933.00
    2999     $82,329.00
    Name: salary_offered, Length: 3000, dtype: object




```python
career_data_typechanged = career_data_cols_dropped.copy()
career_data_typechanged['salary_offered'] = career_data_typechanged['salary_offered'].apply(lambda x: x.replace("$","").replace(",","")).astype(float)
career_data_typechanged.salary_offered
```




    0        99642.0
    1        58626.0
    2        67450.0
    3        47467.0
    4       136684.0
              ...   
    2995     63152.0
    2996    108575.0
    2997     88469.0
    2998    102933.0
    2999     82329.0
    Name: salary_offered, Length: 3000, dtype: float64




```python
career_data_typechanged[['crawl_timestamp', 'valid_through', 'postdate_yyyymmdd', 'last_expiry_check_date', 'latest_expiry_check_date', 'postdate_in_indexname_format']]
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
      <th>crawl_timestamp</th>
      <th>valid_through</th>
      <th>postdate_yyyymmdd</th>
      <th>last_expiry_check_date</th>
      <th>latest_expiry_check_date</th>
      <th>postdate_in_indexname_format</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-06-26 01:54:03 +0000</td>
      <td>2020-07-24</td>
      <td>20200625</td>
      <td>2020.06.26</td>
      <td>2020-06-26</td>
      <td>2020.06.22</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020-05-17 01:21:05 +0000</td>
      <td>2020-06-15</td>
      <td>20200516</td>
      <td>2020.05.17</td>
      <td>2020-05-17</td>
      <td>2020.05.11</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020-06-27 04:53:42 +0000</td>
      <td>2020-07-25</td>
      <td>20200626</td>
      <td>2020.06.27</td>
      <td>2020-06-27</td>
      <td>2020.06.22</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-06-03 01:21:32 +0000</td>
      <td>2020-07-01</td>
      <td>20200602</td>
      <td>2020.06.03</td>
      <td>2020-06-03</td>
      <td>2020.06.01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-05-23 01:19:07 +0000</td>
      <td>2020-06-21</td>
      <td>20200522</td>
      <td>2020.05.23</td>
      <td>2020-05-23</td>
      <td>2020.05.22</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2995</th>
      <td>2020-05-19 01:21:18 +0000</td>
      <td>2020-06-17</td>
      <td>20200518</td>
      <td>2020.05.19</td>
      <td>2020-05-19</td>
      <td>2020.05.11</td>
    </tr>
    <tr>
      <th>2996</th>
      <td>2020-06-12 01:45:25 +0000</td>
      <td>2020-07-10</td>
      <td>20200611</td>
      <td>2020.06.12</td>
      <td>2020-06-12</td>
      <td>2020.06.11</td>
    </tr>
    <tr>
      <th>2997</th>
      <td>2020-04-30 01:47:25 +0000</td>
      <td>2020-05-28</td>
      <td>20200429</td>
      <td>2020.04.30</td>
      <td>2020-04-30</td>
      <td>2020.04.22</td>
    </tr>
    <tr>
      <th>2998</th>
      <td>2020-06-12 00:57:31 +0000</td>
      <td>2020-07-10</td>
      <td>20200611</td>
      <td>2020.06.12</td>
      <td>2020-06-12</td>
      <td>2020.06.11</td>
    </tr>
    <tr>
      <th>2999</th>
      <td>2020-05-07 02:51:11 +0000</td>
      <td>2020-06-05</td>
      <td>20200506</td>
      <td>2020.05.07</td>
      <td>2020-05-07</td>
      <td>2020.05.01</td>
    </tr>
  </tbody>
</table>
<p>3000 rows × 6 columns</p>
</div>




```python
career_data_dtype_change = career_data_typechanged.copy()
pd.to_datetime(career_data_dtype_change["crawl_timestamp"])
```




    0      2020-06-26 01:54:03+00:00
    1      2020-05-17 01:21:05+00:00
    2      2020-06-27 04:53:42+00:00
    3      2020-06-03 01:21:32+00:00
    4      2020-05-23 01:19:07+00:00
                      ...           
    2995   2020-05-19 01:21:18+00:00
    2996   2020-06-12 01:45:25+00:00
    2997   2020-04-30 01:47:25+00:00
    2998   2020-06-12 00:57:31+00:00
    2999   2020-05-07 02:51:11+00:00
    Name: crawl_timestamp, Length: 3000, dtype: datetime64[ns, UTC]




```python
career_data_dtype_change["crawl_timestamp"] = pd.to_datetime(career_data_dtype_change["crawl_timestamp"])
career_data_dtype_change["postdate_yyyymmdd"] = pd.to_datetime(career_data_dtype_change["postdate_yyyymmdd"], format="%Y%m%d")
career_data_dtype_change["last_expiry_check_date"] = pd.to_datetime(career_data_dtype_change["last_expiry_check_date"])
career_data_dtype_change[['crawl_timestamp', 'valid_through', 'postdate_yyyymmdd', 'last_expiry_check_date', 'latest_expiry_check_date', 'postdate_in_indexname_format']]
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
      <th>crawl_timestamp</th>
      <th>valid_through</th>
      <th>postdate_yyyymmdd</th>
      <th>last_expiry_check_date</th>
      <th>latest_expiry_check_date</th>
      <th>postdate_in_indexname_format</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-06-26 01:54:03+00:00</td>
      <td>2020-07-24</td>
      <td>2020-06-25</td>
      <td>2020-06-26</td>
      <td>2020-06-26</td>
      <td>2020-06-22</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020-05-17 01:21:05+00:00</td>
      <td>2020-06-15</td>
      <td>2020-05-16</td>
      <td>2020-05-17</td>
      <td>2020-05-17</td>
      <td>2020-05-11</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020-06-27 04:53:42+00:00</td>
      <td>2020-07-25</td>
      <td>2020-06-26</td>
      <td>2020-06-27</td>
      <td>2020-06-27</td>
      <td>2020-06-22</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-06-03 01:21:32+00:00</td>
      <td>2020-07-01</td>
      <td>2020-06-02</td>
      <td>2020-06-03</td>
      <td>2020-06-03</td>
      <td>2020-06-01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-05-23 01:19:07+00:00</td>
      <td>2020-06-21</td>
      <td>2020-05-22</td>
      <td>2020-05-23</td>
      <td>2020-05-23</td>
      <td>2020-05-22</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2995</th>
      <td>2020-05-19 01:21:18+00:00</td>
      <td>2020-06-17</td>
      <td>2020-05-18</td>
      <td>2020-05-19</td>
      <td>2020-05-19</td>
      <td>2020-05-11</td>
    </tr>
    <tr>
      <th>2996</th>
      <td>2020-06-12 01:45:25+00:00</td>
      <td>2020-07-10</td>
      <td>2020-06-11</td>
      <td>2020-06-12</td>
      <td>2020-06-12</td>
      <td>2020-06-11</td>
    </tr>
    <tr>
      <th>2997</th>
      <td>2020-04-30 01:47:25+00:00</td>
      <td>2020-05-28</td>
      <td>2020-04-29</td>
      <td>2020-04-30</td>
      <td>2020-04-30</td>
      <td>2020-04-22</td>
    </tr>
    <tr>
      <th>2998</th>
      <td>2020-06-12 00:57:31+00:00</td>
      <td>2020-07-10</td>
      <td>2020-06-11</td>
      <td>2020-06-12</td>
      <td>2020-06-12</td>
      <td>2020-06-11</td>
    </tr>
    <tr>
      <th>2999</th>
      <td>2020-05-07 02:51:11+00:00</td>
      <td>2020-06-05</td>
      <td>2020-05-06</td>
      <td>2020-05-07</td>
      <td>2020-05-07</td>
      <td>2020-05-01</td>
    </tr>
  </tbody>
</table>
<p>3000 rows × 6 columns</p>
</div>




```python
missing_values = [np.nan, "", " ", None]

career_data_dtype_change.isin(missing_values).mean().sort_values(ascending=False) * 100
```




    inferred_salary_to              87.133333
    inferred_salary_from            87.133333
    inferred_city                    6.833333
    job_type                         0.533333
    uniq_id                          0.000000
    last_expiry_check_date           0.000000
    post_date_unix_time              0.000000
    inferred_state                   0.000000
    postdate_in_indexname_format     0.000000
    latest_expiry_check_date         0.000000
    postdate_yyyymmdd                0.000000
    crawl_timestamp                  0.000000
    valid_through                    0.000000
    salary_offered                   0.000000
    inferred_salary_time_unit        0.000000
    post_date                        0.000000
    company_name                     0.000000
    job_title                        0.000000
    postal_code                      0.000000
    dtype: float64




```python
columns_to_drop = career_data_dtype_change.isin(missing_values).mean()[(career_data_dtype_change.isin(missing_values).mean()) > 0.86].index

career_data_missing_values = career_data_dtype_change.copy()
career_data_missing_values = career_data_missing_values.drop(columns=columns_to_drop)
career_data_missing_values.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 3000 entries, 0 to 2999
    Data columns (total 17 columns):
     #   Column                        Non-Null Count  Dtype              
    ---  ------                        --------------  -----              
     0   uniq_id                       3000 non-null   object             
     1   crawl_timestamp               3000 non-null   datetime64[ns, UTC]
     2   job_title                     3000 non-null   object             
     3   company_name                  3000 non-null   object             
     4   post_date                     3000 non-null   object             
     5   job_type                      2984 non-null   object             
     6   inferred_salary_time_unit     3000 non-null   object             
     7   salary_offered                3000 non-null   float64            
     8   valid_through                 3000 non-null   object             
     9   postdate_yyyymmdd             3000 non-null   datetime64[ns]     
     10  last_expiry_check_date        3000 non-null   datetime64[ns]     
     11  latest_expiry_check_date      3000 non-null   object             
     12  postdate_in_indexname_format  3000 non-null   datetime64[ns]     
     13  inferred_city                 2795 non-null   object             
     14  inferred_state                3000 non-null   object             
     15  post_date_unix_time           3000 non-null   int64              
     16  postal_code                   3000 non-null   object             
    dtypes: datetime64[ns, UTC](1), datetime64[ns](3), float64(1), int64(1), object(11)
    memory usage: 398.6+ KB
    


```python
missing_values = [np.nan, "", " ", None]

career_data_missing_values.isin(missing_values).mean().sort_values(ascending=False) * 100
```




    inferred_city                   6.833333
    job_type                        0.533333
    uniq_id                         0.000000
    postdate_yyyymmdd               0.000000
    post_date_unix_time             0.000000
    inferred_state                  0.000000
    postdate_in_indexname_format    0.000000
    latest_expiry_check_date        0.000000
    last_expiry_check_date          0.000000
    valid_through                   0.000000
    crawl_timestamp                 0.000000
    salary_offered                  0.000000
    inferred_salary_time_unit       0.000000
    post_date                       0.000000
    company_name                    0.000000
    job_title                       0.000000
    postal_code                     0.000000
    dtype: float64




```python
career_data_missing_values.inferred_city
```




    0            Houston
    1         Cincinnati
    2            Peabody
    3            Villard
    4          Anchorage
                ...     
    2995     Wake forest
    2996    White plains
    2997        Martinez
    2998          Rahway
    2999          Queens
    Name: inferred_city, Length: 3000, dtype: object



Replacing the most likely city in the given state of the job posting


```python
inferred_city_mapping = career_data_missing_values.groupby(['inferred_state'])["inferred_city"].agg(lambda x:x.value_counts().index[0]).to_dict()
inferred_city_mapping
```




    {'Alabama': 'Montgomery',
     'Alaska': 'Anchorage',
     'Arizona': 'Phoenix',
     'Arkansas': 'Texarkana',
     'California': 'Los angeles',
     'Colorado': 'Denver',
     'Connecticut': 'Hartford',
     'Delaware': 'Wilmington',
     'District of columbia': 'Washington',
     'Florida': 'Orlando',
     'Georgia': 'Atlanta',
     'Hawaii': 'Honolulu',
     'Idaho': 'Boise',
     'Illinois': 'Chicago',
     'Indiana': 'Indianapolis',
     'Iowa': 'Des moines',
     'Kansas': 'Wichita',
     'Kentucky': 'Louisville',
     'Louisiana': 'Baton rouge',
     'Maine': 'Augusta',
     'Maryland': 'Baltimore',
     'Massachusetts': 'Boston',
     'Michigan': 'Grand rapids',
     'Minnesota': 'Minneapolis',
     'Mississippi': 'Jackson',
     'Missouri': 'Saint louis',
     'Montana': 'Billings',
     'Nebraska': 'Omaha',
     'Nevada': 'Las vegas',
     'New hampshire': 'Manchester',
     'New jersey': 'Franklin',
     'New mexico': 'Albuquerque',
     'New york': 'New york',
     'North carolina': 'Charlotte',
     'North dakota': 'Grand forks',
     'Ohio': 'Cincinnati',
     'Oklahoma': 'Tulsa',
     'Oregon': 'Portland',
     'Pennsylvania': 'Philadelphia',
     'Rhode island': 'Providence',
     'South carolina': 'Columbia',
     'South dakota': 'Sioux falls',
     'Tennessee': 'Nashville',
     'Texas': 'San antonio',
     'Utah': 'Salt lake city',
     'Vermont': 'Rutland',
     'Virginia': 'Chesapeake',
     'Washington': 'Seattle',
     'West virginia': 'Martinsburg',
     'Wisconsin': 'Madison',
     'Wyoming': 'Cheyenne'}




```python
career_data_missing_values["inferred_city"] = career_data_missing_values["inferred_city"].fillna(career_data_missing_values["inferred_state"].map(inferred_city_mapping))
career_data_missing_values.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 3000 entries, 0 to 2999
    Data columns (total 17 columns):
     #   Column                        Non-Null Count  Dtype              
    ---  ------                        --------------  -----              
     0   uniq_id                       3000 non-null   object             
     1   crawl_timestamp               3000 non-null   datetime64[ns, UTC]
     2   job_title                     3000 non-null   object             
     3   company_name                  3000 non-null   object             
     4   post_date                     3000 non-null   object             
     5   job_type                      2984 non-null   object             
     6   inferred_salary_time_unit     3000 non-null   object             
     7   salary_offered                3000 non-null   float64            
     8   valid_through                 3000 non-null   object             
     9   postdate_yyyymmdd             3000 non-null   datetime64[ns]     
     10  last_expiry_check_date        3000 non-null   datetime64[ns]     
     11  latest_expiry_check_date      3000 non-null   object             
     12  postdate_in_indexname_format  3000 non-null   datetime64[ns]     
     13  inferred_city                 3000 non-null   object             
     14  inferred_state                3000 non-null   object             
     15  post_date_unix_time           3000 non-null   int64              
     16  postal_code                   3000 non-null   object             
    dtypes: datetime64[ns, UTC](1), datetime64[ns](3), float64(1), int64(1), object(11)
    memory usage: 398.6+ KB
    

# Label encoding our state data


```python
career_data_encoded = career_data_missing_values.copy()

from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()

career_data_encoded["inferred_state"] = le.fit_transform(career_data_encoded["inferred_state"])

career_data_encoded["inferred_state"]
```




    0       43
    1       35
    2       21
    3       23
    4        1
            ..
    2995    33
    2996    32
    2997     4
    2998    30
    2999    32
    Name: inferred_state, Length: 3000, dtype: int32



# One hot encoding our state data

We drop the first dummy column to prevent multicollinearity


```python
pd.get_dummies(career_data_missing_values["inferred_state"], prefix="state", drop_first =True)
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
      <th>state_Alaska</th>
      <th>state_Arizona</th>
      <th>state_Arkansas</th>
      <th>state_California</th>
      <th>state_Colorado</th>
      <th>state_Connecticut</th>
      <th>state_Delaware</th>
      <th>state_District of columbia</th>
      <th>state_Florida</th>
      <th>state_Georgia</th>
      <th>...</th>
      <th>state_South dakota</th>
      <th>state_Tennessee</th>
      <th>state_Texas</th>
      <th>state_Utah</th>
      <th>state_Vermont</th>
      <th>state_Virginia</th>
      <th>state_Washington</th>
      <th>state_West virginia</th>
      <th>state_Wisconsin</th>
      <th>state_Wyoming</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2995</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2996</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2997</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2998</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2999</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>3000 rows × 50 columns</p>
</div>




```python
career_data_missing_values.post_date_unix_time
```




    0       1593043200
    1       1589587200
    2       1593129600
    3       1591056000
    4       1590105600
               ...    
    2995    1589760000
    2996    1591833600
    2997    1588118400
    2998    1591833600
    2999    1588723200
    Name: post_date_unix_time, Length: 3000, dtype: int64




```python
from sklearn.preprocessing import MinMaxScaler

career_data_scaled = career_data_encoded.copy()

scaler = MinMaxScaler()

# df_scaled = pd.DataFrame(scaler.fit_transform(df), columns=df.columns)
career_data_scaled["post_date_unix_time"] = scaler.fit_transform(career_data_scaled[["post_date_unix_time"]])
career_data_scaled
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
      <th>uniq_id</th>
      <th>crawl_timestamp</th>
      <th>job_title</th>
      <th>company_name</th>
      <th>post_date</th>
      <th>job_type</th>
      <th>inferred_salary_time_unit</th>
      <th>salary_offered</th>
      <th>valid_through</th>
      <th>postdate_yyyymmdd</th>
      <th>last_expiry_check_date</th>
      <th>latest_expiry_check_date</th>
      <th>postdate_in_indexname_format</th>
      <th>inferred_city</th>
      <th>inferred_state</th>
      <th>post_date_unix_time</th>
      <th>postal_code</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>9a457ef257fecf231693a6ba08f50293</td>
      <td>2020-06-26 01:54:03+00:00</td>
      <td>Asphalt/Concrete Senior Project Manager</td>
      <td>GPAC</td>
      <td>2020-06-25</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>99642.0</td>
      <td>2020-07-24</td>
      <td>2020-06-25</td>
      <td>2020-06-26</td>
      <td>2020-06-26</td>
      <td>2020-06-22</td>
      <td>Houston</td>
      <td>43</td>
      <td>0.956044</td>
      <td>43961</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ba471e2faf6f79caf22cddebbedbc0e8</td>
      <td>2020-05-17 01:21:05+00:00</td>
      <td>Amazon Warehouse Team - Full Time</td>
      <td>Amazon Fulfillment</td>
      <td>2020-05-16</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>58626.0</td>
      <td>2020-06-15</td>
      <td>2020-05-16</td>
      <td>2020-05-17</td>
      <td>2020-05-17</td>
      <td>2020-05-11</td>
      <td>Cincinnati</td>
      <td>35</td>
      <td>0.516484</td>
      <td>50467</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6f00bd02d63c633b5af453366f25c21e</td>
      <td>2020-06-27 04:53:42+00:00</td>
      <td>Amazon Warehouse Associate - Morning Shifts Av...</td>
      <td>Amazon Fulfillment</td>
      <td>2020-06-26</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>67450.0</td>
      <td>2020-07-25</td>
      <td>2020-06-26</td>
      <td>2020-06-27</td>
      <td>2020-06-27</td>
      <td>2020-06-22</td>
      <td>Peabody</td>
      <td>21</td>
      <td>0.967033</td>
      <td>42620</td>
    </tr>
    <tr>
      <th>3</th>
      <td>8ad0d00bfa23cfd7b7c364b8ae72085f</td>
      <td>2020-06-03 01:21:32+00:00</td>
      <td>Assembly Electrical</td>
      <td>Manpower</td>
      <td>2020-06-02</td>
      <td>Full-Time</td>
      <td>/hour</td>
      <td>47467.0</td>
      <td>2020-07-01</td>
      <td>2020-06-02</td>
      <td>2020-06-03</td>
      <td>2020-06-03</td>
      <td>2020-06-01</td>
      <td>Villard</td>
      <td>23</td>
      <td>0.703297</td>
      <td>97275</td>
    </tr>
    <tr>
      <th>4</th>
      <td>31753dc342a1b2a07db712454c0d5f87</td>
      <td>2020-05-23 01:19:07+00:00</td>
      <td>Graphics Designer</td>
      <td>The North West Company - U.S.</td>
      <td>2020-05-22</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>136684.0</td>
      <td>2020-06-21</td>
      <td>2020-05-22</td>
      <td>2020-05-23</td>
      <td>2020-05-23</td>
      <td>2020-05-22</td>
      <td>Anchorage</td>
      <td>1</td>
      <td>0.582418</td>
      <td>37765</td>
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
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2995</th>
      <td>a56efdccbe87fea387e2edd3b1ec9faa</td>
      <td>2020-05-19 01:21:18+00:00</td>
      <td>Store Hourly</td>
      <td>Advance Auto Parts</td>
      <td>2020-05-18</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>63152.0</td>
      <td>2020-06-17</td>
      <td>2020-05-18</td>
      <td>2020-05-19</td>
      <td>2020-05-19</td>
      <td>2020-05-11</td>
      <td>Wake forest</td>
      <td>33</td>
      <td>0.538462</td>
      <td>27460</td>
    </tr>
    <tr>
      <th>2996</th>
      <td>5605b833679597515f7205180b50ea9f</td>
      <td>2020-06-12 01:45:25+00:00</td>
      <td>SAP FICA IS-U Architect (Posted 6-11-20)</td>
      <td>Donnelly &amp; Moore</td>
      <td>2020-06-11</td>
      <td>Contractor</td>
      <td>/0</td>
      <td>108575.0</td>
      <td>2020-07-10</td>
      <td>2020-06-11</td>
      <td>2020-06-12</td>
      <td>2020-06-12</td>
      <td>2020-06-11</td>
      <td>White plains</td>
      <td>32</td>
      <td>0.802198</td>
      <td>74603</td>
    </tr>
    <tr>
      <th>2997</th>
      <td>c74525996c267187b2be11c3c01f3a34</td>
      <td>2020-04-30 01:47:25+00:00</td>
      <td>Data Entry Specialist</td>
      <td>Robert Half</td>
      <td>2020-04-29</td>
      <td>Seasonal/Temp</td>
      <td>/hour</td>
      <td>88469.0</td>
      <td>2020-05-28</td>
      <td>2020-04-29</td>
      <td>2020-04-30</td>
      <td>2020-04-30</td>
      <td>2020-04-22</td>
      <td>Martinez</td>
      <td>4</td>
      <td>0.329670</td>
      <td>08709</td>
    </tr>
    <tr>
      <th>2998</th>
      <td>ee4a13cfc9ce0cb2d66b54b30d5732e6</td>
      <td>2020-06-12 00:57:31+00:00</td>
      <td>Warehouse Associate (Seasonal/ Part-Time/ Full...</td>
      <td>Amazon Fulfillment</td>
      <td>2020-06-11</td>
      <td>Part-Time</td>
      <td>/</td>
      <td>102933.0</td>
      <td>2020-07-10</td>
      <td>2020-06-11</td>
      <td>2020-06-12</td>
      <td>2020-06-12</td>
      <td>2020-06-11</td>
      <td>Rahway</td>
      <td>30</td>
      <td>0.802198</td>
      <td>41693</td>
    </tr>
    <tr>
      <th>2999</th>
      <td>6093631d5e9c136e0b3808e0eaeffb31</td>
      <td>2020-05-07 02:51:11+00:00</td>
      <td>Amazon Warehouse Team Member -Earn up to $15</td>
      <td>Amazon Fulfillment</td>
      <td>2020-05-06</td>
      <td>Full-Time</td>
      <td>/</td>
      <td>82329.0</td>
      <td>2020-06-05</td>
      <td>2020-05-06</td>
      <td>2020-05-07</td>
      <td>2020-05-07</td>
      <td>2020-05-01</td>
      <td>Queens</td>
      <td>32</td>
      <td>0.406593</td>
      <td>96169</td>
    </tr>
  </tbody>
</table>
<p>3000 rows × 17 columns</p>
</div>




```python
from sklearn.model_selection import train_test_split

X = career_data_scaled.drop(columns="salary_offered")
y = career_data_scaled["salary_offered"]

X_train, X_test, y_train, y_test = train_test_split(X,y)
```


```python

```
