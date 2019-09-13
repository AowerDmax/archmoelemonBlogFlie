---
title: Python数据分析基础语法
date: 2019-07-15 14:02:45
tags:
- Python
- Python基础
---

# 数据类型

### 常用数据类型

| **属性** | **类型** |     例子     |
| :------: | :------: | :----------: |
|  电影名  |  字符串  | 肖申克的救赎 |
| 观影人数 |   整数   |    692795    |
|   评分   |  浮点数  |     9.6      |
| 中国大陆 |  布尔值  |    False     |
|  投资额  |   空值   |     None     |

#### 字符串

字符串的定义是使用引号来定义，单引号于双引号是等价的

三引号用来输入包含多行文字的字符串

```python
s = '''hello
my
world'''
print(s)
```

字符串的加法

```python
s = 'hello' + 'world'
s
```

字符串的索引

把字符串中的单个字母拿出来， 下标从零开始

```python
s[0]
```

字符串的分割

默认用空格进行分割

```python
s = 'hello world'
s.split( )
a = 'hello,world'
s.split(',')
```

查看字符串的长度

```python
len(s)
```

#### 整数

#### 浮点数


#### 布尔值


```python
a = True
a
a = 1 > 2
a = False
```

#### 空值

```python
a = ''
a
len(a)
a = None
a
```

### 运算符描述



|  +   | 两数相加 |
| :--: | :------: |
|  -   | 两数相减 |
|  *   | 两数相乘 |
|  /   | 两数相除 |
|  %   |   取模   |
|  //  | 相除取整 |
|  **  | 去幂次方 |

#### 比较运算

|  ==  |   等于   |
| :--: | :------: |
|  !=  |  不等于  |
|  <>  |  不等于  |
|  >   |   大于   |
|  <   |   小于   |
|  >=  | 大于等于 |
|  <=  | 小于等于 |

#### 赋值运算

|  =   |   a = 3    |
| :--: | :--------: |
|  +=  | a = a + 3  |
|  -=  | a = a - 3  |
|  *=  | a = a * 3  |
|  /=  | a = a / 3  |
|  %=  | a = a % 3  |
| **=  | a = a ** 3 |
| //=  | a = a // 3 |

#### 逻辑运算

| and  |  &   |
| :--: | :--: |
|  or  |  \|  |
| not  | not  |

```python
a = 5 > 4
b = True
not a
a|b
a&b
```

## 数据结构

#### 列表List

Python用[]来生成列表， 也可以用list关键字

列表操作

一定要是英文状态的逗号和单引号

列表里面允许各个元素的数据类型不一样

```python
a = [1, 2, 3, 4, 5]
a
actors = ['Tyrion', 'Smith', 'Jogger']
actors
b = [1, 2.3, 'Tyrion']
b
list('abcde')
```

##### 列表的操作

```python
#列表的相加
a+b
#列表的取值
a[0] #索引从0开始
#增加列表
#在末尾增加
a.append()#可以增加各种不同的数据类型
#在特定位置增加
a.insert(1, 10)#在列表的坐标的位置为1的地方插入10这个元素
#删除列表的元素
#默认删除最后的一个元素
a.pop()
a.pop(1)#删除列表的坐标的位置为1的元素
#数据切片
a[0:3]#左闭右开
#取出列表a的第0， 1， 2个元素
a[:3]
#默认从最开头取出元素
a[0:]
#默认取到列表的最后一个元素
#允许有负数， 相当于一个环
a[0:-1]#除了最后一个元素没有被取出来，其他全部都被取出来
#间隔取值
a[2:9:3]
#从索引号2开始取值， 到索引号9结束， 9不被包括， 间隔为3
```



#### 元组tuple

另一种有序列表叫做元组：tuple，用()来表示。 tuple和list非常类似，但是tuple一旦被初始化就**不能被修改**

```python
a = (1, 2, 3, 4, 5, 6)
经常当作常数来使用
#其他的操作和list相同，除了插入修改
append不能使用
insert不能使用
pop不能使用
可以使用索引
a[0]
可以使用切片
a[0:]
```



