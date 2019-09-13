---
title: R语言基本语法与绘图指北
date: 2019-07-21 11:03:50
tags:
- R语言
- 绘图
---

本来想要昨天晚上完成第二篇文章的， 但是发现把学习笔记放在自己的博客上并托管到GitHub上之后， 后期查找的时候并不是特别方便， 所以昨天一直捣弄GitBook， 确实还算不错， 先试用一段时间吧， 如果好用的话， 会后续写一篇入门教程 h h

那么就开始今天的主题，R语言的基本语法与绘图指北

图像可以说是最直观的内容呈现形式了， 所以我们做研究的时候往往需要绘制专业并且美观的图片， 所以今天我首推的工具就是R语言

为什么要学习R语言？

1. 免费，开源
2. 专业的统计分析软件
3. 作图能力强
4. 对各种平台和数据源的兼容性强

## R语言基本语法

R语言在使用中可以使用Tab键进行代码的自动补全

在R中可以通过ctrl+enter运行当前行（和jupyter notebook一样的h h）

可以用shift + enter 把代码整体下移一行

### 变量赋值

```R
a <- 10
b <- 10
#可能很多人都感觉这个好奇怪， 其实把<-看成箭头， 指向变量
#是不是就很容易记住了
c <- "课程"
#在给字符串赋值的时候需要使用双引号
d <- c(1, 2, 3, 4)
#c指的是combine， 组合 ，将这些元素组合成为一个组
```

### 运算

```R
a <- 5
b <- 2
#给a， b赋值
a/5
#a除以b， 结果为2.5
a*5
#a乘以b， 结果为10
a+b
#a加b
a-b
#a减b
a^3
#a的三次方
a%%b
#a对b取余， 结果为1
a%/%b
#a对b整出， 结果为2
```

|  <   |   小于   |
| :--: | :------: |
|  <=  | 小于等于 |
|  ==  |   等于   |
|  !=  |  不等于  |
|  !x  |    非    |
| x\|y |    或    |
| x&y  |    与    |

### 控制结构

```R
# [0, 60)不合格， [60, 80)合格[80， 100]优秀
grade<-45
{
    if(grade>=80)
        print("优秀")
    else if(grade>=60)
        print("合格")
    else
        print("不合格")
}
#增添大括号的原因是将这些代码看成一行一起运行

i <- 10
while(i > 0){
    print(i)
    i<-i - 2
}

for(i in 1:10) print("Hi")
#输出十次Hi
# for(i in x)  对x中的所有元素全部进行一次操作
a <- c(10, 20, 30, 40)
for(i in a) print(i * 10)

```

### 访问数据集

```R
a <- c(10, 20, 30, 40)
a[1]
#得到a中的第一个元素10
a[2]
#得到a中的第二个元素20
#和c++中的数组或者python中的list差不多， 但是下标是从一开始
a[c(1, 4)]
# 得到a中的第一个元素10和第四个元素40
```



### 扩展包的管理

#### 扩展包的作用

能实现某方面需求的功能集合

#### 安装包

```R
install.packages("包的名称")
#需要使用双引号
```

#### 加载包

```R
library(包的名称)
#不需要使用双引号
```

#### 查看当前已经安装的包

```R
installed.packages()
```

## R语言的数据结构

### 向量vector

* **向量**：用于储存数值型、字符型或逻辑型的一堆数组

  数据类型：

  1. 数值型数据：1， 2， 3
  2. 字符型数据：a， b， c
  3. 逻辑型数据：TRUE， FALSE

```R
#向量生成
a<-c(1, 2, 3, 4, 5)
b<-c("red", "blue", "black")
c<-c(TRUE, FALSE, FALSE)

```

* 访问向量中的元素
  1. 访问a中的第一个元素a[1],得到结果1
  2. 访问a中的第一个元素和第四个元素a[c(1, 4)]得到结果1， 4

单个向量中的数据类型必须是相同的数据类型

