## 什么是Numpy?

NumPy 是 Python 中科学计算的基础包。它是一个 Python 库，提供多维数组对象、各种派生对象（例如掩码数组和矩阵）以及用于对数组进行快速操作的各种例程，包括数学、逻辑、形状操作、排序、选择、I/O 、离散傅里叶变换、基本线性代数、基本统计运算、随机模拟等等。

NumPy 包的核心是 ndarray 对象。这封装了同类数据类型的 n 维数组，许多操作在编译代码中执行以提高性能。 NumPy 数组和标准 Python 序列之间有几个重要的区别：

- NumPy 数组在创建时具有固定大小，这与 Python 列表（可以动态增长）不同。更改 ndarray 的大小将创建一个新数组并删除原始数组。

- NumPy 数组中的所有元素必须是相同的数据类型,因此在内存中大小相同。例外情况:可以有对象数组(包括 Python 和 NumPy 对象),从而允许不同大小的元素。例如：

  ```python
  import numpy as np
  
  # 普通数组,要求相同类型(float64)
  arr = np.array([1.2, 2.3, 3.4]) 
  
  # 对象数组,允许不同类型
  obj_arr = np.array([1.2, "hello", np.nan]) 
  ```

  

- NumPy 数组促进了大量数据的高级数学和其他类型的运算。通常，这样的运算比使用 Python 内置序列执行得更高效和代码更少。例如，做一个向量点乘：

  使用 Numpy：

  ```python
  a = np.array([1, 2, 3])
  b = np.array([4, 5, 6])
  np.dot(a, b)  # 32
  ```

  使用 Python 列表：

  ```python
  a = [1, 2, 3]
  b = [4, 5, 6]
  result = 0
  for i in range(len(a)):
      result += a[i] * b[i]  # 32
  ```

  

- 越来越多的基于 Python 的科学和数学软件包都在使用 NumPy 数组。虽然这些软件包通常支持 Python 序列输入,但在处理之前会将此输入转换为 NumPy 数组,并且通常输出 NumPy 数组。换言之,为了有效地使用今天大部分(甚至可能是大多数)基于 Python 的科学/数学软件,仅知道如何使用 Python 内置序列类型是不足够的，您也需要知道如何使用 NumPy 数组。

- 在科学计算中,序列的大小和运算速度是如此重要。如果数据存储在两个 Python 列表 `a` 和 `b` 中,我们可以像这样迭代每个元素:

  ```python
  result = []
  for i in range(len(a)):
      result.append(a[i] * b[i])
  ```

  但是,如果 `a` 和 `b` 都是长度为 10 的列表,那么上面的代码还好,但如果两个列表长度是 10 的 6 次方(1 百万),那么上述代码的效率就会非常低下。换成 NumPy 数组,情况就完全不同了:

  ```python
  import numpy as np
  
  a = np.array([1, 2, 3, 4, 5]) 
  b = np.array([2, 3, 4, 5, 6])
  
  np.multiply(a, b)  # array([ 2,  6, 12, 20, 30])
  ```

  NumPy 利用底层 C 语言实现,可以高效处理大规模的数组运算,这就是为什么在科学计算中 NumPy 数组如此重要的原因。如果两个 NumPy 数组的长度是 10 的 6 次方,上述代码运算起来也是非常高效的,这就是 NumPy 的强大之处。



## 还有谁使用 Numpy?

NumPy 完全支持面向对象的方法。NumPy 的核心 *ndarray* 是一个类,完全支持面向对象的方法。*ndarray* 类拥有许多方法和属性,用于构造和操作数组。*ndarray* 类的许多方法都有对应的 NumPy 函数,可以选择对象方法或函数来使用。这种方法选择的灵活性,使得 NumPy 成为 Python 处理多维数据的事实标准。例如：

对象方法:

```python
arr = np.array([[1, 2], [3, 4]])
arr.transpose()  # [[1 3]  
                 #  [2 4]]
```

函数：

```python
np.transpose(arr)  # [[1 3]
                   #  [2 4]]
```

 NumPy 同时提供面向对象的和函数式的方法来操纵数组,使用哪种完全由个人喜好决定,这使得 NumPy 具有很大的灵活性,可以满足不同程序员的需求。