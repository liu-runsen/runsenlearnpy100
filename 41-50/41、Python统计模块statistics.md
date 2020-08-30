@Author：Runsen



@[TOC]


官网：  https://docs.python.org/3/library/statistics.html
# Python统计模块statistics
statistics 模块实现了许多常用的统计公式，以便使用 Python 的各种数值类型（int，float，Decimal 和 Fraction）进行高效的计算。






```python
# 计算平均数
import statistics


data = [1,2,3,4,5.6]

print(statistics.mean(data))# 3.12
# 等同于

print(sum(data)/len(data))
```

    3.12
    3.12
    


```python
# mode 众数
data = [1,2,3,4,5,1]
statistics.mode(data)
```




    1



# median－中位数
- median-low()－中位数(如果项数是偶数，返回小值)
- median-high()－中位数(如果项数是偶数，返回大值)
- median-grouped() - j将数字排序好再选择中位数



```python
print(statistics.median([1, 3, 5, 7]))
print(statistics.median_low([1, 3, 5, 7]))
print(statistics.median_high([1, 3, 5, 7]))
print(statistics.median_grouped([5, 3, 7]))
```

    4.0
    3
    5
    5.0
    
# 方差

**计算样本方差（sample variance）和样本标准差（sample standard deviation，the square root of the sample variance，也叫均方差）。** 


```python
# variance()－方差
data = [1, 2,  3, 3, 4]
statistics.variance(data)  # 1.3
# stdev－标准差
statistics.stdev(data) # 1.140175425099138
```









```python
# pvariance()－总体方差
statistics.pvariance([1.5, 2.5, 2.5, 2.75, 3.25, 4.75])
```




    0.9739583333333334




```python
### pstdev() -- 返回总体标准差（)。
### pvariance() --返回总体方差（)。

statistics.pstdev(data) # 1.019803902718557
statistics.pvariance(data)# 1.04
```


https://docs.python.org/3/library/statistics.html

