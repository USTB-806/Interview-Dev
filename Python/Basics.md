## 数据类型与变量

- Python 中内置的数据类型包括数字（int、float）、字符串（str）、布尔值（bool）、列表（list）、元组（tuple）、字典（dict）和集合（set）。

### 整数和浮点数
- 整数（int）表示整数，如 `42`。浮点数（float）表示小数，如 `3.14`。
- 支持基本运算：加法 `+`、减法 `-`、乘法 `*`、除法 `/`（返回float）、整除 `//`、取余 `%`、幂 `**`。

  ```python
  a = 10  # int
  b = 3.5  # float
  print(a + b)  # 输出: 13.5
  print(a // 3)  # 输出: 3 (整除)
  ```

### 字符串
- 字符串（str）是字符序列，用单引号或双引号包围，如 `"hello"` 或 `'world'`。
- 支持索引、切片、拼接和格式化。不可变类型。

  ```python
  s = "Python"
  print(s[0])  # 输出: P
  print(s[1:4])  # 输出: yth
  print(s + " is fun")  # 输出: Python is fun
  print(f"Hello, {s}")  # 输出: Hello, Python
  ```

### 布尔值
- 布尔值（bool）只有两个值：`True` 和 `False`。
- 用于条件判断，常来自比较运算符：`==`、`!=`、`<`、`>`、`<=`、`>=`。

  ```python
  x = 5
  y = 10
  print(x < y)  # 输出: True
  print(x == y)  # 输出: False
  ```

### 列表
- 列表（list）是有序、可变序列，用方括号 `[]` 表示，如 `[1, 2, 3]`。
- 支持索引、切片、添加/删除元素。元素可以是不同类型。

  ```python
  my_list = [1, "apple", 3.14]
  print(my_list[1])  # 输出: apple
  my_list.append(4)  # 添加元素
  print(my_list)  # 输出: [1, 'apple', 3.14, 4]
  my_list.remove("apple")  # 删除元素
  print(my_list)  # 输出: [1, 3.14, 4]
  ```

### 元组
- 元组（tuple）是有序、不可变序列，用圆括号 `()` 表示，如 `(1, 2, 3)`。
- 类似列表，但不可修改。用于固定数据。

  ```python
  my_tuple = (1, "banana", 2.5)
  print(my_tuple[0])  # 输出: 1
  # my_tuple[0] = 5  # 会报错，因为不可变
  print(len(my_tuple))  # 输出: 3
  ```

### 字典
字典使用键值对存储数据，键必须是不可变类型（如字符串、数字或元组），值可以是任意类型，具有极快的查找速度。


- 字典如何删除键和合并两个字典
  - 删除键：使用 `del` 语句或 `pop()` 方法。

    ```python
    dict = {'a': 1, 'b': 2, 'c': 3}
    del dict['b']  # 删除键 'b'
    print(dict)  # 输出: {'a': 1, 'c': 3}
    dict.pop('c')  # 删除键 'c'
    print(dict)  # 输出: {'a': 1}
    ```

    当尝试删除一个不存在的键时，del 和 pop() 都会引发 `KeyError` 异常。
    但是在正常使用 pop 方法时，会返回被删除键的值。

    ```python
    dict = {'a': 1, 'b': 2, 'c': 3}
    print(dict.pop('b'))  # 输出: 2
    print(dict)  # 输出: {'a': 1, 'c': 3}
    ```

  - 合并字典：使用 `update()` 方法或字典解包（Python 3.5+）。

    ```python
    dict1 = {'a': 1, 'b': 2}
    dict2 = {'b': 3, 'c': 4}
    dict1.update(dict2)
    print(dict1)  # 输出: {'a': 1, 'b': 3, 'c': 4}
    ```
### 集合
set 和 dict 类似，也是一组 key 的集合，但不存储 value。由于 key 不能重复，所以，在 set 中，没有重复的key。

- 列表去重
    ```python
    my_list = [1, 2, 2, 3, 4, 4, 5]
    my_set = set(my_list)  # 使用 set 去重
    unique_list = list(my_set)  # 转换回列表
    ```

## 常见题目

### 列表推导式
- 简洁创建列表。

  ```python
  # 传统方式
  squares = []
  for x in range(10):
      squares.append(x**2)

  # 推导式
  squares = [x**2 for x in range(10)]
  print(squares)  # 输出: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
  ```

### 字符串操作
- 反转字符串。

  ```python
  s = "hello"
  reversed_s = s[::-1]
  print(reversed_s)  # 输出: olleh
  ```

### python 中 == 和 is 的区别
- `==` 用于比较两个对象的值是否相等，而 `is` 用于比较两个对象的身份（即它们是否是同一个对象）。
  
  ```python
  a = [1, 2, 3]
  b = a
  c = [1, 2, 3]

  print(a == b)  # 输出: True (值相等)
  print(a is b)  # 输出: True (在内存中地址相同)

  print(a == c)  # 输出: True (值相等)
  print(a is c)  # 输出: False (内存地址不同)
  ```

### 如何将字符串转换为整数

- 使用 `int()` 函数。

  ```python
  s = "123"
  num = int(s)
  print(num)  # 输出: 123
  print(type(num))  # 输出: <class 'int'>
  ```

### 深浅拷贝的区别
- 浅拷贝（shallow copy）创建一个新的对象，但不复制
  嵌套对象的引用。深拷贝（deep copy）创建一个新的对象，并递归复制所有嵌套对象。

  ```python
  import copy

  original = [1, 2, [3, 4]]
  shallow_copied = copy.copy(original)
  deep_copied = copy.deepcopy(original)

  original[2][0] = 'changed'

  print(original)        # 输出: [1, 2, ['changed', 4]]
  print(shallow_copied) # 输出: [1, 2, ['changed', 4]] (嵌套对象被修改)
  print(deep_copied)    # 输出: [1, 2, [3, 4]] (嵌套对象未被修改)
  ```