### 矩阵matrix

* **矩阵** ：二维的数据集， 且每个元素都是相同的数据类型

* 矩阵生成

  ```R
  matrix(vector, nrow, ncol, byrow, dimnames)
  m1 <- matrix(1:20, nrow = 5, ncol = 4)
  #按照列排序
  #1 6 11 16
  #2 7 12 17
  #3 8 13 18
  #4 9 14 19 
  #5 10 15 20
  m1 <- matrix(1:20, nrow = 5, ncol = 4， byrow = TRUE)
  #按照行排序
  #dimnames给矩阵的行和列命名
  n1 <- c("a", "b", "c", "d")
  n2 <- c(1, 2, 3, 4 ,5)
  m1 <- matrix(1:20, nrow = 5, ncol = 4， byrow = TRUE, dimnames = list(n2, n1))
  ```

* 访问矩阵中的元素

  ```R
  m1[2, 4]
  #访问matrix中的第二行第四列的元素
  m1[2, c(2, 3)]
  #访问matrix中的第二行， 第二列第三列的元素
  m1[3,]
  #访问matrix中第三行的元素
  m1[,4]
  #访问matrix中第四列的元素
  ```

### 数组array

* **数组**：数组与矩阵类似，但是维度可以大于2

* 数组生成

  ```R
  array(vector, dimensions, dimnames)
  array1 <- array(1:24, c(2, 3, 4))
  #两行三列四个矩阵
  array2 <- array(1:48, c(2, 3, 4， 2))
  #一个四行三列的矩阵matrix， 其中每个矩阵里面的元素又是一个两行三列的矩阵
  n1 <- c("x1", "x2")
  n2 <- c("y1", "y2", "y3")
  n3 <- c("z1", "z2", "z3", "z4")
  array1 <- array(1:24, c(2, 3, 4), dimnames = list(n1, n2, n3))
  ```

* 访问数组中的元素
  
  1. array1[2, 3, 1]

### 数据框dataframe

* **数据框**：由不同的列（可以是不同的数据类型）组成

* 数据框组成

  ```R
  data.frame(col1, col2, col3, ...)
  #年龄
  age <- c(21, 22, 23, 24)
  #性别
  gender <- c("female",  "male", "female", "female")
  #成绩
  grade <- c(91, 92, 93, 94)
  df1 <- data.frame(age, gender, grade)
  df1
  ```

* 访问数据框中的元素

  1. 通过下标
  2. 通过列名
  3. 通过美元符号

  ```R
  df1[1, ]
  #访问第一行
  df2[ , 2]
  #访问第二列
  df1[, 1:3]
  #访问第一列， 第二列， 第三列
  df1[-1, ]
  #访问除了第一行意外的其他行
  
  df1["age"]
  df1[c("age", "grade")]
  
  
  df$age
  #记得按Tab键
  
  ```

  

### 列表list

* **列表**：就是一些对象的有序集合， 这些对象可能是向量、矩阵、数组、数据框、其他列表的组合

* 列表的生成

  ```R
  list1 <- list(obj1, obj2, obj3, ...)
  ```

* 访问列表中的元素

  ```R
  list1[[2]]
  #通过双重括号来访问列表中第二个对象-obj2
  #查看obj2的数据类型， 然后根据obj2的数据类型， 进行不同的访问
  list[[2]][2, 2]
  list$obj2
  #如果第二个对象有命名，则可以通过美元符号来访问第二个对象
  v1 <- c(1, 2, 3, 4)
  m1 <- matrix(1:20, nrow = 4, ncol = 5)
  age <- c(11, 12, 13)
  country <- c("China", "Japan", "American")
  df1 <- data.frame(age, country)
  list1 <- list(x = v1, y = m1, z = df1)
  list1&x
  list1$y
  list1$z
  ```

  

## 导入与导出数据

getwd()得到当前的工作目录

### 导入数据流程