#### 字典dict

Python用{ key: value }来生成Dictionary

```python
mv = {'name':'肖申克的救赎', 'actor':'Tyrion', 'score':'9.6', 'country':'American'}
#数据类型可以是不同的数据类型
mv
mv['name']
#查看字典中所有的keys
mv.keys()
#查看字典中所有的value
mv.value()
#查看字典中所有的items
mv.items()
#修改字典中的元素
#修改
mv['name'] = '泰坦尼克号'
#插入
mv['directors'] = '德拉邦特'
#删除
mv.pop('directors')

```



#### 集合set

Python用{}来生成集合， 集合中不含有相同的元素

```python
s1 = {2, 3, 4, 2}
s1
len(s1)
#增加元素
s1.add()
#集合的交并集的概念
s2 = {1， 2， 4， 7， 9}
s1&s2 #做交集
s1|s2 #做并集
s1 - s2 #属于s1 但是 不属于 s2 的元素
s2 - s1 #属于s2 但是 不属于 s1 的元素
```

## 可变对象和不可变对象

可变对象可以对其进行插入，删除等操作， 

不可变对象不可以对其进行有改变的操作

python中列表（list） 字典（dictionary）集合（set）都是可变的

元组（tuple）整型，字符串都是不可变的

#### 类型转换

```python
int(3.14)
float(3)
s = 'abcd'
type(s)
list(s)
```

#### 判断和循环

python里面是区分大小写的

```python
2 == 2
3 == 'a'
if 2 > 1:
    print('hello')
else:
    print('world')
x = 0
if x > 0:
    print('True')
elif x == 0:
    print('Zero')
else:
    print('False')
#循环
#for循环
for i in [1,2,3,4,5,6]:
    print(i)
#while循环
i = 1
while i < 10:
    print(i)
    i+=1
for i in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]:
    if i % 2 == 1:
        print(i)
```

#### 列表生成式

列表生成式即List Comprehension， 是python内置的非常简单却强大的可以用来创建list的生成式

```
list(range(1, 11))
#左闭右开
[x**2 for x in range(1, 10)]
[i for i in range(1, 100) if i%10==0]
[str(x) for x in range(1, 10)]
[int(x) for x in list('123456789')]
```

## python函数

#### 内置函数

```python
#取绝对值函数
abs(-1)
a = [2, 3, -1, 4]
#找到最大的值
max(a)
#找到最小的值
min(a)
#求和
sum(a)

```

#### 自定义函数

函数function， 通常接受输入参数， 并有返回值

它负责完成某项特定的任务， 而且相较于其他代码，具备相对的独立性

函数通常有以下的几个特征：

* 使用def关键字来定义一个函数
* def后面是函数的名称， 括号是函数的参数， 不同的参数用， 隔开， def func():的形式是必须要有的，参数可以为空； 
* 使用缩进来划分函数的内容 
* return 返回特定的值， 如果省略， 返回None



使用函数时， 只需要将参数换成特定的值传给函数

**python**中并没有限定参数的类型，因此可以使用不同的参数类型：

在这个例子中， 如果传入的两个参数不可以相加， 那么**python**会将报错：

如果传入的参数数目与实际不符合， 也会报错：

可以在函数定义的时候给参数设定默认值

```python
def add(a, b):
    return a+b
def func(x, a = 1, b = 0, c = 0):
    return a*x**2+b*x+c
def f(x):
    return x**2, x**3
#f(2), return (4, 8)元组常数，不可以更改

```

### 第一作业总结

1. 列表生成式

   ```python
   [f(i) for i in range(begin , end) if i != error] 
   ```

2. 判断一个数字或者一个字符串是否在一个列表当中

   ```python
   want_find in list1
   ```

3. 数据切片

   ```python
   #倒序输出
   i[::-1]
   #奇数输出
   i[::2]
   #偶数输出
   i[1::2]
   ```