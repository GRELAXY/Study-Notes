# Python学习

​                                                                                                                    ---by Wheat

一些碎碎念：

主要参考了《Python编程：从入门到实践》和[b站的Python入门教程](https://www.bilibili.com/video/BV1wD4y1o7AS/?spm_id_from=333.1387.favlist.content.click)。举例代码基本都拿到VScode里面跑过。

然后来叠一个甲：

本笔记完全基于我个人的理解和认知，不对其中内容的正确性做绝对保证。请读者在参考本笔记时，自行进行实践和验证，以确认内容的准确性和适用性。

同时，本笔记中的内容可能存在一定的局限性和不足之处，希望读者能够理解和包容。如果您发现本笔记中存在任何错误或问题，可以dd:point_right:transmitmail@163.com

最后，本笔记仅供学习交流使用，请勿用于商业用途或其他非法目的。如涉及侵权等问题，请及时与我联系，我将积极配合处理

ps：蛇年就是要学Python嘛（提前拜个年

![image-20250116224835590](Python学习.assets/image-20250116224835590.png)

[P也是蛇](https://www.bilibili.com/video/BV12PqhYwEe3/?spm_id_from=333.337.search-card.all.click&vd_source=1f1cd53303a8ead1f003e16147d0ca52)

ps：ps：p让我c显得像:clown_face:





---



[TOC]

---



## 零
### 注释

- 单行注释：#

  `#这个是单行注释，换行了就不算`

- 多行注释：''' 开头结尾各三个' ("""也可以)

````py
'''
函数名：
输入：
输出：
'''
````

- **中文编码声明注释**：，如果涉及到中文内容，建议添加中文编码声明注释。一定要写在第一行

`#coding=utf-8`



***

### 占位符

- 空语句：pass
- 操作未确定时，线使用pass语句作为占位符，以保持程序结构的完整性，方便后续补充具体实现细节（不会报错）



---



### 缩进

- 和c的{}起类似功能用来划分语句块，表示包含和层次关系。常用于类定义，函数定义、流程控制语句和异常处理语句
- 语句块的开始由冒号(:)和下一行缩进组成 ；缩进的结束代表了语句块的结束

~~完了习惯了{}，一下子没有看不懂代码了呜呜~~

````py
#类定义
class Student:
    pass

#函数定义
def fun():
    pass

````



---



###  保留字



| False  | None     | True    | __peg_parser__ | and   |
| ------ | -------- | ------- | -------------- | ----- |
| as     | assert   | async   | await          | break |
| class  | continue | def     | del            | elif  |
| else   | except   | finally | for            | from  |
| global | if       | import  | in             | is    |
| lambda | nonlocal | not     | or             | raise |
| pass   | return   | try     | while          | yield |

- 如果不记得了可以现场打印看一下捏

````py
import keyword
print(keyword.kwlist)
````



---



### 识别符的命名

- 可以是英文 中文 下划线 和数字，但第一个不能为数字

- 不推荐中文

- 类命名是单词首字母大写（Pascal风格）如`MyClass`，模块内部的类开头还有个下划线 如`_InnerMyClass`，用双下划线__的变量和方法是类私有的

- 模块、函数、类的属性和方法命名是全小写,可以用下划线连接

- 包命名全小写，不推荐下划线可以用.

- 常量命名全部大写字母

- 双下划线开头和结尾的是Python专用标识

- 

  ~~以后就会了我懒了~~



## 壹

---



### print:school:

#### 函数原型:writing_hand:

`print(value,...,sep='',end='\n',file=None)`



- sep=” “，意思为print中若有逗号，实际输出效果是一个空格(字符串中的不算)

````py
print("Hello，world！","Hi,Python!")
#实际输出为 Hello,world！ Hi,python!
````



- （文件操作）往文件中写内容 
- file="写入的文件地址" 若无默认直接到屏幕

````py
fp=open("note.txt","w")
print("我哩个直接print就可以了"，file=fp)
print("python NB! ")
fp.close()#记得关闭文件
````



- 注意到end=\n 了吗，对它内嵌的换行 ，如果想修改末尾不是换行符可以

  `print("hello"，end="!")`输出结果就是hello！了



如此如此所以我可以这样玩

````py
print("great","value","这就是",sep="yaha",end=":clown_face:")
#输出：greatyahavalueyaha这就是:clown_face:
````





#### 常见操作:wolf:

- 字符串需要加引号‘ “ 都可以，数字英文表达式这类不需要加引号

````py
a=90
print(90)
print(a)
print("这个python真的好方便，但是没有；不要再手贱了")#习惯c的“了那就用”把
````



- 连接符+，只能够字符串和字符串连接

`print("Hello"+"world")`输出：helloword

- 可以使用chr（）通过ASCII来输出字符
- ord（）中填入‘文字’来输出对应的ASCII值（只能单个字符）

````py
print(chr(98))
print('b')
print('ord(虞)')
print('严')
print(chr(ord("玩")))
#输出：
#b
#b
#34398
#20005
#玩
````



---



### input:face_with_head_bandage:

#### 函数原型:writing_hand:

`input(*args, **kwargs)  # 实际签名未知   `

-   从标准输入读取一个字符串。会去掉尾部的换行符。   
-  如果提供了提示字符串，会在读取输入之前将其打印到标准输出，且不带尾部换行符。   
- 可选参数 prompt 用于指定用户输入时的提示信息，默认为空字符串 
-  prompt = kwargs.get('prompt', '')    如果 prompt 存在:打印 prompt ，结尾不换行 ,返回输入的内容   



#### 常见操作:wolf:

- 收到的只能是字符串变量，前可以用“提示词prompt”

````py
x=input("在这写在这里：")#对直接写个x就可以当变量了。。。
print(“我只是想说：”+x)
#输出
#在这写在这里：居然不用自己定义变量类型，可恶啊
#我只是想说：居然不用自己定义变量类型，可恶啊
````

- 如果不想要字符串类型的可以用函数转类型
  - float （默认一位，如果你输入是三位小时也会显示三位,最多14位）[^1]
  - bool(布尔类型)

````py
num=input("随便输入点数字：")
num=int(num)
cnt=int(input("cnt:"))
print(num,cnt)
print(num+cnt)#因为转换成整数了所以直接变成了表达式
#输出：
#随便输入点数字：1
#cnt:2
#1 2
#3//表达式的结果
````



## 貳

---



### 变量:yum:

- 无c的类型定义，直接`变量名=value`

#### 数值类型

###### 不可变数

- 不可变数据类型包括数值（如整数、浮点数）、字符串（`str`）和元组（`tuple`）。这些数据类型的值在创建后不能被修改，如果对其进行操作，实际上是创建了一个新的对象

###### 整数

- 十进制（默认）、二进制（0b或0B）、八进制（0o或0O）、十六进制(0x或0X)

###### 浮点数

- 直接复制带小数点，或者用科学计数法，如`x=1.99E2`输出199.0

  - 如果输出float类型的运算结果可能会输出14位小数，因为有些十进制小数在二进制中无法精确表示，如`0.1`和`0.2`在二进制表示中是无限循环的，所以当它们相加时，会出现一些微小的误差，导致结果有很多小数位。
  - 想要特定位数小数的可以使用`round(number(,digits))`,如`round(0.1+0.2,3)`则输出保留三位小数结果(但末尾是0所以不显示，输出为：0.3)
####3## 复数

 - 实部用.real  虚部用.imag表示

````py
#实数
num1=987#十进制
num2=0b010101#二进制
num3=0O3752#八进制
num4=0X5656ADF#十六进制
#但直接print输出还是按十进制

#复数
x=123+456j
print(x.real)
print(x.imag)
#输出：
#123.0
#456.0
````

###### 字符串

- 用‘ or “ or ”‘ 围起来 ，如果是多行的话必须用”’围起来

  - 一些转义字符：`\n`换行  、`\t`横跳到下一个制表单位（8） 、`\"`双引号 、`\'`单引号、`\\`反斜杠

- 常见操作：
  | `a+b`    | 连接ab字符串                      |
  | -------- | --------------------------------- |
  | `x*n`    | 或者`n*x`复制n次字符串x           |
  | `x in s` | 如果x是s子串则为TRUE，否则为FALSE |

  - 字符串的索引：正向：从左到右，从0开始；反向：从右到左，从-1开始

  - 字符串的切片：`str[start:end:step]`    

  - [start,end) ，step默认为1，负数就逆过来
  
    ````py
    s="Helloword"
    print(s[0],s[-9])
    print(s[2:5])#不包含5
    print(s[-5:-2])#反向递减
    print(s[:5])#没写默认从0开始
    print(s[5:])#默认一直到结尾
    #输出：
    #H H
    #llo
    #owo
    #Hello
    #word
    ````
  

###### 布尔类型

- `bool(x)`:x是任意一种数据类型,可将其转换为布尔值

- 真为True 或1，假为False 或0
- 如果bool中是整数，非负为真，0为假；字符串，元组，列表，字典，非空为真，空为假



## 叄


***



### 算术运算符

|  +   |  加  |  1+1=2   |
| :--: | :--: | :------: |
|  -   |  减  |   1-0    |
|  *   |  乘  |  2*3=6   |
|  /   |  除  | 10/2=5.0 |
|  //  | 整除 | 10//3=3  |
|  %   | 取余 |  10%3=1  |
|  **  |  幂  | 2**4=16  |

- 优先级：**   >   *、/、%、//    >   +、-



***

### 赋值运算

- 和c一样 ，= 、+=、-=、*=、/=、%=、**=、//=



***

### 比较运算符&逻辑运算符

- 和c一样，<、<=、>、>=、==、！=  ，但是可以连续比较 ，如`a<=x<=b`
- c中的`&&`、`||`和`!`分别换为可读性更高的 `and`、`or`和`not`



***

### 位运算符(二进制)

- 和c一样，z按位与`&`、按位或`|`、按位异或`^`、按位取反`~`、左移`<<`、右移`>>`

- 位移运算，左移：溢出部分被舍弃，低位端补0；右移：溢出被舍弃，如果符号位（最高位）为1，则补1，为0则补0



***

### *运算符的优先级

- 从上到下优先级递减

  |          **          |        幂        |
  | :------------------: | :--------------: |
  |       ~、+、-        | 取反、正号、负号 |
  |     *、/、%、//      |    算术运算符    |
  |         +、-         |       加减       |
  |        <<、>>        |  左移位、右移位  |
  |          &           |      按位与      |
  |          ^           |     按位异或     |
  |          \|          |      按位或      |
  | <、<=、>、>=、!=、== |       比较       |
  |          =           |       赋值       |

  



## 肆

***

### 顺序结构

- 按自然顺序，从上到下一次运行

### 选择结构
#### 单分支结构
````py
if 表达式：
	语句块
````
#### 双分支结构
````py
if 表达式：
	语句块
else：
	语句块
````
#### 多分支语句块
````py
if 表达式1：
	语句块1
elif 表达式2：
	语句块2
elif 表达式n：
	语句块n
else：
	语句块n+1
````

#### 嵌套
````py
#使用只要缩进就好
#例如（随便举的）
if 表达式1：
	if 表达式2：
    语句块1
    else：
    语句块2
else：
	if 表达式3：
    语句块3
	elif 表达式4：
    语句块4
    else：
    语句块5
````

#### 模式匹配
- match-case——switch差不多但不用自己写break

````py

match x：
	case a：
   		 语句块
    case b：
    	语句块
    case c：
    	语句块
    case _:#_是通配符号如果前面匹配都没成功就会执行它(~default)
     	语句块
    
````



### 循环结构

#### for循环

**1. for 循环变量 in 遍历对象：**
	**语句块**

**2. for 循环变量 in 遍历对象：**
	**语句块1**
**else:**
	**语句块2**

````py
#遍历字符串
for i in "hello":
    print(i,end="")
#输出：
#hello请按任意键继续. . .

#range()函数
for i in range(1,11):
    if i%2==0:
        print(i,"是偶数",sep="")
    else:
        print(i,"是奇数",sep="")
    
````



#### while循环

**1. while 表达式**

​	**语句块**

**2. while 表达式**

​	**语句块1**

**else：**

​	**语句块2**

````py
#玩一下罢了
print("-------Wechat------------")
print(":clown_face:")
name=input("Please Enter the user's name:")
password=eval(input("THe password:"))

cnt = 2
while cnt>0:
    if name != "PY":
        print("Can not find this user.only",cnt,"chances leave")
        name=input("Please enter the right name:")
        password=eval(input("THe password:"))
        cnt-=1
    elif  password != 666666:
        print("Wrong password.only",cnt,"chances leave")
        name=input("Please Enter the user's name:")
        password=eval(input("THe password:"))
        cnt-=1
    else :
        print("Verified seccessfully! Welcome to the wechat")
        break
else :
    print("""Oportunities are run out.
    We are sorry that this account will be freeze to protect its security.
    """)
````





### 转跳语句

#### break

- 和c一样，退出循环

#### continue

- 和c一样，跳过本次循环直接进入下次循环

## 伍.

### 序列

**`sname[start : end : step]`,一块可存放多个值的连续内存空间，这些值按一定顺序排列，可通过每个值所在位置的编号（称为索引）访问。主要包括字符串、列表、元组、集合、字典。字符串、列表、元组成为有序序列；集合和字典成为无序数列且不支持索引、切片、相加和相乘操作**

####  序列的索引
	正向：从左到右，从0开始；反向：从右到左，从-1开始

####  序列的切片
	`str[start:end:step]`    

- [start,end) ，step默认为1，负数就逆过来

​	*如果想复制整个列表可以：

````py
list1=["a","A","b"]
list2=list1[:]  #将整个list1复制到list2中

#如果没有切片操作，两个列表都指向同一个列表，会对其一起操作
my_books=["physis",'mathA']
friends_books=my_list

my_books.append(""mathB"")#此时friends和my的都会添加
````



#### 序列的相关操作：

|   x in s   |  若x为s的元素，则为真，否则为假  |
| :--------: | :------------------------------: |
| x not in s | 若x不为s的元素，则为真，否则为假 |
|   len(s)   | 序列s中的元素个数（即序列长度）  |
|   max(s)   |     序列s中元素的最大值[^2]      |
|   min(s)   |     序列s中元素的最小值[^3]      |
| s.index(x) |   序列s中第一次出现元素x的位置   |
| s.count(x) |       序列s中出现x的总次数       |

````py
str = "helloworld"
print("e" in str )
print("e" not in str)
print(len(str))
print(max(str))
print(min(str))
print(str.index('l'))
print(str.count("l"))
#输出：
#True
#False
#10
#w
#d
#2
#3
````



### 列表:clown_face:[^4]

**一种可变列表，用`[]`定义，元素之间用`,`间隔，元素可以为任意数据类型**

#### 创建

- （1）`list_name=[element1,element2,.......]`
- （2）list（）函数：`list_name=list(序列)`
- （3）l列表生成表达式：`[表达式 for 变量 in 可迭代对象 if 条件]`

````py
print(list("hello"))
print(list(range(1,10,4)))
even_numbers = [i for i in range(1, 11) if i % 2 == 0]
print(even_numbers)  
#玩一下生成随机数
import random
lst=[random.randint(1,100) for _ in range(10)]
print(lst)
#输出：(打印列表包括了方括号)
#['h', 'e', 'l', 'l', 'o']
#[1, 5, 9]
#[2, 4, 6, 8, 10]
#[85, 73, 22, 48, 57, 35, 51, 80, 61, 25]
````

- 相加：- `list=list1+list2+...`可以创建出新的list，元素包含list1，list2.....中的元素

- 相乘：- `list=list1*n`,list的元素中，list1的元素重复出现n次

````py 
list1=list("hello")
list2=list(range(1,10,4))
list3=["python","simplistic",6]
print(list3*3)
print(list1+list2)
print(len(list1+list2+list3))
#输出：
#['python', 'simplistic', 6, 'python', 'simplistic', 6, 'python', 'simplistic', 6]
#['h', 'e', 'l', 'l', 'o', 1, 5, 9]
#11
````







#### 访问和遍历

````py
my_list=["hello",3,5,6]
#第一种方式
for item in my_list:
    print(item,end="")
print()
#第二种方式
for i in range(0,len(my_list)):
    print(i,my_list[i])
#第三种方式
for index,item in enumerate(my_list,start=1):
    print(index,item)
#输出：
#hello356
#0 hello
#1 3
#2 5
#3 6
#1 hello
#2 3
#3 5
#4 6
````





#### 增删改操作

|    lst.append(x)     |                   在列表lst尾部加一个元素                    |
| :------------------: | :----------------------------------------------------------: |
| lst.insert(index,x)  |               在列表lst第index个位置加一个元素               |
|    lst.clear（）     |                      清除lst中所有元素                       |
|    lst.pop(index)    | 将lst中第index个元素取出（==使用==）,并从列表中删除，若不写index默认弹出最后一个元素（和栈相似） |
|    del list_name     |                         删除整个列表                         |
| del list_name[index] |              删除列表中第index个元素（从0开始）              |
|    lst.remove(x)     | 将lst中出现的**第一个**x元素删去（==不知道元素的序列但直到元素的值==）[^5] |
|    lst.reverse(x)    |                      将lst中的元素反转                       |
|     lst.copy(x)      |              拷贝lst中所有元素，并生成个新列表               |



#### 排序

`my_list.sort(key=None,reverse=False)`

- `key`：指定排序时进行比较的元素，可以指定一个函数或者 lambda 函数,此函数将在每个元素比较前被调用。默认按字母顺序
- `reverse`：排序规则，`reverse=True`为降序，`reverse=False`为升序（默认）。该方法会直接在原列表上进行排序，不会产生新的列表。

`sort(iterable,key=None,reversed=False)`

- `iterable`：可迭代对象，如列表、元组等
- `key`和`reverse`的含义与`lst.sort()`中的相同。该函数会返回一个新的已排序的列表，原列表不会发生变化

````py
lst = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
lst.sort()
print("lst.sort() 后：", lst) 
lst.sort(reverse=True)
print("lst.sort(reverse=True) 后：", lst) 
# 输出：[1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]
# 输出：[9, 6, 5, 5, 5, 4, 3, 3, 2, 1, 1]

new_lst = sorted(lst)
print("sorted(lst) 后：", new_lst) 
new_lst = sorted(lst, reverse=True)
# 输出：[1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]
print("sorted(lst, reverse=True) 后：", new_lst)  # 输出：[9, 6, 5, 5, 5, 4, 3, 3, 2, 1, 1]
````



#### 二维列表

````py
#创建
lst=[['广州',555],['hhh',666],['jdbfjgghfjgfh',5564]]

#列表生成式创建
two_dim_list=[[column for row in range(5)]for row in range(4)]#4行5列

#遍历
for row in lst:#行
  for column in row:#列
    print(column,end='\t')
#输出：
#广州    555     hhh     666     jdbfjgghfjgfh   5564    
````



***

### 元组:green_apple:

**不可变序列，其元素的值就不能被修改，用`()`定义，元素之间用`,`间隔，只有一个元素时逗号也不可以省略**

#### 创建

- （1）直接：`tuple_name=(element1,element2,....)`
- （2）tuple函数`tuple_name=tuple(序列)`
- （3）元组生成式：（和list不同，生成的是tuple对象而不是tuple，若想要将其转换成元组可以用tuple函数）

````python
#第一种
tuple_name1=("hello","world",[6,5,8,"Hi"],5.6)
#第二种
tuple_name2=tuple("hello python")
#第三种
tuple_elements=(item for item in range(0,11) if item%2==0)
tuple_name3=tuple(tuple_elements)

print(tuple_name1)
print(tuple_name2)
print(tuple_name3)
#输出：
#('hello', 'world', [6, 5, 8, 'Hi'], 5.6)
#('h', 'e', 'l', 'l', 'o', ' ', 'p', 'y', 't', 'h', 'o', 'n')
#(0,2,4,6,8,10)
````



#### 删除元组

- `del tuple_name`



#### 访问和遍历

和列表一样

````py
my_tuple=("hello",3,5,6)
#第一种方式
for item in my_tuple:
    print(item,end="")
print()
#第二种方式
for i in range(0,len(my_tuple)):
    print(i,my_list[i])
#第三种方式
for index,item in enumerate(my_tuple,start=1):
    print(index,item)
````

#### 修改元组变量

- 虽然不可以秀爱元组的元素但可以给贮存元的变量重新赋值

````py
tuple_name=(1,5,9)
ruple_name=(2.5)#重新赋值，直接覆盖
````



### 字典 :dizzy:

- 根据一个信息查找另一个信息，构成“键—值”对（key—value），key充当索引作用。如果定义中key相同，最后一个元素会覆盖
- 无序，即第一个添加到字典的元素在内存中不一定放在第一位（hash）[^6]



#### 创建

- （1）直接：`dict_name={key1:value1,key2:value2,...}`

- （2）dict函数：dict_name=dict(key1=value1,key2=value2....)
- （3）zip映射函数+dict：

````py
list1=[10,20,30]
list2=["dogs","cats","birds"]
#print(list(zip(list1,list2)))
d=dict(zip(list1,list2))#可以把列表中得元组转化为键值对
print(d)
#输出：
#[(10, 'dogs'), (20, 'cats'), (30, 'birds')]
#{10: 'dogs', 20: 'cats', 30: 'birds'}
````

- 可以通过元组当作键，但列表不可以(即可变序列不可以做key)

````py
t=(10,20,30)
print({t:10})
#输出：
#{(10,20,30):10}
````

- （4）生成式：
	`d={key:value for item in range}`

	`d={key:value for key,value in zip(list1,list2)}`

````python
import random
d={key : random.randint(1,100) for key in range(3)}
print(d)
list1=[1001,1002,1033]
list2=["a","v","h"]
d={key:value for key,value in zip(list1,list2)}
print(d)
#输出：
#{0: 65, 1: 10, 2: 42}
#{1001: 'a', 1002: 'v', 1033: 'h'}
````



#### 删除

`del dict_name`



#### 访问和遍历

- 访问元素：`d[key]或着d.get(key)`

  d.get(key)中key不存在会返回None。还可以指定None的默认值如`print(d.get("java","不存在"))`会返回”不存在“

- 遍历元素：

  `items()`方法主要是用于字典（`dict`）对象的。字典（dict）的 items() 方法是一种非常有用的功能。它不接受任何参数，返回一个字典视图对象，该对象包含字典的键值对

  （1）遍历出元组（key，value)`for element in d.items()`

  （2）分别遍历出key和value`for key,value in d.items()`

  ````py
  d={10:20,90:80,70:80}
  for item in d.items():
  	print(item)
  for key,value in d.items():
      print(key,"->",value)
  #输出：
  #(10, 20)
  #(90, 80)
  #(70, 80)
  #10 -> 20
  #90 -> 80
  #70 -> 80
  ````

  

#### 字典的操作

|      d.keys()      |                      获取所有key的数据                       |
| :----------------: | :----------------------------------------------------------: |
|     d.values()     |                     获取所有value的数据                      |
| d.pop(key,default) | 获取key对应的value同时删除key-value对；若不存在则返回default，如没设置default则返回None |
|    d.popitem()     |     随机从字典中一个 取出一堆，返回类型为元组，同时删去      |
|      d.clear       |                  清空字典中所有key—value对                   |

````python
d={1002:5,1003:6,1004:8}

#向字典中添加
d[1005]=9

keys=d.keys()
print(keys)
print(list(keys))
print(tuple(keys))
print(d.values())
print(dict(list(d.items())))#元组->列表中得元组->字典
print(d.pop(1008,"好耶"))
print(d.popitems())
#输出：
#dict_keys([1002, 1003, 1004, 1005])
3[1002, 1003, 1004, 1005]
#(1002, 1003, 1004, 1005)
#dict_values([5, 6, 8, 9])
#{1002: 5, 1003: 6, 1004: 8, 1005: 9}
#好耶
#(1005, 9)
````



### 集合:fishing_pole_and_fish:

- **无序不重复** 的元素序列，只能存储不可变数据类型（即不可以存储列表和字典），但是是可变数据类型



#### 创建

- （1）直接：`s={element1,element2,element3,....}`
- （2）set()函数：`s=set(可迭代公式)`

- （3）生成式：`s=(i for i in range() if...`（和其他的一样）

#### 删除

- `del set_name`



#### 操作符

- 交集：A&B          并集：A|B       差集：A-B（A中扣去(A&B)）	补集：A^B     



#### 集合的操作方法

|  s.add   | 如果x不在集合中，则将x加入s中（不会重复添加） |
| :------: | :-------------------------------------------: |
| s.remove |  如果x在集合中，则将其删除；若不在，则会报错  |
| s,clear  |              清楚集合中所有元素               |



#### 遍历

````python
for item in s :
    print(item)
    
for index,item in enumerate(s):
    print(index,"->",item)
    
````



## 陸

***

## 字符串:monkey:

- 不可变数据类型

### 常用操作

| str.split(sep=None) | 把str按照指定分隔符sep进行分割，结果为列表类型              |
| :-----------------: | ----------------------------------------------------------- |
|   str.count(sub)    | sub字符串在str中出现的次数                                  |
|    str.find(sub)    | 查询sub在str中是否存在。不存在为-1，存在为sub首次出现的索引 |
|     str.index()     | 与.find()同，区别是如果sub不存在index（）会报错             |
|  str.startswith(s)  | 查询str是否以s开头                                          |
|   str.endswith(s)   | 查询str是否以s结尾                                          |



````python
s1="hello world"
str_list=s1.split(sep=" ")
print(str_list[0]+str_list[1])
print(s1.count("o"))
print(s1.find("p"))
print(s1.index("o"))
print(s1.startswith("s"))
print(s1.endswith("ld"))
#输出：
#hello world
#2
#-1
#4
#False
#True
````



### 输出样式

| str.replace(old,news(,count)) | 使用news替换字符串str中所有old字符串，结果是新的字符串。如果不指定`count`或`count`为`-1`，则会替换所有匹配的子串；如果指定了`count`，则只会替换前`count`个匹配的子串。 |
| :---------------------------: | ------------------------------------------------------------ |
|  str.center(width,fillchar)   | 字符串str在指定的宽度范围内居中，可以使用fillchar进行填充    |
|          str.lower()          | 将str字符转换为小写字母，结果是新字符串                      |
|          str.upper()          | 将str字符转换为大写字母，结果是新字符串                      |
|          str.title()          | 将str字符每个单词的首字母改成大写                            |
|        str.join(item)         | 在item中的每个元素的后面都增加一个新的字符串str。用于将序列（如列表、元组或字符串集合）中的元素以指定的字符连接生成一个新的字符串。该方法只能用于字符串对象，这意味着需要先确保序列中的元素也都是字符串类型（或者可以被转换为字符串的类型，比如数字） |
|       str.strip(chars)        | 从str中去掉左侧和右侧chars中列出的字符串                     |
|       str.lstrip(chars)       | 从str中去掉左侧chars中列出的字符串                           |
|       str.rstip(chars)        | 从str中去掉右侧chars中列出的字符串                           |

````python
s=" hello world "
new_s=s.replace('o',"!",1)
print(new_s)
print(s.center(7,"*"))
print(s.center(15,"*"))
print(s.lower())
print(s.upper())
print(s.strip('ld'))
print(s.strip('dl '))#与dl，ld的顺序无关只要包含ld就会删除
print(s.lstrip('rd '))
print(s.rstrip(' '))
print(', '.join(('Fusion', 'Sphere', 'Cloud')))#用逗号连接列表中的字符串
print(" ".join(('China', 'Japan', 'USA', 'UK')))#用空格连接字符串列表
numbers = (123, 456, 789)
print('-'.join(map(str, numbers)))#将数字列表转换为字符串列表，然后连接

#输出：
# hell! world
# hello world
#* hello world *
# hello world
# HELLO WORLD
# hello world
#hello wor
#hello world
# hello world
#Fusion, Sphere, Cloud
#China Japan USA UK
#123-456-789
````



### 格式化字符串:confused:

1. 占位符：和c一样
2. f-string：用{}来表明被替换的内容
3. str.format（）：模板字符串.format



````python
name="鱼"
age=18
score=98.56
#占位符
print('name:%s,age:%d,score:%.2f' %(name,age,score))
#f-string
print(f'name:{name},age:{age},score:{score}') #格式刷
#str.format
print("name:{0},age:{1},score:{2}".format(name,age,score))#0,1,2对应format中的索引位置

#输出：
#name:鱼,age:18,score:98.56
#name:鱼,age:18,score:98.56
#name:鱼,age:18,score:98.56
````



#### **str.format的格式**

在index后可以跟:arrow_heading_down:

| :        | 填充             | 对齐方式                                 | 宽度     | ，           | .精度                        | 类型                                  |
| -------- | ---------------- | ---------------------------------------- | -------- | ------------ | ---------------------------- | ------------------------------------- |
| 引导符号 | 用于田中单个字符 | <左对齐          >右对齐       ^居中对齐 | 输出宽度 | 千分位分隔符 | 小数点后的精度or最大输出长度 | 整数：b\d\o\x\X       浮点数：e\E\f\% |

 

````python
s1='helloword'
print('{0:*^20}'.format(s1))
print("{0:,.5f}".format(655449.1665))
#输出：
#*****helloword******
#655,449.16650
````



 ### 数据的验证

| str.isdigit()   | 所有字符都是数字                      |
| --------------- | ------------------------------------- |
| str.isnumeric() | 所有字符都是数字                      |
| str.isdecimal() | 所有字符都是数字[^7]                  |
| str.isalpha()   | 所有字符都是字母（包括中文字符）      |
| str.isalum()    | 所有字符都是数字或字母(包括中文字符） |
| str.islower()   | 所有字符都是小写                      |
| str.isupper()   | 所有字符都是大写                      |
| str.istitle()   | 所有字符都是首字符大写                |
| str.isspace()   | 所有字符都是空白字符（\t,\n等）       |



### 字符串拼接

1. str.join()
2. 直接拼接
3. 用格式化字符串进行拼接





### 字符串的去重操作

````python
#(1)字符串拼接以及not in
s='helloworldhellowordhelloword'
new_s=' '
for item in s:
    if item not in new_s:
        new_s+=item #拼接操作
print(new_s)

#输出：
# helowrd
    
#（2）索引+not in
new_s2=' '
for i in range (len(s)):
    if s[i] not in new_s2:
        new_s2+=s[i]
print(new_s2)

#(3)集合+列表排序
new_s3=set(s) #用集合的唯一性去重
myList=list(new_s3)
list.sort(key=s.index)#按照s中媳妇首次出现的索引值进行排序。不能index()，这样就调用了index函数了，与逻辑不符
print(''. )

#输出：
# helowrd
# helowrd
#helowrd
````



[还有一些查重操作](https://www.bilibili.com/list/ml3225845583?spm_id_from=333.1387.0.0&oid=712020469&bvid=BV1wD4y1o7AS&p=89)







## 柒

***

## 函数

### 自定义函数的结构

````python
def 函数名 (参数列表):
    函数体
    [return返回值列表]
````



### 传参

- 位置参数：按照函数的定义中的位置传入

- 关键字传参：可不按照顺序用`形参名字=值`传递

- 默认值传参：如果函数的定义中对形参赋了值，在调用时没有传参则直接使用默认值
  **位置参数在前，关键字参数在后，默认值参数放在最后**

- 可变参数：个数可变的位置参数和个数可变的关键字参数
  - 个数可变的位置参数：`*para_name`调用时可以接受任意个数的实际参数，并放到一个**元组**中  (print可以处理元组)
  - 个数可变的关键字参数：`**para_name`调用时可以接受任意多个`参数=值`形式的参数并放到一个**字典**中

````python
def add_sum(*para_name):
    sum=0
    for i in range(0,len(para_name)+1):
        sum+=i
    print(sum)

def printdict(**para_name):
    print(type(para_name))
    for key,value in para_name.items():
        print(key,"->",value)

add_sum(50,65,82)#传入3个值，len（para_name）为3
printdict (value1='key1',key2='value2')

d={"afsf":"afsg","af":"hh","wr":"sg"}
print(printdict(**d))#解包[^8]
#输出：
#6
#<class 'dict'>
#value1 -> key1
#key2 -> value2
#<class 'dict'>
#afsf -> afsg
#af -> hh
#wr -> sg
#None（函数没有return，子goon给输出个None）
````

解包[^8]



ps：如果形参很多可以:arrow_heading_down:

````python
def function_name(
		para_0,para_1,para_2,
		para_3,para_4,...)
````





### 返回值

- 返回值可以是一个或**多个**。多个值的话返回结果是一个元组类型

````python
def caculate(num1,num2):
    sum=num1+num2
    return sum

print(caculate(caculate(1,2),3))    #1+2+3,先算内层的caculate

def sum(num):
    odd_sum=0 #奇数
    even_sum=0 #偶数
    for i in range(1,num+1):
        if i%2==0 :
            even_sum+=1
        else:
            odd_sum+=1
    return odd_sum,even_sum

result = sum(10)
print(type(result),result)

#解包赋值
a,b = sum(10)
print(a,b)

#输出结果：
#6
#<class 'tuple'> (5, 5)
#5 5
````



### 匿名函数 lambda

- 使用场景：体只有一句代码且只有一个返回值的时候可以用匿名函数简化。（因为lambda是没有名字的函数，所以只可以使用一次）
- result =lambda 参数列表：表达式

````python
Ex1:
s=lambda a,b:a+b
print(type(s))
print(s(10,20))
#输出：
#<class 'function'>
#30

Ex2:
lst=[10,20,30,40]
for i in range(len(lst)):
    result=lambda x:x[i]
    print(result(lst))
#输出：
#10
#20
#30
#40
````



### 函数模块的导入

- 函数的优点之一：可将代码块和主程序分离，甚至可以将函数存在成为**模块**的独立文件中，在用`imnport`导入模块

1. 导入整个模块

````python
#pizza.py
def make_pizza(size , *toppings):
    print(f"Making a {size}-inch pizza with the following toppings: ")
    for topping in toppings:
        print(f"- {topping}")
````

````python
#making_pizza.py
import pizza  #导入

#调用
pizza.make_pizza(13,'pepperomi')
pizza.make_pizza(18,'mushroom','double cheese')
````




2. 导入特定函数：`from module_name import function_name0,function_name1,function_name2`

调用的时候不需要加`模块名.`只需要直接引用函数名字`function_name1()`



- 若想导入所有的函数则用*代替  `for module import *`就可以用module中的所有函数了



3. 用as指定别名（原函数名过长或与本文件函数名有冲突的情况下）

（1）给函数指定别名 :`from module_name import function_name as function_name1`

（2）给模块指定别名：`import module_name as module_name1`









## 捌

***

## 类

- 根据类来创建对象，将其实例化。可以指定实例中存储什么信息，定义对这些实例可以执行哪些操作。用于模拟现实中的某物。
- Python中首字母大写的名称指的是类



 ### 自定义数据类型的结构

````python
class 类别名:   #类名首字母大写
    pass
````




### 类中的函数

1. 类中的函数称为方法。与前面提到的函数使用的差别只用调用方式

2. 特殊的方法：`def __init__(self,para_1,para_2,...)`          	init要有两个下划线`_`

 - `_init__`：每当程序员根据类创建新实例的时候，Python会自动运行它

 - 形参中self 必不可少且必须位于所有形参前面。当Python调用这个方法创建实例的时候，会自动传入实参self。程序员只需要传递para_x.

  以self为前缀的变量可供类中所有方法使用，这些可以通过实例访问的变量成为属性。如：

  ````python
  def __init__ (self,name,age): #初始化属性name，age
      self.name=name
      self.age=age
  ````

- 给属性指定默认值：

    ````python
    class Car:
        
        #初始化属性
        def __init__(self,model,year):
            self.model=model
            self.year=year
            self.odometer_reading = 0 #汽车里程的初始值默认为0
    ````

    



### 创建对象的语法格式为：

````python
对象名 = 类名()
````




````python
Ex
class Person:
    #初始化属性name和age
	def __init__(self,name,age):
		self.name=name
		self.age=age
		
    #模拟人sleep
	def sleep(self):
		print(f"{self.name} is sleeping")
    	
  #模拟人eat
	def eat(self):
		print(f"{self.name} is eating")
        
 
#创建实例
person_1 = Person("YQQ","1999878")#person1 为Person类型的对象
#访问属性
print(f"{person_1.name} is {person_1.age} years old.")
#调用方法
person_1.eat()
person_1.sleep()
#again
person_2 = Person("YPY","1999878")#person1 为Person类型的对象
print(f"{person_2.name} is {person_2.age} years old.")
person_2.eat()
person_2.sleep()

````





### 继承

- 编写的类是既有的类的特殊版本，可以使用继承来获取既有类的所有属性和方法。既有类成为父类，新类成为子类

- `class 子类（父类）`

````python
#父类
class Person:
    pass
#子类       
class Superhuman (Person):
	def __init__(self, name, age):
		"""
		先初始化父类的属性，再初始化子类特有属性
		"""
		super().__init__(name, age)   #super()函数用于调用父类的方法

		self.energy = 100

	def read_energy(self):
		print(f"There's still {self.energy}% leaves")

        
pq=Superhuman("PQ","99")
pq.read_energy()
pq.sleep()
    
"""输出：
There's still 100% leaves
PQ is sleeping
"""
````

#### 重写父类的方法

- 在子类中用同名方法覆盖

```python
class Superhuan(Person):
    ...
    def sleep(self):
        print(f"{self.name} doesn't need to zzz!!!")  
```



### 组合

- 将类的部分提取出类作为独立的类，使得大型类拆分为协同工作的小类
- 操作类似于在在初始化自身属性的时候将一个默认属性创建为一个小类的对象。这样Python就可以在创建的实例中查找对应属性，在到储存对应属性的实例中调用方法等

````python
#父类
class Person:
    pass

#子类的小类
class Equipment:
    def __init__(self,power=100):
        self.power=power
        
    def show_equip_1(self):
        print(f"The Excalibur :{self.power}%")
      
    def show_equip_2(self):
        print(f"The Holy Unicorn :{self.power}%")
#子类
class Superhuman(Person):
	def __init__(self, name, age):
		"""
		先初始化父类的属性，再初始化子类特有属性
		"""
		super().__init__(name, age)   #super()函数用于调用父类的方法

		self.energy = 100
        self.equipment=Equipment()#没有指定power的值，默认为100

	def read_energy(self):
		print(f"There's still {self.energy}% leaves")
      
pq=Superhuman("PQ","99")
pq.read_energy()
pq.equipment.show_equip_2()

#输出：
#There's still 100% leaves
#The Holy Unicorn :100%
````



### 类的导入

- 导入类：`from module import class_name_1,class_name_2,...`

- 导入整个模块：`import module_name`访问则需：`module_name.class.name`
- 导入模块中所有类：`from module import *`(不推荐)
- 使用别名（与函数相同）`from module import class_name as name`







## 玖

***

## 文件



### 读取文件

*VScode要先打开所需文件夹（Ctrl+O并打开文件夹）

1. 告知路径：需导入pathlib库中的Path类，Path对象指向一个文件

````python
from pathlib import Path

path=Path('绝对路径or相对路径')
````

ps：与c不同可使用`/` ，无需用`//`

2. 读取全部内容：使用`path.read_text()`方法读取全部内容，并将内容作为一个字符串返回

    ````python
    contents = path.read_text()
    print(contents)
    ````

    ps:用read_text()会比源文件多出一个空行，可以用.rstrip去掉（详字符串的输出演示）

    `contents = path.read_text().rstrip()`

3. 读取各行：在读取全部内容之后可以用`splitlines()`将字符串转换成一系列行，返回一个列表

````python
contents = path.read_text()
lines = contents.splitlines()
for line in lines:
    print(line)    #line默认左端有空格
````



 ### 写入文件

1. 告知路径

2. 写入一行：使用`path.write_text()`.如果文件不存在，则会新建一个。若存在，则会删除原内容再将心内容写入其中

    注：只能写入字符串，若是其他类型需要用`str()`转换

````python
from pathlib import Path
path = Path('...')
path.write_text("Hello world!")
````



3.写入多行：用字符串拼接，在写入文件中

````python
contents = "Unless……\n"
contents += "Oh! Could it be some kind of sign\n"
contents += "That my world is all about to change\n“
contents += "Is it finally time for the challenge I arranged\n"
contents += "Though I never thought that it would come to this\n"
contents += "Just know I'll be here buying you time\n"
path = Path("EPIC!!!OMG.txt")
path.write_text(contents)
````



### 异常

#### try-except

- 每当发生错误时，Python会创建一个异常对象。如果编写了处理异常的代码，程序会继续运行，否则会停止并显示一个traceback
- 可以用`try-except`代码块来编写.如果`try`代码快运行没问题，则跳过`except`，否则运行`except`代码块

例如：traceback：

`print(5/0)`   -->  

````py
Traceback (most recent call last):
 File "e:\Vscode\code for p\trytoplay.py", line 1, in <module>
  print(5/0)
ZeroDivisionError: division by zero
````

try-except:

````python
try:
    print(5/0)
except ZeroDivisionError:
	print("Can not divide by zero")
#输出：
#Can not divide by zero
````

- 常见的try-except模块还会添加else。以此来避免让用户看到traceback

````python
print("Give me two number ,and I'll divide them")
print("enter'q' to quit")
while True:
	num1=input("plz enter the first number:")
	if num1=='q':
		break
	else:
		num2=input("plz enter the secound number:")
		if num2 =='q':
			break
		else:
			try:
				res=int(num1)/int(num2)
			except ZeroDivisionError:
				print("Can not divide by zero")
			else:
				print("The result is {:.20}".format(res))

'''
输出：
Give me two number ,and I'll divide them
enter'q' to quit
plz enter the first number:5
plz enter the secound number:0
Can not divide by zero
plz enter the first number:6
plz enter the secound number:4
The result is 1.5
plz enter the first number:q'''
````

#### FileNotFoundError

- 为了避免文件打开失败建议使用try-except-else模块进行编写（类似于c中的fopen文件后对文件指针检查是否存在的操作）

````python
from pathlib import Path
path = Path('...')

try:
    contents=path.read_text(encoding='utf-8') #或其他编码格式
except:
    print("Can not open this file.")
else:
    pass
````



#### 静默失败

- except中的内容用pass占位，这样异常的时候就不会有任何输出







### 储存数据

- `JSON`格式文件储存数据，可以用不同编程语言打开。用于储存用户输入的数据，使下一次打开程序时还能调用。

1. 导入json模块
2. 获取.json格式的文件路径
3. 用`json.dumps(target)`将target转为JSON格式的数据，用write_text写入

或者read_text后用`json.loads(target)`将JSON格式的数据转换为python对象

````python
from pathlib import Path
import json

lst=[2,3,5,7]

path=Path('test.json')
contents=json.dumps(lst)
path.write_text(contents)
#打开文件：
#[2,3,5,7]

contents=path.read_text()
lst=json.loads(contents)
print(lst)
#输出：
#[2,3,5,7]
````





















































## 附录

### 常用的内置函数

#### 1.数据类型转换

| bool(objection) |   获取objection的布尔值   |
| :-------------: | :-----------------------: |
| str(objection)  | 将objection转成字符串类型 |
|     int(x)      |      将x转成int类型       |
|    float(x)     |     将x转成float类型      |
| list(sequence)  |    将序列转成列表类型     |
| tuple(sequence) |    将序列转成元组类型     |
|  set(sequence)  |    将序列转成集合类型     |

#### 2.常见数学函数

|    abs(x)     |          获取x的绝对值           |
| :-----------: | :------------------------------: |
|  divmod(x,y)  |        获取x与y的商和余数        |
| max(sequence) |       获取sequence的最大值       |
| min(sequence) |       获取sequence的最小值       |
|   sum(item)   |     对可迭代对象进行求和运算     |
|    pow)x,y    |           获取x的y次幂           |
|  round(x,y)   | 对x进行保留d位小数，结果四舍五入 |



#### 3.迭代器操作函数

|     sorted(item)      |                   对可迭代对象进行排序                    |
| :-------------------: | :-------------------------------------------------------: |
|  reversed(sequence)   |                反转序列生成新的迭代器对象                 |
|   zip(item1,item2)    | 将item1和item2打包成一个与那组，并返回一个可迭代的zip对象 |
|    enumerate(item)    |             根据item对象创建一个enumerate对象             |
|       all(item)       |    判断可迭代对象item中所有的元素的布尔值是否都为True     |
|       any(item)       |     判断可迭代对象item中所有元素的布尔值是否都为False     |
|      next(item)       |                  获取迭代器的下一个元素                   |
| filter(function,item) |         通过指定条件过滤序列并返回一个迭代器对象          |
|  map(function,item)   | 通过函数function对可迭代对象item的操作返回一个迭代器对象  |



#### 4. 文件操作函数

|   path.exists()   | 指定文件是否存在，存在返回True,否则返回False |
| :---------------: | -------------------------------------------- |
| path.read_text()  | 在指定文本中读取所有内容                     |
| path.write_text() | 将字符串写入文本中                           |
|   json.dumps()    | 将python对象转换为json格式                   |
|   json.loads()    | 将json格式转换为python对象                   |









#### 5. 其他

| format(value,format_spec) | 将value以format_spac格式进行显示 |
| :-----------------------: | :------------------------------: |
|          len(s)           |     获取s的长度或s元素的个数     |
|       id(objection)       |        获取对象的内存地址        |
|          type(x)          |         获取x的数据类型          |
|          eval(s)          |     执行s字符串所代表的代码      |






---



### 一些函数的解释

#### 1. `len()`：

- **用于返回对象的长度（元素个数）**

- 如果对象是字符串，`len()`函数返回字符串的字符个数；如果对象是列表、元组或字典等，`len()`函数返回其元素的个数



#### 2.`type()`:
- **用于返回对象的类型**

````py
ch = "Hello"
print(type(ch)) 
# 输出: <class 'str'>
````

#### 3.`eval()`:
- **将字符串当作有效的表达式来求值，并返回表达式的值**

- `eval(expression, globals=None, locals=None)` 
- 该函数会把字符串参数的引号去掉，把中间的内容当成 Python 的代码并执行，然后返回执行结果。

````py
a=input("请打下3.24+5.23：")#输入的时候重复一遍
print(eval(a))
#输出：
#请打下3.24+5.23：3.24+5.23
#8.47

h="北京欢迎你"
print(h)
print(eval("h"))#去掉两边的"使h从字符串变成了一个变量
#输出：
#北京欢迎你
#北京欢迎你
#另外：不可以print(eval(h))
````



#### 4. range（）：

`range(start, end(, step))`     范围是：[start,end)

- start：计数从 start 开始，默认是从 0 开始
- end：计数到 end 结束，==但不包含 end==
- step：步长，默认为 1
- 例如，range(5)等价于range(0, 5)。range()函数返回一个range对象，该对象表示一个数字序列，通常用于循环中。



#### 5.enumerate：

`enumerate(iterable, start=n)`

- 用于在遍历可迭代对象（如列表、元组、字符串等）的同时提供该元素的索引值。它返回一个迭代器，生成的是带有索引和值的元组，作用是为可迭代对象生成一个计数器，返回(index, value)形式的元组
- start=n;索引从n开始计数

````py
my_list=["hello",3,5,6]
#随常用的就是遍历
for index,item in enumerate(my_list,start=1):
    print(index,item)
    print(enumerate(my_list,start=0))
#输出：
#1 hello
#<enumerate object at 0x000001ED6A271600>
#2 3
#<enumerate object at 0x000001ED6A271640>
#3 5
#<enumerate object at 0x000001ED6A2715C0>
#4 6
#<enumerate object at 0x000001ED6A271600>
````



#### 6. id（）：

`id(value)`:变量地址



#### 7. random():

**这个得引入`import random`**

1. `random.random()`：返回一个 0 到 1 之间的随机浮点数。
2. `random.uniform(a, b)`：返回一个 a 到 b 之间的随机浮点数。
3. `random.randint(a, b)`：返回一个 a 到 b 之间（包括 a 和 b）的随机整数。



#### 8. zip（）

- 用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的对象。如果各个迭代器的元素个数不一致，则返回的对象长度与最短的对象相同。

如：zip ( list1 , list2 ) = [ ( list1[i] , list2[i] )  for i in range(min(len(list1),len(list2)))]



#### 9.map（function,iterable,...)

- `function`：是一个函数，用于处理`iterable`中的元素。
- `iterable`：是一个可迭代对象，如列表、元组、字符串等。
- `...`：可选参数，可传入多个可迭代对象。

````python
def square(x):
    return x ** 2
numbers = (1, 2, 3, 4, 5) 
squared_numbers = list(map(square, numbers)) 
print(squared_numbers)
# 输出：(1, 4, 9, 16, 25) 

def uppercase(s):
    return s.upper() 
strings = ('apple', 'banana', 'cherry') 
uppercase_strings = list(map(uppercase, strings)) 
print(uppercase_strings)  
# 输出：('APPLE', 'BANANA', 'CHERRY')
````



































***

## 注释


[^1]:当然python对变量类型卡的不是特别死，会自动帮你转换。比如在下面那个例子中如果是num=int(num),但我又对它num/3，输出也会输出0.333333333的
[^2]: 对于数字类型的元素，会按照数值大小进行比较，找出最大值 ; 对于字符串类型的元素，会按照字符的编码值进行比较，找出编码值最大的字符串 ; 对于列表和元组，会先比较每个元素的第一个值，如果相等再比较第二个值，以此类推，找出最大的元素 ; 集合不支持直接使用 min()函数求最大值 ; 字典也不支持直接使用 min()函数求最大值。
[^3]:对于数字类型的元素，会按照数值大小进行比较，找出最小值 ; 对于字符串类型的元素，会按照字符的编码值进行比较，找出编码值最小的字符串 ; 对于列表和元组，会先比较每个元素的第一个值，如果相等再比较第二个值，以此类推，找出最小的元素 ; 集合不支持直接使用 min()函数求最小值 ; 字典也不支持直接使用 min()函数求最小值。
[^4]: 和C语言中的数组的区别如下：1. 可变性：C 语言中的数组是静态的，一旦定义后长度就不能改变，不能在任何位置插入或删除元素；而 Python 中的列表是可变的，可以在任意位置插入或删除元素。2. 数据类型：C 语言的数组不能存放不同类型的数据，而 Python 中的列表可以存放不同类型的数据。3. 内存分配：在 C 语言中，创建数组时需要预先指定数组的容量大小，并为所有元素分配内存；而 Python 中的列表在存储元素时会根据实际情况动态分配内存。
[^5]:不是指按与字母顺序相反的顺序排列列表元素，而只是反转列表元素的排列顺序
[^6]:类似于链表，直接通过链表的地址去访问链表。在编程语言中，hash（哈希或散列）是一种将任意长度的二进制值（明文）映射为较短的固定长度的二进制值（Hash 值）的算法。它能给一大堆不规律的数据，给出长度固定的标签，这些标签的值分散得比较均匀。数据可以通过某种方式变成标签，但标签通常无法逆向变回数据。
[^7]:三者区别:arrow_forward:`isdigit()`：`True`：Unicode 数字、全角数字（双字节）、带圈圈的数字（④）、byte 数字（单字节）`False`：汉字数字、罗马数字、小数`Error`：无`isdecimal()`：`True`：Unicode 数字、全角数字（双字节）`False`：罗马数字、汉字数字、小数、byte 数字（单字节）`Error`：byte 数字（单字节）`isnumeric()`：`True`：Unicode 数字、全角数字（双字节）、罗马数字、汉字数字`False`：小数`Error`：byte 数字（单字节）

[^8]:代码中最后一行的`**d`是字典解包操作。当函数的参数以`**`开头时，表示可以接收一个字典，并将字典中的键值对作为关键字参数传递给函数。在`printdict`函数中，通过这种方式可以方便地处理字典类型的参数。例如，在`printdict (value1='key1', key2='value2')`中，就是将字典`{'value1': 'key1', 'key2': 'value2'}`通过解包的方式传递给了函数。而在`print(printdict(**d))`中，`d = {"afsf": "afsg", "af": "hh", "wr": "sg"}`，也是通过解包的方式将字典`d`的键值对作为关键字参数传递给了`printdict`函数。除了字典的解包，还有以下几种：列表、元组解包：使用 * 操作符，可将列表、元组中的元素作为单独的参数传递给函数，也可用于列表的拼接等操作。集合解包：虽然参考内容中未详细提及，但作为可迭代对象，集合也可以进行解包操作。字符串解包：将字符串中的字符作为单独的元素进行解包。函数返回值解包：当函数返回多个值时，可以将其进行解包分别赋值给多个变量。:facepunch:

