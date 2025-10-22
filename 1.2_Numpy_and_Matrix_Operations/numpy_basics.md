# 📘 第 1 章：NumPy 简介与数组创建

---

## 🧭 1.1 什么是 NumPy

**NumPy（Numerical Python）** 是 Python 科学计算的基础库，  
用于高效处理 **多维数组（ndarray）** 与 **矩阵运算**。

相比 Python 原生 list：
- NumPy 数组支持 **向量化运算**（速度快）
- 元素类型统一（节省内存）
- 提供大量的数学函数（如 sin、mean、dot）

---

## ⚙️ 1.2 导入 NumPy 模块

```python
import numpy as np   # 通常用 np 作为别名
```
💡 建议在所有项目中统一使用 np，这样代码简洁且通用。
## 🧩 1.3 创建数组的几种方式

NumPy 的核心对象是 ndarray（n-dimensional array）。

### ✅ 方法一：使用 np.array()
```python
import numpy as np

# 创建 Python 列表
data = [1, 2, 3, 4, 5]

# 转换为 NumPy 数组
arr = np.array(data)

print(arr)
print(type(arr))

```
🟢 输出：
```python
[1 2 3 4 5]
<class 'numpy.ndarray'>
```
### ✅ 方法二：使用嵌套列表创建二维数组
```python
arr2d = np.array([[1, 2, 3],
                  [4, 5, 6]])

print(arr2d)
```
🟢 输出：
```lua
[[1 2 3]
 [4 5 6]]
```
💡 NumPy 中二维数组就相当于「矩阵」，支持行列运算。
### ✅ 方法三：使用内置函数创建特定数组
| 函数                              | 说明                          |
| ------------------------------- | --------------------------- |
| `np.zeros(shape)`               | 创建全 0 数组                    |
| `np.ones(shape)`                | 创建全 1 数组                    |
| `np.full(shape, value)`         | 创建固定数值数组                    |
| `np.eye(n)`                     | 创建单位矩阵                      |
| `np.arange(start, stop, step)`  | 创建等差数组（类似 Python `range()`） |
| `np.linspace(start, stop, num)` | 创建线性等分数组                    |
```python
zeros = np.zeros((2, 3))      # 2行3列全0矩阵
ones = np.ones((3, 2))        # 3行2列全1矩阵
arange_arr = np.arange(0, 10, 2)   # 0~10 间隔为2
linspace_arr = np.linspace(0, 1, 5) # 0~1 线性划分5个数

print(zeros)
print(ones)
print(arange_arr)
print(linspace_arr)
```
🟢 输出：
```lua
[[0. 0. 0.]
 [0. 0. 0.]]
[[1. 1.]
 [1. 1.]
 [1. 1.]]
[0 2 4 6 8]
[0.   0.25 0.5  0.75 1.  ]
```
### ✅ 方法四：生成随机数组
```python
rand = np.random.rand(2, 3)   # 均匀分布 [0,1)
randint_arr = np.random.randint(0, 10, (2, 3))  # 随机整数数组

print(rand)
print(randint_arr)
```
📊 随机数在数据模拟、神经网络权重初始化中广泛使用。
## 🔍 1.4 查看数组属性
```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

print(arr.ndim)   # 维度数
print(arr.shape)  # 形状（行, 列）
print(arr.size)   # 元素总数
print(arr.dtype)  # 数据类型
```
🟢 输出：
```lau
2
(2, 3)
6
int64
```
## 🧠 1.5 数据类型转换（dtype）
NumPy 数组类型统一，可以通过 astype() 转换类型。
```python
arr = np.array([1.5, 2.8, 3.2])
arr_int = arr.astype(int)

print(arr)
print(arr_int)

```
🟢 输出：
```
[1.5 2.8 3.2]
[1 2 3]
```
💡 astype() 会生成新数组，不改变原数据。
## ⚡ 小结
| 操作类别    | 常用函数                                                  |
| ------- | ----------------------------------------------------- |
| 从列表创建   | `np.array()`                                          |
| 生成特殊数组  | `np.zeros()` / `np.ones()` / `np.full()` / `np.eye()` |
| 等差 / 等分 | `np.arange()` / `np.linspace()`                       |
| 随机数组    | `np.random.rand()` / `np.random.randint()`            |
| 查看属性    | `.shape` / `.ndim` / `.dtype`                         |
| 类型转换    | `.astype()`                                           |
# 📘 第 2 章：数组属性与索引切片

## 🧭 2.1 数组属性回顾
```python
import numpy as np

arr = np.array([[1, 2, 3],
                [4, 5, 6],
                [7, 8, 9]])

print(arr.ndim)   # 数组维度
print(arr.shape)  # 形状（行, 列）
print(arr.size)   # 元素总数
print(arr.dtype)  # 数据类型
```
🟢 输出：
```
2
(3, 3)
9
int64
```

## 🎯 2.2 一维数组的索引与切片
```python
a = np.array([10, 20, 30, 40, 50])

print(a[0])       # 第一个元素
print(a[-1])      # 最后一个元素
print(a[1:4])     # 从索引1到3
print(a[:3])      # 前3个元素
print(a[::2])     # 间隔取值（步长2）
```
🟢 输出：
```
10
50
[20 30 40]
[10 20 30]
[10 30 50]
```

## 🧩 2.3 二维数组的索引
```python
b = np.array([[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9]])

print(b[0, 0])  # 第一行第一列
print(b[1, 2])  # 第二行第三列
print(b[2, :])  # 第三行全部
print(b[:, 1])  # 所有行第二列
```
🟢 输出：
```
1
6
[7 8 9]
[2 5 8]
```

