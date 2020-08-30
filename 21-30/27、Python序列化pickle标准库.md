![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS8wZTgyODU5My0zZTk2LTQ3ODctYjE0Yy0xNmRhNzFhYzAwMDUucG5n?x-oss-process=image/format,png)




@[toc]

听过Python序列化pickle标准库吗？

# 序列化


序列化 (Serialization)是将对象的状态信息转换为可以存储或传输的形式的过程。就是将数据结构转化成你看不懂的东西


pickle提供四个功能：dumps,dump,loads,load 和json 一样


从小demo入手

```python
import pickle
data = [{'a': 'A', 'b': 2, 'c': 2.22}]
# 使用 pickle.dumps() 可以将一个对象转换为二进制字符串（dump string）：
data_string = pickle.dumps(data)
print("DATA:")
print(data)
print("PICKLE:")
print(data_string)
```

---



```python
DATA:
[{'a': 'A', 'b': 2, 'c': 2.22}]
PICKLE:
b'\x80\x03]q\x00}q\x01(X\x01\x00\x00\x00aq\x02X\x01\x00\x00\x00Aq\x03X\x01\x00\x00\x00bq\x04K\x02X\x01\x00\x00\x00cq\x05G@\x01\xc2\x8f\\(\xf5\xc3ua.'
```


现在给你这个data_string 你能知道这是啥吗？


 虽然 pickle 编码的字符串并不一定可读，但是我们可以用 pickle.loads() 来从这个字符串中恢复原对象中的内容（load string）：

```python
# pickle.loads() 来从这个字符串中恢复原对象中的内容（load string）：
data_from_string = pickle.loads(data_string)
print(data_from_string)
```


dumps 和loads 相反的作用

```python
[{'a': 'A', 'b': 2, 'c': 2.22}]
```







dumps 可以接受一个可省略的 protocol 参数（默认为 0）




```python
data_string_0 = pickle.dumps(data, 0)
print("Pickle 0:", data_string_0)
data_string_1 = pickle.dumps(data, 1)
print("Pickle 1:", data_string_1)
data_string_2 = pickle.dumps(data, 2)
print("Pickle 2:", data_string_2)
# 如果 protocol 参数指定为负数，那么将调用当前的最高级的编码协议进行编码：
print("Pickle -1:", pickle.dumps(data, -1))
```


输出如下


```python
Pickle 0: b'(lp0\n(dp1\nVa\np2\nVA\np3\nsVb\np4\nL2L\nsVc\np5\nL3L\nsa.'
Pickle 1: b']q\x00}q\x01(X\x01\x00\x00\x00aq\x02X\x01\x00\x00\x00Aq\x03X\x01\x00\x00\x00bq\x04K\x02X\x01\x00\x00\x00cq\x05K\x03ua.'
Pickle 2: b'\x80\x02]q\x00}q\x01(X\x01\x00\x00\x00aq\x02X\x01\x00\x00\x00Aq\x03X\x01\x00\x00\x00bq\x04K\x02X\x01\x00\x00\x00cq\x05K\x03ua.'
Pickle -1: b'\x80\x04\x95\x1c\x00\x00\x00\x00\x00\x00\x00]\x94}\x94(\x8c\x01a\x94\x8c\x01A\x94\x8c\x01b\x94K\x02\x8c\x01c\x94K\x03ua.'
```



从这些格式中恢复对象时，不需要指定所用的协议，pickle.load() 会自动识别：

```python
print("Load 1:", pickle.loads(data_string_1))
print("Load 2:", pickle.loads(data_string_2))

OUT：
Load 1: [{'a': 'A', 'b': 2, 'c': 3}]
Load 2: [{'a': 'A', 'b': 2, 'c': 3}]
```



存储和读取 pickle 文件




```python
# 存储和读取 pickle 文件
with open('data.pkl', 'wb') as f:
    pickle.dump(data, f)

with open('data.pkl',"rb") as f:
    data_from_file = pickle.load(f)

print(data_from_file)

# 清理生成的文件：
os.remove('data.pkl')

OUT：
[{'a': 'A', 'b': 2, 'c': 3}]
```

