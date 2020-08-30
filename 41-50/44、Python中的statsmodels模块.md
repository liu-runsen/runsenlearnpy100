

@Author：Runsen


@[toc]

# statsmodels入门
这个非常简单的案例研究旨在让您快速上手 statsmodels。从原始数据开始，我们将展示估计统计模型和绘制诊断图所需的步骤。我们只使用由statsmodels它或它pandas和patsy 依赖项提供的函数。

来源：http://www.statsmodels.org/stable/gettingstarted.html



```python
import statsmodels.api as sm
import pandas
from patsy import dmatrices # patsy用于描述统计模型和使用类似公式构建设计矩阵R
#下载了Guerry数据集，这是一组历史数据，用于支持Andre-Michel Guerry在1833年 关于法国道德统计的论文。

df = sm.datasets.get_rdataset("Guerry", "HistData").data
```


```python
df.head()
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
      <th>dept</th>
      <th>Region</th>
      <th>Department</th>
      <th>Crime_pers</th>
      <th>Crime_prop</th>
      <th>Literacy</th>
      <th>Donations</th>
      <th>Infants</th>
      <th>Suicides</th>
      <th>MainCity</th>
      <th>...</th>
      <th>Crime_parents</th>
      <th>Infanticide</th>
      <th>Donation_clergy</th>
      <th>Lottery</th>
      <th>Desertion</th>
      <th>Instruction</th>
      <th>Prostitutes</th>
      <th>Distance</th>
      <th>Area</th>
      <th>Pop1831</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>E</td>
      <td>Ain</td>
      <td>28870</td>
      <td>15890</td>
      <td>37</td>
      <td>5098</td>
      <td>33120</td>
      <td>35039</td>
      <td>2:Med</td>
      <td>...</td>
      <td>71</td>
      <td>60</td>
      <td>69</td>
      <td>41</td>
      <td>55</td>
      <td>46</td>
      <td>13</td>
      <td>218.372</td>
      <td>5762</td>
      <td>346.03</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>N</td>
      <td>Aisne</td>
      <td>26226</td>
      <td>5521</td>
      <td>51</td>
      <td>8901</td>
      <td>14572</td>
      <td>12831</td>
      <td>2:Med</td>
      <td>...</td>
      <td>4</td>
      <td>82</td>
      <td>36</td>
      <td>38</td>
      <td>82</td>
      <td>24</td>
      <td>327</td>
      <td>65.945</td>
      <td>7369</td>
      <td>513.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>C</td>
      <td>Allier</td>
      <td>26747</td>
      <td>7925</td>
      <td>13</td>
      <td>10973</td>
      <td>17044</td>
      <td>114121</td>
      <td>2:Med</td>
      <td>...</td>
      <td>46</td>
      <td>42</td>
      <td>76</td>
      <td>66</td>
      <td>16</td>
      <td>85</td>
      <td>34</td>
      <td>161.927</td>
      <td>7340</td>
      <td>298.26</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>E</td>
      <td>Basses-Alpes</td>
      <td>12935</td>
      <td>7289</td>
      <td>46</td>
      <td>2733</td>
      <td>23018</td>
      <td>14238</td>
      <td>1:Sm</td>
      <td>...</td>
      <td>70</td>
      <td>12</td>
      <td>37</td>
      <td>80</td>
      <td>32</td>
      <td>29</td>
      <td>2</td>
      <td>351.399</td>
      <td>6925</td>
      <td>155.90</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>E</td>
      <td>Hautes-Alpes</td>
      <td>17488</td>
      <td>8174</td>
      <td>69</td>
      <td>6962</td>
      <td>23076</td>
      <td>16171</td>
      <td>1:Sm</td>
      <td>...</td>
      <td>22</td>
      <td>23</td>
      <td>64</td>
      <td>79</td>
      <td>35</td>
      <td>7</td>
      <td>1</td>
      <td>320.280</td>
      <td>5549</td>
      <td>129.10</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 23 columns</p>
</div>




```python
df.columns
```




    Index(['dept', 'Region', 'Department', 'Crime_pers', 'Crime_prop', 'Literacy',
           'Donations', 'Infants', 'Suicides', 'MainCity', 'Wealth', 'Commerce',
           'Clergy', 'Crime_parents', 'Infanticide', 'Donation_clergy', 'Lottery',
           'Desertion', 'Instruction', 'Prostitutes', 'Distance', 'Area',
           'Pop1831'],
          dtype='object')




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 86 entries, 0 to 85
    Data columns (total 23 columns):
    dept               86 non-null int64
    Region             85 non-null object
    Department         86 non-null object
    Crime_pers         86 non-null int64
    Crime_prop         86 non-null int64
    Literacy           86 non-null int64
    Donations          86 non-null int64
    Infants            86 non-null int64
    Suicides           86 non-null int64
    MainCity           86 non-null object
    Wealth             86 non-null int64
    Commerce           86 non-null int64
    Clergy             86 non-null int64
    Crime_parents      86 non-null int64
    Infanticide        86 non-null int64
    Donation_clergy    86 non-null int64
    Lottery            86 non-null int64
    Desertion          86 non-null int64
    Instruction        86 non-null int64
    Prostitutes        86 non-null int64
    Distance           86 non-null float64
    Area               86 non-null int64
    Pop1831            86 non-null float64
    dtypes: float64(2), int64(18), object(3)
    memory usage: 15.5+ KB
    


```python
# 在地区Region  85 non-null object有缺失值
df = df.dropna()
```

法国86个省的识字率是否与19世纪20年代皇家彩票的人均赌注有关。

我们需要控制每个部门的财富水平，在回归方程的右侧包含一系列虚拟变量，以控制由于区域效应而导致的未观察到的异质性。


**使用普通最小二乘回归（OLS）估计模型。**






```python
# 使用patsy的dmatrices函数来创建设计矩阵
#  y 是一个 N×1关于人均彩票投注数据的一栏（彩票）。X 是 N×7带有截距， 识字和财富变量，以及4个区域二进制变量
y, X = dmatrices('Lottery ~ Literacy + Wealth + Region', data=df, return_type='dataframe')
```


```python
y[:3]
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
      <th>Lottery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>41.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>38.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>66.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