## 🧠 2.4 切片修改与视图机制
```python
c = np.array([1, 2, 3, 4, 5])
d = c[1:4]       # 取出切片视图
d[:] = 0          # 修改视图内的值
print(c)          # 原数组也会变化
```
🟢 输出：
```
[1 0 0 0 5]
```
```python
e = c[1:4].copy()
e[:] = 9
print(c)   # 原数组不变
print(e)
```
🟢 输出：
```
[1 0 0 0 5]
[9 9 9]
```

## 🧮 2.5 布尔索引与条件筛选
```python
arr = np.array([10, 15, 20, 25, 30])
mask = arr > 20
print(mask)
print(arr[mask])
```
🟢 输出：
```
[False False False  True  True]
[25 30]
```

## 🔁 2.6 Fancy Index（花式索引）
```python
a = np.array([10, 20, 30, 40, 50])
idx = [0, 2, 4]
print(a[idx])
```
🟢 输出：
```
[10 30 50]
```
```python
b = np.arange(12).reshape(3, 4)
print(b[[0, 2], [1, 3]])
```
🟢 输出：
```
[1 11]
```

## ⚡ 小结
| 操作类型 | 示例 |
|-----------|-------|
| 一维索引 | `a[2]` |
| 二维索引 | `a[1, 3]` |
| 切片 | `a[1:4]`, `a[:, 2]` |
| 布尔索引 | `a[a > 0]` |
| 花式索引 | `a[[0,2,4]]` |
| 深拷贝 | `.copy()` |
# 📗 第 3 章：数组运算与广播机制

## ⚙️ 3.1 数组的基本运算
```python
import numpy as np

a = np.array([1, 2, 3, 4])
b = np.array([10, 20, 30, 40])

print(a + b)  # 加法
print(a - b)  # 减法
print(a * b)  # 乘法（逐元素）
print(b / a)  # 除法（逐元素）
```
🟢 输出：
```
[11 22 33 44]
[ -9 -18 -27 -36]
[ 10  40  90 160]
[10. 10. 10. 10.]
```

## 📈 3.2 数组与标量运算
```python
arr = np.array([1, 2, 3, 4, 5])

print(arr * 2)   # 所有元素乘以2
print(arr + 10)  # 所有元素加10
```
🟢 输出：
```
[2 4 6 8 10]
[11 12 13 14 15]
```

> 💡 NumPy 自动对标量广播到所有元素。

## 🧮 3.3 通用函数（ufunc）
NumPy 提供大量**通用函数（universal functions）**，对数组逐元素运算。
```python
arr = np.array([0, 1, 2, 3])

print(np.sqrt(arr))  # 平方根
print(np.exp(arr))   # e^x
print(np.sin(arr))   # 正弦
print(np.log(arr + 1))  # 自然对数（避免log(0)）
```
🟢 输出：
```
[0.         1.         1.41421356 1.73205081]
[ 1.          2.71828183  7.3890561  20.08553692]
[ 0.          0.84147098  0.90929743  0.14112001]
[0.         0.69314718 1.09861229 1.38629436]
```

## 🧭 3.4 广播机制（Broadcasting）
广播允许不同形状的数组参与运算。

```python
a = np.array([1, 2, 3])
b = np.array([[10], [20], [30]])

print(a + b)
```
🟢 输出：
```
[[11 12 13]
 [21 22 23]
 [31 32 33]]
```

> 💡 NumPy 自动扩展维度以匹配形状。

## ⚡ 3.5 数组比较与逻辑运算
```python
a = np.array([1, 2, 3])
b = np.array([2, 2, 2])

print(a == b)
print(a > b)
print(np.logical_and(a > 0, b < 3))
```
🟢 输出：
```
[False  True False]
[False False  True]
[ True  True False]
```

## 📊 3.6 统计运算
```python
arr = np.array([[1, 2, 3],
                [4, 5, 6]])

print(arr.sum())        # 总和
print(arr.mean())       # 均值
print(arr.max())        # 最大值
print(arr.min())        # 最小值
print(arr.std())        # 标准差
print(arr.var())        # 方差
print(arr.sum(axis=0))  # 按列求和
print(arr.sum(axis=1))  # 按行求和
```
🟢 输出：
```
21
3.5
6
1
1.707825127659933
2.9166666666666665
[5 7 9]
[ 6 15]
```

## 🎯 3.7 矩阵点积与线性代数
```python
a = np.array([[1, 2],
              [3, 4]])
b = np.array([[5, 6],
              [7, 8]])

print(np.dot(a, b))  # 矩阵乘法
print(a @ b)         # 等价写法
```
🟢 输出：
```
[[19 22]
 [43 50]]
```

## 🧠 3.8 其他常用函数
| 函数 | 说明 |
|------|------|
| `np.clip(a, min, max)` | 限制元素范围 |
| `np.round(a, n)` | 四舍五入 |
| `np.sort(a)` | 排序 |
| `np.argsort(a)` | 返回排序索引 |
| `np.unique(a)` | 去重 |

示例：
```python
arr = np.array([10, 5, 8, 5, 10])
print(np.unique(arr))
print(np.sort(arr))
print(np.argsort(arr))
```
🟢 输出：
```
[ 5  8 10]
[ 5  5  8 10 10]
[1 3 2 0 4]
```

## ✅ 小结
| 操作类型 | 示例 |
|-----------|-------|
| 基本算术 | `+ - * /` |
| 通用函数 | `np.sqrt()`、`np.exp()` |
| 统计函数 | `np.mean()`、`np.std()` |
| 线性代数 | `np.dot()`、`@` |
| 广播机制 | 自动扩展维度 |
| 比较与逻辑 | `==`、`>`、`np.logical_and()` |