1. 通过setwd()重置工作目录
2. 将Excel文件另存为csv格式文件， 并存入到新的工作目录中
3. 输入read.csv("csv文件名称及其后缀")

### 导出数据流程

1. 通过setwd()重置工作目录
2. 输入write.csv(要导出的数据集,“csv文件名称及其后缀”)
3. 输入write.csv(要导出的数据集,“csv文件名称及其后缀” ,row.names = FALSE), 不输出索引行

## ggplot2绘图

### 介绍ggplot2

#### 功能

1. ggplot2是一个作图包

2. 可以创建诸如散点图、线图、柱状图等图表， 将数据可视化呈现

   ```R
   #ggplot2是一个扩展包
   install.packages("ggplot2")
   library(ggplot2)
   ```

   

#### 要素

* ggplot2要素主要包括：
  
1. 背景，坐标轴， 图形， 标题， 图例， 分面， 文本注释
  
* 一个具有诚意的ggplot2的作图应该是这样子的：

  ```R
  ggplot(data, aes(x, y))+geom_xx()+annotate()+labs()+facet_grid()+...
  # annotate 文本注释的一个函数
  # labs 标题， 可以添加坐标的标题
  # facet_grid() 是一个封面函数
  
  ```

#### 理念

* ggplot2的核心理念是：将绘图与数据相分离

* 有命令式作图的调整函数， 可以随时更换参数来调整图形， 更具灵活性

  

  ```R
  ggplot(data, aes(x, y))+   #初始化图形并指定数据源和作图变量， aes美学英文的首字母缩 写
  geom_XX()+                 #制定图形的类型 geom是几何学英文的首字母缩写
  annotate()+                #添加文本注释
  labs()+                    #修改主标题和坐标轴标题
  ...
  ```

  

#### 逻辑

* ggplot2是按照图层叠加作图的， 通过+号叠加， 越到后面图层越高
* ggplot2作图符合人的认知， 有明确的起点和终点， 由ggplot开始做图可以在后面的任一叠加函数停止作图

### 作图类型

#### 散点图

* 作用：描绘两组变量的关系情况
* 代码：ggplot(data, aes(x, y)) + geom_point()

#### 线图

- 作用：描绘两组变量的关系情况
- 代码：ggplot(data, aes(x, y)) + geom_line()

#### 柱状图

* 作用：查看变量的频数分布情况

* ggplot(data, aes(x)) + geom_bar()

* ```
  class()
  #可以查看变量类型
  numeric 数字类型
  需要转换成分子， 
  factor()
  分类变量
  ```

  

#### 直方图

* 查看变量的分布情况
* 代码：ggplot(data, aes(x)) + geom_histogram()

#### 密度图

* 作用：查看变量的频率分布情况
* 代码： ggplot(data, aes(x)) + geom_density()

#### 箱线图

* 作用：查看变量的统计值分布情况
* 代码： ggplot(data, aes(x， y)) + geom_boxplot()

### 分组作图

#### 分组变量的数据类型

```R
ggplot(mtcars,aes(wt, mpg, color = qsec)) + geom_point()
#渐变的颜色来做图
#wt作为x轴
#mpg作为y轴
#qsec作为染色的标志， 连续性的变量， 可以使用连续性的表尺
ggplot(mtcars, aes(wt, mpg, color = factor(vs))) + geom_point()
```

#### color与fill的区别

color是对点、线、 或者是图形的边界进行填色

fill是对图形的内部进行填充

#### 参数在aes内和外的区别

在aes内的时候， 会查找数据集中是否有这个变量，然后根据这个来渐变颜色， 如果使用factor颜色区分会很明显

想用颜色来分组

```R
ggplot(mtcars,aes(wt, mpg, color = qsec)) + geom_point()
```

在aes外部的时候会把所有的点、线染成你想要的颜色

统一图层的颜色

```R
ggplot(mtcars,aes(wt, mpg) + geom_point(color = "blue"))
```