X[:3]
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
      <th>Intercept</th>
      <th>Region[T.E]</th>
      <th>Region[T.N]</th>
      <th>Region[T.S]</th>
      <th>Region[T.W]</th>
      <th>Literacy</th>
      <th>Wealth</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>37.0</td>
      <td>73.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>51.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>13.0</td>
      <td>61.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 模型拟合和总结
mod = sm.OLS(y, X)    # Describe model

res = mod.fit()       # Fit model

print(res.summary())   # Summarize model
```

                                OLS Regression Results                            
    ==============================================================================
    Dep. Variable:                Lottery   R-squared:                       0.338
    Model:                            OLS   Adj. R-squared:                  0.287
    Method:                 Least Squares   F-statistic:                     6.636
    Date:                Thu, 09 May 2019   Prob (F-statistic):           1.07e-05
    Time:                        18:02:22   Log-Likelihood:                -375.30
    No. Observations:                  85   AIC:                             764.6
    Df Residuals:                      78   BIC:                             781.7
    Df Model:                           6                                         
    Covariance Type:            nonrobust                                         
    ===============================================================================
                      coef    std err          t      P>|t|      [0.025      0.975]
    -------------------------------------------------------------------------------
    Intercept      38.6517      9.456      4.087      0.000      19.826      57.478
    Region[T.E]   -15.4278      9.727     -1.586      0.117     -34.793       3.938
    Region[T.N]   -10.0170      9.260     -1.082      0.283     -28.453       8.419
    Region[T.S]    -4.5483      7.279     -0.625      0.534     -19.039       9.943
    Region[T.W]   -10.0913      7.196     -1.402      0.165     -24.418       4.235
    Literacy       -0.1858      0.210     -0.886      0.378      -0.603       0.232
    Wealth          0.4515      0.103      4.390      0.000       0.247       0.656
    ==============================================================================
    Omnibus:                        3.049   Durbin-Watson:                   1.785
    Prob(Omnibus):                  0.218   Jarque-Bera (JB):                2.694
    Skew:                          -0.340   Prob(JB):                        0.260
    Kurtosis:                       2.454   Cond. No.                         371.
    ==============================================================================
    
    Warnings:
    [1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
    


```python
res.params
```




    Intercept      38.651655
    Region[T.E]   -15.427785
    Region[T.N]   -10.016961
    Region[T.S]    -4.548257
    Region[T.W]   -10.091276
    Literacy       -0.185819
    Wealth          0.451475
    dtype: float64




```python
# 应用Rainbow测试线性度
print(sm.stats.linear_rainbow(res))#第一个数字是F统计量，第二个数字是p值。
sm.graphics.plot_partregress('Lottery', 'Wealth', ['Region', 'Literacy'],
                          data=df, obs_labels=False)
```

    (0.847233997615691, 0.6997965543621644)
    






![](https://img-blog.csdnimg.cn/20190509180722494.png)

对于statsmodels确实是一个值得学习的机器学习库

参考：http://www.statsmodels.org/stable/gettingstarted.html
