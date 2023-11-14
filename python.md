------

# 	1.print

print(2)

print(2+5)

print(2.4)

**print写入文件**

```python
fp = open("D:/use.txt",'a+')
print('hello',file=fp)#file = 文件指针
fp.close()#不是close(fp)
```

# 2.转义字符

\r 覆盖\r前的

\b 退一格

```python
print('hello\r  wor')
```

输出为wor

```python
print(r'hello\r  wor')
```

输入为 hello\r wor

**如果不想转义字符起作用 那么在前面加r或R**

**且最后一个字符不能是反斜杠，但可以双反斜**

# 3.变量的使用

变量由三部分组成

**标识**：表示对象所存储的内存地址，使用内置函数id()来获取。

**类型**：表示的是对象的数据类型，使用内置函数type()来获取。

**值**

变量多次赋值后，标识会改变。即：变量名会指向新的空间。

# 4.数据类型

**整数类型**

二进制以**0b**开头

八进制以**0o**开头

十六进制以**0x**开头

开头是python**识别进制**的根据

------

**浮点类型**

 浮点数存储不精确性

可导入**模块 decimal** 来解决

```python
from decimal import Decimal

print(Decimal('1.1')+Decimal('2.2'))
```

输出为3.3

如果不导入这个模块 那么输出为3.300000000003

------

**布尔类型**

True真为1，False假为0

python中，布尔值可以转成整数计算

```python
f1=True

print(f1+1)#注意大小写 True
```

输出为2

------

**字符串类型**

单引号 双引号 三引号都可以

单双引号只能在**同一行**中使用

而三引号可以**跨行**。

------



## 数据类型转换

将不同数据类型的数据拼接在一起需要进行转换

拼接需要用到运算符'+',起到链接作用。

**str()   int()    float()**

```python
name='张三'
age=20
#print('我叫'+name+'，今年'+age+'岁')
#上面一行会报错，下面一行才是正确的写法
print('我叫'+name+'，今年'+str(age)+'岁')
```

int，float，bool类型转换为str类型时不变

但是str转换为int类型，字符串会被转换为数字串

str(**小数**)转换为int类型，报错，因为字符串为**小数串**

float转换为int类型，会截取整数部分，舍掉小数

------

将str转成int类型时，**字符串必须为数字串（整数），非数字串**不允许转换,float()也是如此

int转为float时会加小数

76转为76.0

# 5.注释

**单行注释**

#开头，直到换行结束

**多行注释**

没有单独的标记，将一对三引号之间的代码称为多行注释

**中文编码声明注释**

在文件开头加上中文声明注释，用以指定源码文件的编码格式

**#coding:utf-8**以utf-8编码，用记事本打开另存为可看到文件编码模式

# 6.input

**返回值**类型，输入值类型为**str**，且需要**输入回答**

```python
a=input('请输入一个加数:')
b=input('请输入另一个加数:')
print(a+b)
```

输入10和20后，输出为1020，这里的+起到连接作用，因为input返回值类型为str，所以需要数据转换

```python
a=input('请输入一个加数:')
a=int(a)
b=input('请输入另一个加数:')
b=int(b)
print(a+b)
```

或者

```python
a=int(input('请输入一个加数:'))
b=int(input('请输入另一个加数:'))
print(a+b)
```

# 7.运算符

## 算术运算符

加减乘除 取余和c一样

与c不同的是，python的 **/** 会直接算出小数，而 **//** 是整除运算

且 ****** 表示幂运算

```python
print(11/2)#输出为5.5
print(11//2)#输出为5
print(2**3)#输出为8
```

但是有一点很关键，

当进行**整除运算**和**取余运算**时，两个数**正负不同**必须按照公式来计算

```python
print(-9//4)#输出为-3，列式算得-2.25，向下取整为-3
print(9//-4)#输出为-3
```

**整除运算，向下取整**

```python
print(9%-4)#输出为-3，   9-(-4)*(-3)=-3
print(-9%4)#输出为3，    -9-4*(-3)=3
```

**取余运算，余数=被除数-除数*商**

------

## 赋值运算符

顺序从右到左

支持**链式赋值**--a=b=c=20

```python
a=b=c=20
print(a,id(a))
print(b,id(b))
print(c,id(c))#a，b，c的标识(地址)相同，链式赋值只有一个整数对象，但有a，b，c三个引用指向这个对象
a=20
b=20
c=20
print(a,id(a))
print(b,id(b))
print(c,id(c))#结果相同
```

支持**参数赋值**

a+=30等等 与c一样

且如果一个**int进行除法运算**，那么他会**转换为float类型**，无论他是否能除断。

------

支持**解包赋值**

要求等号左右个数相同

```python
a,b=10,20#解包赋值
print(a,b)
a,b=b,a#交换两个数的值
print(a,b)
```

------

## 比较运算符

比较运算符的结果为bool类型

```python
a,b=10,20
print(a<b)#True
print(a>b)#False
```

**==**比较的是**变量的值**，**is**比较的是**对象的标识是否相同**

相同则返回True，不同则返回False，is not则相反

```python
a,b=10,20
print(a==b)#False
print(a is b)#False
print(a is not b)#True
a=b=10
print(a==b)#True
print(a is b)#True
print(a is not b)#False
```

## 布尔运算符

and

or

not

in

not in

**双运算数**

**and**  **or **

**单运算数**

**not**

```python
a,b=1,2
print(a==1 and b==2)#True  True and True--->True
print(a!=1 and b==2)#False   True and False--->False
                    #        Flase and True--->False
print(a!=1 and b!=2)#False   False and False--->False
```

**and，当两个运算数都为True时，运算结果才为True**

**or，只要有一个运算数为True，运算结果就为True**

**not，如果运算数为True，运算结果为False**

​         **如果运算数为False，运算结果为True**

​         **即对bool运算结果取反**

```python
str1='helloworld'
print('W' in str1)#False
print("w" in str1)#True
print("w" not in str1)#False
```

in与not in区分大小写且只能在字符串中使用

## 位运算符

将数据转成二进制进行计算

**位与&**

**对应数位都是1，结果数位才是1，否则为0**

```python
print(4&8)#结果为0
```

4 00000100

8 00001000

   00000000  结果为0

**位或|**

**对应数位都是0，结果数位才是0，否则为1**

```python
print(4|8)#结果为12
```

4 00000100

8 00001000

   00001100  结果为12

**左移位运算符<<**

从左到右，左为高，右为低

**高位溢出舍弃，低位补0**

```python
print(4<<1)#8
```

  00000100  4    左移后

  00001000  8

**右移位运算符>>**

**低位溢出舍弃，高位补0**

```python
print(4>>1)#2
```

4  00000100

​    00000010

------

## 运算符优先级

括号()>算术运算>位运算>比较运算>布尔运算

算术运算中**先算幂运算，再乘除>加减**

位运算中**先>>,<<，再&，再|**

比较运算中没有优先级，按照正常逻辑顺序

布尔运算中**先and，再or，再=**

# 8.布尔值

所有对象都有一个布尔值

获取对象的布尔值使用内置函数**bool()**

```python
print(bool(False))
print(bool(None))
print(bool(0))
print(bool(''))#空字符串
print(bool(""))#空字符串
print(bool([]))#空列表
print(bool(list()))#空列表
print(bool(()))#空元组
print(bool(tuple()))#空元组
print(bool({}))#空字典
print(bool(dict()))#空字典
print(bool(set()))#空集合
```

以下对象的布尔值为False

- False
- 数值0
- None
- 空字符串
- 空列表
- 空元组
- 空字典
- 空集合

# 9.结构

## 顺序结构

## 选择结构

### **双分支结构**

```python
money=1000
s=int(input('请输入取款金额:'))
if(s<=1000):
    money-=s
    print('取款成功，余额还有',money)
else:
    print('余额不足')
```

if，else的**缩进**要相同，且不用花括号，用**冒号**代替

------

### **多分支结构**

```python
score=int(input('请输入你的成绩:'))
if(score<=100 and score>=90):#也可以写成if(90<=score<=100):
    print('A')
elif(score<=90 and score>=80):
    print('B')
elif(...)
else:
    print('对不起，成绩有误，不在有效范围内')
```

与c不同的是&& ||用and  or来进行了替代，更方便记忆

且多分支的语句是**elif**，最后结尾仍然用**else**

判断条件中可以按照上面第二行注释来写，也更方便

------

### **嵌套if**

```python
use=input('您是会员吗?y/n')
money=int(input('原价为:'))
if use=='y':
    if money>=200:
        print('打八折,金额为:',money*0.8)
    elif 100<=money<200:
        print('打九折,金额为:',money*0.7)
    elif 0<=money<100:
        print('不打折,金额为:',money)
    else:
        print('金额输入错误')
else:
    if money>=200:
        print('打九折,金额为:',money*0.9)
    else:
        print('金额输入错误')
```

### 条件表达式

x  **if**  判断条件  **else**  y

如果判断条件的布尔值为**True**，条件表达式的返回值为**x**，**否则**条件表达式的返回值为**y**

```python
a=input('请输入一个整数')
b=input('请输入一个整数')
print(a+'>='+b if a>=b else a+'<'+b)
```

与c中的？：运算符差不多，如果判断条件成立，则返回前面的，否则返回后面的

------

### pass语句

语句什么都不做，只是一个占位符，用在语法上需要语句的地方

什么时候使用？--先搭建语法结构，还没想好代码怎么写的时候

哪些语句可以一起使用？

- if语句的条件执行体
- for-in语句的循环体
- 定义函数时的函数体

```python
money=int(input('请输入金额:'))
if 100<money<200:
    pass
else:
    pass
```

这样写语法不会报错

### 特殊情形

```python
age=int(input('请输入你的年龄:'))
if age:#这样写就直接判断age的布尔值
    print(age)
else:
    print('年龄为:',age)
```

输入18 输出为 18

输入0 输出为 年龄为：0

**如果age 的布尔值为True 则执行if**

**如果为False，则执行else**

------

## 循环结构

### 内置函数range()

用于生成一个整数序列。创建range对象的三种方式：

- range(stop)-->创建一个[0,stop)之间的整数序列，**步长**为1

  ```python
  r=range(10)
  print(r)#range(0,10)，start默认为0
  print(list(r))#用于查看range对象中的整数序列
  			 #[0,1,2,3,4,5,6,7,8,9,]
  ```

- range(start,stop)-->创建一个[start,stop)之间的整数序列，步长为1

  ```python
  r=range(1,10)
  print(r)#range(1,10)
  print(list(r))#[1,2,3,4,5,6,7,8,9]
  ```

- range(start,stop,step)-->创建一个[start,stop)之间的整数序列，步长为step

  ```python
  r=range(1,10,2)
  print(r)#range(1,10,2)
  print(list(r))#[1,3,5,7,9]步长为2,可以理解为从1开始每走两个数字将落点数字拉进整数序列
  ```

上面学的in，not in也可以用来判断指定的整数在序列中是否存在

```python
r=range(1,10,2)
print(r)
print(list(r))
print(3 in r)#Ture
print(4 in r)#False
```

返回值是一个**迭代器对象**。

range类型的**优点**：不管range对象表示的整数序列有多长，所有range对象占用的内存空间都是相同的，因为仅仅需要存储start，stop和step，只有当用到range对象时，才会去计算序列中的相关元素

**通常会用到for循环中的判断条件对象**

### while循环

```python
a=1
while a<10:
    print(a)
    a+=1
```

```python
a=1
sum=0
while a<10:
    sum+=a
    a+=1
print(sum)
```

### for-in循环

- in表达从(字符串、序列等)中依次取值，又称为遍历
- for-in遍历的对象必须是可迭代对象

语法结构

​	**for**  自定义的变量  **in**  可迭代对象：

​			循环体

```python
str='python'
for item in str:
    print(item)
```

输出为

p

y

t

h

o

n

一次循环将一个字符赋给item，并不是一整个

```python
for item in range(10):
    print(item)#和上面一样 同理
```

如果在循环体中不需要使用到自定义变量，可将自定义变量写为“_”

```python
for _ in range(5):
    print('python')#输出5次
```

​    

求1-100内的偶数之和，用两种循环方式实现

```python
sum=0
for a in range(1,101):
    if a%2==0:
        sum+=a
print(sum)
```

```python
sum=0
a=0
while a<=100:
    if a%2==0:
        sum+=a
        a+=2
print(sum)
```

#### 输入三位数的水仙花数

```python
for a in range(100,1000):
    num1=a%10#个位
    num2=a%100//10#十位
    num3=a//100#百位
    if num1**3+num2**3+num3**3==a:
        print(a,'是水仙花数')
```

要注意if的缩进一定要与上面一致，如果和for一致那么if就在for外面了，且不会报错。**python一定要注意缩进！！！**

#### break，continue

break跳出一整个循环，continue跳出这一轮循环，进入下一轮循环。

但都只仅限于这一层循环。

### else语句

if...else，if不成立时执行else

while...else，没有碰到break时执行else

for...else，没有碰到break时执行else

------

### 嵌套循环

```python
for i in range(1,4):#输出一个3行4列的矩阵
    for m in range(1,5):
        print('*', end='\t')#end=''，是print函数的一个参数，为末尾传递一个字符串代替原有的换行符。  不换行输出
    print()#换行
```

**九九乘法表**

```python
for i in range(1,10):
    for j in range(1,i+1):
        print(i,'*',j,'=',i*j,end='\t')
    print()
```

# 10.列表

## 列表的创建

列表需要使用中括号[]，元素之间使用，分隔。

也可以使用list()函数

```python
st=['hello','world']
st2=list(['hello','world'])
print(st)
print(st2)#都输出 ['hello','world']
```

## 列表的特点

元素有序排序

索引映射唯一数据

**任意数据类型混存**

可以存储重复数据

**根据需要动态分配和回收内存**

## 列表查询

**index()获取索引**

```python
st=['hello','world','1']
print(st.index('hello'))#注意是.
#如果列表中有相同元素则只返回列表中相同元素的第一个元素的索引
#如果查询的元素在列表中不存在，则会抛出valueError
```

```python
st=['hello','world','1','2']
print(st.index('hello',1,3))
```

还可以在指定的start和stop间查找

------

### **获取列表中单个元素**

正向索引0到(N-1)

逆向索引-N到-1

```python
st=['hello','world','1','2','998']
print(st[1])
print(st[-4])#都输出 world
```

------

### **获取列表中的多个元素******(切片)****

**列表名[start:stop:step]**

切片的结果---原列表片段的拷贝

切片的范围---[start,stop)

step默认为1---简写为[start:stop]

step为**正数**---[:stop:step]---切片的第一个元素默认是列表的第一个元素

​                     [start::step]---切片的最后一个元素默认是列表的最后一个元素

​	上述两种都是 从start开始往后计算切片

step为**负数**，与上面情形相反

```python
st=[1,2,3,4,5,6,7]
print(st[1:5:1])#[2,3,4,5]
```

```python
st=[1,2,3,4,5,6,7]
print(st[5:1:-1])#[6,5,4,3]
```

------

### **判断指定元素在列表中是否存在**

​	**in，not in**

### 列表元素的遍历

**for 迭代标量 in 列表**

## 列表元素的增删改操作

### 增加操作

***append()，在列表的末尾添加一个元素***

```python
st=[1,2,3,4,5,6,7]
st.append(100)
print(st)#[1,2,3,4,5,6,7,100]
#且没有创建新的列表，前后列表的标识相同
```

```python
st=[1,2,3,4,5,6,7]
st1=['hello','world']
st.append(st1)
print(st)#[1, 2, 3, 4, 5, 6, 7, ['hello', 'world']]
#将st1作为一个元素添加到列表的末尾，这时应用extend()
```

***extend()，在列表的末尾至少添加一个元素***

```python
st=[1,2,3,4,5,6,7]
st1=['hello','world']
st.extend(st1)
print(st)#[1, 2, 3, 4, 5, 6, 7, 'hello', 'world']
```

***insert()，在任意位置上添加一个元素***

```python
st=[1,2,3,4,5,6,7]
st.insert(4,100)
print(st)#[1, 2, 3, 4, 100, 5, 6, 7]
```

***切片，在任意的位置上添加N多个元素***

```python
st=[1,2,3,4,5,6,7]
st1=[100,200,300,400]
st[1:]=st1#将st从索引为1的地方开始切，并将st1添加上去
print(st)#[1, 100, 200, 300, 400]
```

------

### 删除操作

**remove()，一次删除一个元素，重复元素只删除一个，若元素不存在则输出valueError。**

```python
st=[1,2,3,4,5,6,7]
st.remove(2)
print(st)#[1,3,4,5,6,7]
```

**pop()，删除一个指定索引位置上的元素，指定索引不存在则抛出IndexError，不指定索引则删除列表中最后一个元素。**

```python
st=[1,2,3,4,5,6,7]
st.pop(3)
print(st)#[1,2,3,5,6,7]
```

```python
st=[1,2,3,4,5,6,7]
st.pop()
print(st)#[1,2,3,4,5,6]
```

**切片，一次至少删除一个元素，且将产生一个新的列表对象**

```python
st=[1,2,3,4,5,6,7]
new_st=st[1:3]
print(st)
print(new_st)#[2,3]
```

**也可以不产生新的列表对象**

```python
st=[1,2,3,4,5,6,7]
st[1:3]=[]
print(st)#[1,4,5,6,7]
```

------

**clear清除列表中的所有元素**

```python
st=[1,2,3,4,5,6,7]
st.clear()
print(st)#[]
```

**del删除对象列表**

```python
st=[1,2,3,4,5,6,7]
del st
print(st)#报错，st已经被删除，没有st这个列表了。
```

------

### 修改操作

​	**为指定索引的元素赋予一个新值**

```python
st=[1,2,3,4,5,6,7]
st[3]='a'
print(st)#[1, 2, 3, 'a', 5, 6, 7]
```

​	**为指定的切片赋予一个新值**

```python
st=[1,2,3,4,5,6,7]
st[1:3]=['a','b','c']#可以理解为先删除索引1和2的对象再塞入右值
print(st)#[1, 'a', 'b', 'c', 4, 5, 6, 7]
```

------

### **排序操作**

​	**调用sort()方法，列表中的所有元素默认按照从小到大的顺序进行排序，可以指定reverse=True，进行降序排序。**

```python
st=[1,100,3,200,5,6,7]
st.sort()#(reverse=False)   
print(st)#[1, 3, 5, 6, 7, 100, 200]
#且排序前后，列表的标识没有更改，是同一个列表。
```

```python
st=[1,100,3,200,5,6,7]
st.sort(reverse=True)
print(st)#[200, 100, 7, 6, 5, 3, 1]
```

这个排序如果int和str类型混合将会报错。

------

**sorted()，可以指定reverse=True，进行降序排序，原列表不发生改变，生成一个新列表**

```python
st=[1,100,3,200,5,6,7]
st1=sorted(st)
print(st)#[1, 100, 3, 200, 5, 6, 7]
print(st1)#[1, 3, 5, 6, 7, 100, 200]
```

```python
st=[1,100,3,200,5,6,7]
st1=sorted(st,reverse=True)
print(st)
print(st1)#[200, 100, 7, 6, 5, 3, 1]
```

------

## 列表生成式

​	**语法格式：[i*i	for	i	in	range(1,10)]**

i*i表示列表元素的表达式，i为自定义变量，range(1,10)为可迭代对象。

**列表表达式通常包含自定义变量。**

```python
st=[i for i in range(1,10)]
print(st)#[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```python
st=[i*i for i in range(1,10)]
print(st)#[1, 4, 9, 16, 25, 36, 49, 64, 81]
```

```python
st=[i*3 for i in range(1,10)]
print(st)#[3, 6, 9, 12, 15, 18, 21, 24, 27]
```

# 11.字典

​	python内置的数据结构之一，与列表一样是一个可变序列。

​	以**键值对**的方式存储数据，字典是一个**无序且不可变**的序列。

```python
score={'张三':100,'李四':90,'王五':80}
print(score)
```

这里的张三称为键，100称为值，'张三':100就是一个键值对。

字典示意图与哈希表类似，字典是根据部首或者拼音查找相对应的页码，而python中的字典是根据key查找value所在的位置。

**字典创建时，'索引'与输入顺序不一定相同，他们的排序是根据哈希排序计算得来的。**

**字符串也是不可变序列，不可变序列不能进行增删改**

------

## 字典的创建

​	**使用花括号**

```python
score={'张三':100,'李四':90,'王五':80}
```

​	**使用内置函数dict()**

```python
student=dict(name='jack',age=20)
print(student)#{'name': 'jack', 'age': 20}
```

​	**空字典**

```python
d={}
print(d)#{}
```

------

## 字典元素的获取

​	**score['张三']**

​	**get()方法，score.get('张三')**

[]取值与使用get()取值的**区别**

​	[]如果字典中不存在指定的key，则抛出KeyError异常

```python
score={'张三':100,'李四':90,'王五':80}
print(score['张三'])#100
print(score['五五'])#KeyError
```

​	get()方法取值，如果字典中不存在指定的key，并不会抛出KeyError，而是返回None，可以通过参数设置默认的value，以便指定的key不存在时返回。

```python
score={'张三':100,'李四':90,'王五':80}
print(score.get('张三'))#100
print(score.get('五五'))#None
print(score.get('五五',233))#233是在查找'五五'所对的value不存在时，提供的一个默认值。
```

## 字典元素的增删改操作

### 	key的判断

​		**in，not in**

​		指定的key在字典中存在返回True

```python
score={'张三':100,'李四':90,'王五':80}
print('张三' in score)#True
print('五五' in score)#False
```

### 字典元素的删除

```python
score={'张三':100,'李四':90,'王五':80}
del score['张三']#删除一对
print(score)#{'李四': 90, '王五': 80}
```

```python
score={'张三':100,'李四':90,'王五':80}
score.clear()#清空字典
print(score)#{}
```

### 字典元素的新增与修改

```python
score={'张三':100,'李四':90,'王五':80}
score['陈六']=70##新增
print(score)#{'张三': 100, '李四': 90, '王五': 80, '陈六': 70}

score['张三']=50##修改
print(score)#{'张三': 50, '李四': 90, '王五': 80, '陈六': 70}
```

## 获取字典视图

​	**keys()**，获取字典中所有的key。

​	**values()**，获取字典中所有的value。

​	**items()**，获取字典中所有的key，value对。

```python
score={'张三':100,'李四':90,'王五':80}
key=score.keys()
print(key)#dict_keys(['张三', '李四', '王五'])
print(type(key))#<class 'dict_keys'>

item=score.items()
print(item)#dict_items([('张三', 100), ('李四', 90), ('王五', 80)])
			##('张三', 100)是元组

value=score.values()
print(value)#dict_values([100, 90, 80])
```

------

## 字典元素的遍历

```python
score={'张三':100,'李四':90,'王五':80}
for a in score:
    print(a)#张三
		   #李四
		   #王五
```

```python
score={'张三':100,'李四':90,'王五':80}
for a in score:
    print(score.get(a))
'or'  print(score[a])
    				 #100
					 #90
					 #80
```

------

## 字典的特点

- 字典中所有的元素都是一个key-value对，key不允许重复，value可以重复。

  ```python
  a={'name':'张三','name':'李四'}
  print(a)#{'name': '李四'}
  
  a={'name':'张三','nickname':'李四'}
  print(a)#{'name': '张三', 'nickname': '李四'}
  
  a={'name':'张三','nickname':'张三'}
  print(a)#{'name': '张三', 'nickname': '张三'}
  ```

- 字典中的元素是无序的

- 字典中的key必须是不可变对象

- 字典也可以根据需要动态地伸缩

- 字典会浪费较大的内存，是一种使用空间换时间的数据结构

## 字典生成式

内置函数zip()，用于将可迭代的对象作为参数，将对象中对应的元素打包成一个元组，然后**返回**由这些元组组成的**列表**。

```python
items=['fruits','books','others']
prices=[96,78,85]
st=zip(items,prices)
print(list(st))#[('fruits', 96), ('books', 78), ('others', 85)]
```

**生成式**

{item.upper()	:	price	for	item,price	in	zip(items,prices)}

key的表达式  **:**  value的表达式  **for**  自定义key，value的变量  **in**  可迭代对象

```python
items=['fruits','books','others']
prices=[96,78,85]
d={item:price for item,price in zip(items,prices)}
print(d)#{'fruits': 96, 'books': 78, 'others': 85}
```

```python
items=['fruits','books','others']
prices=[96,78,85]
d={item.upper():price for item,price in zip(items,prices)}
print(d)#{'FRUITS': 96, 'BOOKS': 78, 'OTHERS': 85}
```

如果items和prices的数量不同，以短的为基准相对应。

# 12.元组

## 什么是元组

​	python内置的数据结构之一，是一个不可变序列。

​		不可变序列：字符串、元组。没有增删改的操作。

​		可变序列：列表、字典。可以对序列执行增删改的操作。

​					

```python
st=[50,60]
print(id(st))#2047475878656
st.append(100)
print(id(st))#2047475878656

s='hello'
print(id(s))#2047475877936
s=s+'world'
print(id(s))#2047475878000
```

可变序列在更改前后是同一个序列，但不可变序列不是同一个。

## 元组的创建方式

​	直接小括号()

```python
	t1=('python','hello',90)
    t2='python','hello',90
    print(t2)#('python', 'hello', 90)
    print(t1)#('python', 'hello', 90)
    #可以省略小括号，还是元组。
```

​	使用内置函数tuple()

```python
t=tuple(('python','hello',90))
```

​	只包含一个元素的元组需要使用逗号和小括号。

```python
t=(10,)#如果不加小括号和逗号，那么编译器会认为是其他类型
```

**空元组**

```python
t=()
t=tuple()
print(t)#()
```

------

## 为什么要将元组设计成不可变序列

​	在多任务环境下，同时操作对象时不需要枷锁(重要数据多人操作可能会乱，改成不可变就没有这个问题)。

​	因此，在程序中尽量使用不可变序列。

**注意事项**

- 元组中存储的是对象的引用

- 如果元组中对象是不可变对象，则不能再引用其它对象

- 如果元组中对象时可变对象，则可变对象的引用不允许改变，但数据可以改变

  

## 元组遍历

1.使用索引.

```python
s=('python','123','hello')
print(s[1])
```

2.for in 循环

```python
s=('python','123','hello')
for item in s:
    print(item)
```

------

# 13.集合

可变类型的序列，没有value的字典。

## **创建方式**

​	直接{}

```python
s={'python','hello'}
```

​	使用set()

```python
s=set('python')
print(type(s))
```

创建空集合只能用set，不能{}，否则是空字典。

## 集合的相关操作

### 	判断操作

​	in 或 not in

```python
s={1,2,3,4,5}
print(1 in s)#True
print(10 in s)#False
```

### 	新增操作

**添加一个**

```python
s={1,2,3,4,5}
print(s)
s.add(50)
print(s)
```

**添加多个**

```python
s={1,2,3,4,5}
print(s)
s.update({10,20})#update不仅可以放集合还可以放列表，元组
print(s)
```

### 	删除操作

一次删除一个指定元素

```python
s={1,2,3,4,5}
print(s)
s.remove(4)#指定元素不存在抛出keyerror
print(s)
```

```python
s={1,2,3,4,5}
print(s)
s.discard(4)#不存在也不抛出keyerror
print(s)
```

一次删除一个随机元素

```python
s={1,2,3,4,5}
print(s)
s.pop()#不能添加参数
print(s)
```

清空集合

```python
s={1,2,3,4,5}
print(s)
s.clear()
print(s)#set()
```

## 集合间的关系

### 两个集合是否相等

用!= 或者 ==

```python
s={1,2,3,4}
s1={1,2,30,40}
print(s==s1)#False
```

### 一个集合是否是另一个集合的子集

```python
s={1,2,3,4}
s1={1,2}
print(s1.issubset(s))#True,s1是s的子集
```

### 一个集合是否是另一个集合的超集

```python
s={1,2,3,4}
s1={1,2}
print(s.issuperset(s1))#True,s是s1的超集
```

### 两个集合是否没有交集

```python
s={1,2,3,4}
s1={1,2}
print(s.isdisjoint(s1))#False,s和s1有交集
```

## 集合的数学操作

### 交集

```python
s={1,2,3,4}
s1={1,2}
print(s.intersection(s1))#{1,2}
print(s1 & s2)#等价
```

### 并集

```python
s={1,2,3,4}
s1={1,2,5}
print(s.union(s1))#{1,2,3,4,5}
print(s | s1)#等价
```

### 差集

```python
s={1,2,3,4}
s1={1,2,5}
print(s.difference(s1))#{3,4}
print(s - s1)#等价
```

### 对称差集(两集合不共有的元素)

```python
s={1,2,3,4}
s1={1,2,5}
print(s.symmetric_difference(s1))#{3,4,5}
print(s ^ s1)#等价
```

## 集合生成式

用于生成集合的公式，与列表生成式一样，把方括号改成花括号就可以了。

没有元组生成式(因为他是不可变序列)

```python
st={ i*i for i in range(6)}#集合
print(st)#{0, 1, 4, 9, 16, 25}
st={ i*i for i in range(10)}
print(st)#{0, 1, 64, 4, 36, 9, 16, 49, 81, 25}
		#无序性
```

```python
st=[ i*i for i in range(6)]#列表
print(st)#{0, 1, 4, 9, 16, 25}
```

# 14.数据结构总结

| 数据结构    | 是否可变 | 是否重复                 | 是否有序 | 定义符号    |
| ----------- | -------- | ------------------------ | -------- | ----------- |
| 列表(list)  | 可变     | 可重复                   | 有序     | [ ]         |
| 元组(tuple) | 不可变   | 可重复                   | 有序     | ( )         |
| 字典(dict)  | 可变     | key不可重复，value可重复 | 无序     | {key:value} |
| 集合(set)   | 可变     | 不可重复                 | 无序     | { }         |

# 15.字符串

**不可变**的字符序列

## 驻留机制

​	仅保存一份相同且不可变字符串的方法，不同的值被存放在字符串的驻留池中，python的驻留机制对相同的字符串只保留一份拷贝，后续创建相同字符串时，不会开辟新空间，而是把该字符串的地址赋给新创建的变量。

a='python'

b='python'

a，b变量只占用一个python的空间地址。

**驻留机制的几种情况（交互模式cmd）**

- 字符串的长度为0或1时
- 符合标识符的字符串（含有字母，数字，下划线的字符串）
- 字符串只在编译时进行驻留，而非运行时
- [-5,256]之间的整数数字

**优缺点**

- 当需要值相同的字符串时，可以直接从字符串池里拿来使用，避免频繁的创建和销毁，提升效率和节约内存，因此拼接字符串和修改字符串是比较影响性能的。
- 在需要进行字符串拼接时建议使用str类型的join()方法，而非+，因为join方法是先计算出所有字符中的长度，然后再拷贝，只new（创建）一次对象，效率要比"+"高

## 字符串的常用操作

### 查询操作

| 功能     | 方法名称 | 作用                                                         |
| -------- | -------- | ------------------------------------------------------------ |
|          | index()  | 查找子串substr第一次出现的位置，如果查找的子串不存在时，则抛出valueerror。 |
| 查询方法 | rindex() | 查找子串substr最后一次出现的位置，如果查找的子串不存在时，则抛出valueerror。 |
|          | find()   | 查找子串substr第一次出现的位置，如果查找的子串不存在时，则返回-1. |
|          | rfind()  | 查找子串substr最后一次出现的位置，如果查找的子串不存在时，则返回-1. |

```python
s='hello,hello'
print(s.index('lo'))#3
print(s.find('lo'))#3
print(s.rindex('lo'))#9
print(s.rfind('lo'))#9
```

### 大小写转换操作

| 功能       | 方法名称     | 作用                                                         |
| ---------- | ------------ | ------------------------------------------------------------ |
|            | upper()      | 把字符串中所有字符都转成大写字母                             |
|            | lower()      | 把字符串中所有字符都转成小写字母                             |
| 大小写转换 | swapcase()   | 把字符串中所有大写字母转成小写字母，把所有小写字母转成大写字母 |
|            | capitalize() | 把第一个字符转换为大写，其余字符转换为小写                   |
|            | title()      | 把每个单词的第一个字符转换为大写，把每个单词的剩余字符转换为小写 |

```python
s='hEllo,hello'
print(s.upper())
#s1=s.upper()
#print(s1)   等效，s与s1地址不同，不是同一个，因为是不可变序列。
print(s.lower())
print(s.swapcase())
print(s.capitalize())
print(s.title())
#HELLO,HELLO
#hello,hello
#HeLLO,HELLO
#Hello,hello
#Hello,Hello
```

### 对齐操作

| 功能       | 方法名称 | 作用                                                         |
| ---------- | -------- | ------------------------------------------------------------ |
|            | center() | 居中对齐，第1个参数指定宽度，第2个参数指定填充符，第2个参数是可选的，默认是空格，如果设置宽度小于实际宽度则返回原字符串 |
| 字符串对齐 | ljust()  | 左对齐，第1个参数指定宽度，第2个参数指定填充符，第2个参数是可选的，默认是空格，如果设置宽度小于实际宽度则返回原字符串 |
|            | rjust()  | 右对齐，第1个参数指定宽度，第2个参数指定填充符，第2个参数是可选的，默认是空格，如果设置宽度小于实际宽度则返回原字符串 |
|            | zfill()  | 右对齐，左边用0填充，该方法只接收一个参数，用于指定字符串的宽度，如果指定的宽度小于等于字符串的长度，则返回字符串本身 |

```python
s='hello,python'
print(s.center(20))
print(s.center(20,'*'))
print(s.ljust(20,'*'))
print(s.rjust(20,'*'))
print(s.zfill(20))
#    hello,python    
#****hello,python****
#hello,python********
#********hello,python
#00000000hello,python
```

### 劈分操作

| 功能         | 方法名称 | 作用                                                         |
| ------------ | -------- | ------------------------------------------------------------ |
|              |          | 从字符串的左边开始劈分，默认的劈分字符是空格字符串，返回的值都是一个列表 |
|              | split()  | 以通过参数sep指定劈分字符串的分隔符                          |
|              |          | 通过参数maxsplit指定劈分字符串时的最大劈分次数，在经过最大次劈分之后，剩余的子串会单独做为一部分 |
| 字符串的劈分 |          | 从字符串的右边开始劈分，默认的劈分字符是空格字符串，返回的值都是一个列表 |
|              | rsplit() | 以通过参数sep指定劈分字符串的分隔符                          |
|              |          | 通过参数maxsplit指定劈分字符串时的最大劈分次数，在经过最大次劈分之后，剩余的子串会单独做为一部分 |

```python
s='hello world python'
st=s.split()
print(st)
st1='hello|world|python'
print(st1.split(sep=('|')))
print(st1.split(sep='|',maxsplit=1))
print(st1.rsplit(sep='|',maxsplit=1))
#['hello', 'world', 'python']
#['hello', 'world', 'python']
#['hello', 'world|python']
#['hello|world', 'python']
```

### 判断方法

| 功能             | 方法名称       | 作用                                                         |
| ---------------- | -------------- | ------------------------------------------------------------ |
|                  | isidentifier() | 判断指定的字符串是不是合法的标识符                           |
|                  | isspace()      | 判断指定的字符串是否全部由空白字符组成（回车、换行、水平制表符） |
|                  | isalpha()      | 判断指定的字符串是否全部由字母组成                           |
| 判断字符串的方法 | isdecimal()    | 判断指定的字符串是否全部由十进制的数字组成                   |
|                  | isnumeric()    | 判断指定的字符串是否全部由数字组成                           |
|                  | isalnum()      | 判断指定的字符串是否全部由字母和数字组成                     |

中文在isidentifier()，isalpha()，isalnum()，中是True。

中文数字 一二三四，和罗马数字，在isdecimal()中是False，但是在isnumeric()中是True。

### 替换和合并

| 功能         | 方法名称  | 作用                                                         |
| ------------ | --------- | ------------------------------------------------------------ |
| 字符串替换   | replace() | 第1个参数指定被替换的子串，第2个参数指定替换子串的字符串，该方法返回替换后得到的字符串，替换前的字符串不发生变化，调用该方法时可以通过第3个参数指定最大替换次数 |
| 字符串的合并 | join()    | 将列表或者元组中的字符串合并成一个字符串                     |

```python
s='hello,python,python'
print(s.replace('python','java',1))
print(s.replace('python','java',2))

#hello,java,python
#hello,java,java
```

```python
s='hello','python','python'
print('|'.join(s))
print(''.join(s))

#hello|python|python
#hellopythonpython
```

### 比较操作

**运算符**：>，>=，<，<=，==，!=

**比较规则**：首先比较两个字符串中的第一个字符，如果相等则继续比较下一个字符，依次比较下去，直到两个字符串中的字符不相等时，其比较结果就是两个字符串的比较结果，两个字符串中的所有后续字符将不再被比较。

**比较原理**：两上字符进行比较时，比较的是其原始值，调用内置函数ord可以得到指定字符的原始值。与内置函数ord对应的内置函数chr，调用chr时指定原始值可以得到其对应的字符。

类似于ASCII码值。

### 切片操作

字符串是不可变类型，不具备增删改等操作，所以切片操作将产生新的对象。

```python
s='hello,python'
s1=s[:5]
s2=s[6:]
s3=s1+'!'+s2
print(s1)
print(s2)
print(s3)
#hello
#python
#hello!python
```

也包含三个参数，等同上。起点终点步长。

如果步长是负数，那么会倒过来，因为字符串的负向索引是反过来的。

起点终点步长都可为负数，按负向索引进行切片。

### 格式化字符串

两种方式

​	%作占位符

​	{}作占位符

```python
name='张三'
age=20
print('我叫%s，今年%d' % (name,age))
print('我叫{0}，今年{1}'.format(name,age))
print(f'我叫{name}，今年{age}')
#我叫张三，今年20
#我叫张三，今年20
#我叫张三，今年20
```

```python
print('{0:.3}'.format(3.1415926))#3.14
print('{0:.3f}'.format(3.1415926))#3.142
print('{1:}'.format(3.1415926,1))#1
#0是索引，代替format()里面索引为0的参数
```

### 编码转换

两台计算机交换数据时需要编码转换

**编码与解码的方式**

​	编码：将字符串转换为二进制数据（bytes）

​	解码：将bytes类型的数据转换成字符串类型

```python
s='天涯共此时'
print(s.encode(encoding='GBK'))
print(s.encode(encoding='UTF-8'))
#b'\xcc\xec\xd1\xc4\xb9\xb2\xb4\xcb\xca\xb1'
#b'\xe5\xa4\xa9\xe6\xb6\xaf\xe5\x85\xb1\xe6\xad\xa4\xe6\x97\xb6'

s1=s.encode(encoding='GBK')
print(s1.decode(encoding='GBK'))#天涯共此时
#编码方式与解码方式必须相同，不然不能进行解码。
```

GBK与UTF-8是编码格式，在GBK中一个中文占两个字节，在UTF-8中一个中文占三个字节。

# 16.函数

## 创建与调用

​	**创建**

​	def 函数名 ([输入参数])：

​		  函数体

​		  [return xxx]



```python
def plus(a,b):
    c=a*b
    return c
result=plus(5,6)#位置实参
print(result)#30
```

## 参数传递

实参，形参，和c语言的函数差不多。

**传递方式**

​	**位置实参**

​		根据形参对应的位置进行实参传递

​	**关键字实参**

​		根据形参名称进行实参传递

```python
def plus(a,b):
    c=a*b
    return c
result=plus(b=5,a=6)#关键字实参
print(result)
```

**内存变化分析**

在函数调用过程中，进行参数的传递

**如果是不可变对象，在函数体内的修改不会影响实参的值。**

**如果是可变对象，在函数体内的修改会影响到实参的值。**

## 返回值

​	函数返回多个值时，结果为**元组**

​	返回1个值时，直接返回**相同类型**

```python
def fun(num):
    odd=[]
    even=[]
    for i in num:
        if i%2:
            odd.append(i)
        else:
            even.append(i)
    return odd,even
st=[1,2,3,4,5,6,7,8]
print(fun(st))#([1, 3, 5, 7], [2, 4, 6, 8])
```

## 默认值

```python
def plus(a,b=2):
    c=a*b
    return c
print(plus(5))#10，5给了a，b采用默认值2
print(plus(5,3))#15，5给了a，3给了b。
```

print函数的默认值是换行

```python
print('hello')
print('world')
#hello
#world
```

要改变换行可以进行如下操作

```python
print('hello',end='\t')
print('world')
#hello	world
```

## 参数定义

**个数可变的位置参数**

​	定义函数时，可能无法事先确定传递的位置实参的个数时，使用可变的位置参数

​	使用*定义个数可变的位置形参

​	结果为一个元组

**个数可变的关键字形参**

​	定义函数时，可能无法事先确定传递的关键字实参的个数时，使用可变的关键字形参

​	使用**定义个数可变的关键字形参

​	结果为一个字典

**在一个函数的定义过程中，既有个数可变的关键字形参，也有个数可变的位置形参，要求，个数可变的位置形参，放在个数可变的关键字形参之前。**

```python
def fun(*a):
    print(a)
fun(10)
fun(1,2,3)
fun(20,30)

#(10,)
#(1, 2, 3)
#(20, 30)
```

```python
def fun(*a):
    print(a[0])
fun(10)
fun(1,2,3)
fun(20,30)

#10
#1
#20
```

```python
def fun(**a):
    print(a)

fun(a=10)
fun(a=20,b=30,c=40)

#{'a': 10}
#{'a': 20, 'b': 30, 'c': 40}
```

```python
def fun(a,b,c):
    print('a=',a)
    print('b=',b)
    print('c=',c)
st=[10,20,30]
dic={'a':10,'b':20,'c':30}
fun(*st)#*，将列表中的每个元素转换为位置参数传入
fun(**dic)#**，将字典的键值对转换为关键字参数传入
#a= 10
#b= 20
#c= 30
```

```python
def fun(a,b,*,c,d):#c，d只能采用关键字实参传递
```

 **从*之后的参数，在函数调用时，只能采用关键字实参传递。**

## 变量的作用域

与c语言一样，不同的是，在函数里使用 global前缀 定义变量，在函数外也可使用。

## 递归函数

与c语言相同

**计算阶乘**

```python
def fun(a):
    if(a==1):
        return 1
    else:
        return a*fun(a-1)
print(fun(6))#720
```

**斐波那契数列**

```python
def fun(a):
    if(a==1):
        return 1
    elif a==2:
        return 1
    else:
        return fun(a-1)+fun(a-2)
print(fun(6))#8

for i in range(1,6):
    print(fun(i))#1,1,2,3,5
```

# 17.异常处理机制

```python
try:
    a=int(input('请输入第一个整数'))#10
    b=int(input('请输入第二个整数'))#0
    result=a/b
    print('结果为:',result)
except ZeroDivisionError:#except后接错误类型
    print('对不起，除数不允许为0')#输出此句话
#可以多个except
except ValueError:#给a赋值A，就会输出下面的print
    print('只能输入数字串')
print('程序结束')
```

**try...except...else结构**

​	如果try块中没有抛出异常，则执行else块，如果try中抛出异常，则执行except块。

```python
try:
    a=int(input('请输入第一个整数'))
    b=int(input('请输入第二个整数'))
    result=a/b
    print('结果为:',result)
except ZeroDivisionError:
    print('对不起，除数不允许为0')
else:
    print('结果为:',result)
```

```python
try:
    a=int(input('请输入第一个整数'))
    b=int(input('请输入第二个整数'))
    result=a/b
    print('结果为:',result)
except ZeroDivisionError as e:#在这后面跟个，as+变量，会让变量赋值为错误类型
    print('对不起，除数不允许为0',e)#对不起，除数不允许为0 division by zero
else:
    print('结果为:',result)
```

**try...except...else...finally结构**

​	finally块无论是否发生异常都会被执行，能常用来释放try块中申请的资源。

```python
try:
    a=int(input('请输入第一个整数'))
    b=int(input('请输入第二个整数'))
    result=a/b
    print('结果为:',result)
except ZeroDivisionError as a:
    print('对不起，除数不允许为0',a)
else:
    print('结果为:',result)
finally:
    print('无论是否产生异常，总会被执行的代码')
```

## 异常类型

| 序号 | 异常类型          | 描述                        |
| ---- | ----------------- | --------------------------- |
| 1    | ZeroDivisionError | 除(或取模)零(所有数据类型)  |
| 2    | IndexError        | 序列中没有此索引(index)     |
| 3    | KeyError          | 映射中没有这个键            |
| 4    | NameError         | 未声明/初始化对象(没有属性) |
| 5    | SyntaxError       | python 语法错误             |
| 6    | ValueError        | 传入无效的参数              |

## traceback模块

```python
import traceback
try:
    print(1/0)
except:
    traceback.print_exc()#打印出出现错误的具体位置
```

# 18.类与对象

## 类的创建

```python
class Student:#创建类
    a=1#直接写在类里面的变量，称为类属性
    def __init__(self,name,age):
        			 #self.name称为实体属性，将局部变量的name的值赋给实体属性
        self.name=name#self后面可以不是name，但一般是与变量名相同
        self.age=age
    
    def play(self):#实例方法，在类外定义的叫函数，在类中定义的叫方法
        print('出去玩')
    
    @classmethod    #类方法
    def game(self):
        print('游戏')
        
    @staticmethod#静态方法
    def run():
        print('静态方法')
```

## 对象的创建

​	对象的创建又称为类的实例化

​	**语法**：实例名=类名()

```python
class Student:
    a=1
    def __init__(self,name,age):
        self.name=name
        self.age=age

    def play(self):
        print('出去玩')

    @classmethod
    def game(self):
        print('游戏')

    @staticmethod
    def run():
        print('静态方法')

st=Student('张三',20)#对象
st.game()#游戏
Student.eat(st)#类名,方法名(类的对象)-->实际上就是方法定义处的self
```

## 类属性、类方法、静态方法

类属性：类中方法外的变量称为类属性，被该类的所有对象所共享

类方法：使用@classmethod修饰的方法，使用类名直接访问的方法

静态方法：使用@staticmethod修饰的方法，使用类名直接访问的方法

```python
print(Student.a)
Student.game()
Student.run()
```

## 动态绑定属性和方法

python是动态语言，在创建对象之后，可以动态地绑定属性和方法

**绑定属性**

```python
class student:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def eat(self):
        print(self.name + '在吃饭')
st1=student('张三',20)
st2=student('李四',30)
st2.gender='男'
print(st2.name,st2.age,st2.gender)
print(st1.name,st1.age)
```

**绑定方法**

```python
class student:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def eat(self):
        print(self.name + '在吃饭')
st1=student('张三',20)
st2=student('李四',30)
def show():
    print('1111')
st2.show=show
st2.show()
```

## 面对对象的三大特征

### 封装

提高程序的安全性。

​	将数据(属性)和行为(方法)包装到类对象中。在方法内部对属性进行类对象的外部调用方法。这样，无需关心方法内部的具体实现细节，从而减少复杂度。

​	在python中没有专门的修饰符用于属性的私有，如果该属性不希望在类对象中访问，前面使用两个“_”。

```python
class student:
    def __init__(self,name,age):
        self.name=name
        self.__age=age#封装，年龄不希望在类的外部被使用。

    def show(self):
        print(self.name,self.__age)
st1=student('张三',20)
st1.show()#张三 20

print(st1.name)#张三
print(st1.__age)#error
print(st1._student__age)#20，在类的外部可以用 _类名__类属性 来访问被封装的类属性
```

### 继承

提高代码的复用性

​	语法格式	class 子类类名 （父类1，父类2...）:

​								pass

如果一个类没有继承任何类，则默认继承object。

python支持多继承。

定义子类时，必须在其构造函数中调用父类的构造函数。

```python
class person():
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def info(self):
        print(self.name,self.age)

class student(person):
    def __init__(self,name,age,temp):
        super().__init__(name,age)
        self.temp=temp

stu=student('张三',12,3287)
stu.info()#张三 12
```

多继承同上类似。

------

#### 方法重写

父类的方法不能满足子类的需求时，可以在子类中重写方法。

重写方法与父类中的方法同名，可以继承（或者不继承）父类的方法，再写子类需要的操作。

```python
class person():
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def info(self):
        print(self.name,self.age)

class student(person):
    def __init__(self,name,age,temp):
        super().__init__(name,age)
        self.temp=temp
    def info(self):
        super().info()#继承父类原有info
        print(self.temp)#为子类的新info添加独有功能

stu=student('张三',12,3287)#张三 12 3287
stu.info()
```

------

#### object类

​	object类是所有类的父类，因此所有类都有object类的属性和方法。

​	内置函数dir()可以查看指定对象所有属性。

​	object类有一个__ str __()方法，用于返回一个对于“对象的描述”，对应于内置函数str()经常用于print()方法，帮我们查看对象的信息，所以我们经常会对str(简称)进行重写。

```python
class person():
    def __init__(self,name,age):
        self.name=name
        self.age=age

stu=person('张三',20)
print(stu)#<__main__.person object at 0x0000028D5A1D0810>

```

```python
class person():
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def __str__(self):
        return '我叫{0},今年{1}岁'.format(self.name,self.age)
stu=('张三',20)
print(stu)#名字是张三,年龄是20
```

```python
class person():
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def __str__(self):
        return '1'
stu=person('张三',20)
print(stu)#1
```

------

### 多态

简单地说，多态就是“具有多种形态”，它指的是：即便不知道一个变量所引用的对象到底是什么类型，仍然可以通过这个变量调用方法，在运行过程中根据变量所引用对象的类型，动态决定调用哪个对象中的方法。

```python
class animal(object):
    def eat(self):
        print('动物')

class dog(animal):
    def eat(self):
        print('狗')

class cat(animal):
    def eat(self):
        print('猫')

class person:
    def eat(self):
        print('人')

def fun(obj):
    obj.eat()

fun(animal())#动物
fun(dog())#狗
fun(cat())#猫
fun(person())#人
```

不管eat是谁的方法，只要类中有，都能在同一函数中调用。

------

python是动态语言

而静态语言实现多态的三个必要条件

- 继承
- 方法重写
- 父类引用指向子类对象

可以看到person没有继承animal类，也没有重写方法，也没有在animal类中引用指向person类，所以这就是python的多态属性。

------

## 特殊方法和特殊属性

|          | 名称         | 描述                                                   |
| -------- | ------------ | ------------------------------------------------------ |
| 特殊属性 | __ dict __   | 获得类对象或实例对象所绑定的所有属性和方法的字典       |
| 特殊方法 | __ len __()  | 通过重写len方法，让内置函数len()的参数可以是自定义类型 |
|          | __ add __()  | 通过重写add方法，可使用自定义对象具有"+"功能           |
|          | __ new __()  | 用于创建对象                                           |
|          | __ init __() | 对创建的对象进行初始化                                 |

**__ dict __**

```python
class person:
    def __init__(self,name,age):
        self.name=name
        self.age=age
p1=person('张三',20)
print(p1.__dict__)#{'name': '张三', 'age': 20}
print(person.__dict__)#{'__module__': '__main__', '__init__': <function person.__init__ at 0x00000213DA2D93A0>, '__dict__': <attribute '__dict__' of 'person' objects>, '__weakref__': <attribute '__weakref__' of 'person' objects>, '__doc__': None}
```

------

**__ add __**

```python
a=20
b=30
c=a.__add__(b)
#等效c=a+b
print(c)
```

```python
class person:
    def __init__(self,name):
        self.name=name
    def __add__(self,other):
        return self.name+other.name
p1=person('张三')
p2=person('李四')
p3=p1+p2#不在person内重定义add就会报错，p1.__add__(p2)也会报错。
print(p3)#张三李四
```

------

**__ len __**

```python
str1='name'
st=str1.__len__()
print(st)#4
```

```python
class person:
    def __init__(self,name):
        self.name=name
    def __len__(self):
        return len(self.name)
p1=person('jack')
len=p1.__len__()#或者len=len(p1),也要在person内重定义
print(len)#4
```

------

**__ new __ 和 __ init __**

```python
class person:
    def __new__(cls, *args, **kwargs):
        obj=super().__new__(cls)
        return obj
    def __init__(self,name):
        self.name=name
p1=person('jack')
```

先执行person('jack')，传递参数给person类中new中的cls，然后传参给obj中的cls，return obj传参给init方法中的self，self再传给p1.

------

## 类的赋值，浅拷贝与深拷贝

​	**变量的赋值操作**

​		只是形成两个变量，实际上还是指向同一个对象。

​	**浅拷贝**

​		python拷贝一般都是浅拷贝，拷贝时，对象包含的子对象内容不拷贝，因此，源对象与拷贝对象会引用同一个子对象。

​	**深拷贝**

​		使用copy模块的deepcopy函数，递归拷贝对象中包含的子对象，源对象和拷贝对象所有的子对象也不相同。

------



```python
class cpu:
    pass
class disk:
    pass
class computer:
    def __init__(self,cpu,disk):
        self.cpu=cpu
        self.disk=disk

cpu1=cpu()
cpu2=cpu1
print(cpu1)
print(cpu2)#地址相同，说明一个对象赋给了两个变量。
```

```python
class cpu:
    pass
class disk:
    pass
class computer:
    def __init__(self,cpu,disk):
        self.cpu=cpu
        self.disk=disk

import copy
computer1=computer(cpu,disk)
computer2=copy.copy(computer1)
print(computer1,computer1.cpu,computer1.disk)
print(computer2,computer2.cpu,computer2.disk)#cpu和disk不拷贝，两者引用同一个子对象。
```

浅拷贝只复制指向某个对象的指针，而不复制对象本身，新旧对象还是共享同一块内存。但深拷贝会另外创造一个一模一样的对象，新对象跟原对象不共享内存，修改新对象不会改到原对象。

------

# 19.模块

​	**函数与模块（Modules）的关系**

​			一个模块中可以包含N多个函数

​	**在python中一个扩展名为.py的文件就是一个模块**

​	**使用模块的好处**

​			方便其它程序和脚本的导入并使用

​			避免函数名和变量名冲突

​			提高代码的可维护性

​			提高代码的可重用性

------

## 自定义模块

​		**创建模块**

​				新建一个.py文件，名称尽量不要与python自带的标准模块名称相同。

​		**导入模块**

​				import	模块名称	[as 别名]                    （导入模块所有功能）

​				from	模块名称	import	函数/变量/类   （导入模块中的某一功能）

**可导入自定义模块**，在文件夹右键中找到make dictionary as。

------

## 以主程序形式运行

​	在每个模块的定义中都包括一个记录模块名称的变量__ name __ ，程序可以检查该变量，已确定他们在哪个模块中执行。如果一个模块不是被导入到其他程序中执行，那么它可能在解释器的顶级模块中执行。顶级模块的__ name __ 变量的值为 __ main__.

# 20.包

​		包是一个分层次的目录结构，它将一组功能相近的模块组织在一个目录下。

​		作用：代码规范；避免模块名称冲突

------

**包与目录的区别**

​		包含__ init __.py文件的目录称为包

​		目录里通常不包含__ init __.py文件

------

**包的导入**

​		import	包名.模块名

使用import方式进行导入时，只能跟包名或者模块名。

使用from...import可以导入包，模块，函数，变量。

------

# 21.常用的内置模块

sys，time，os，calendar，urllib，json，re，math，decimal，logging

# 22.文件的读写操作

内置函数**open()**创建文件对象

语法规则：**file	=	open(	'filename'	,	[mode,encoding])**

```python
file=open('a.txt','r')
```

------

## 常用的文件打开模式

| 打开模式 |                             描述                             |
| :------: | :----------------------------------------------------------: |
|    r     |       以只读模式打开文件，文件的指针将会放在文件的开头       |
|    w     | 以只写模式打开文件，如果文件不存在则创建，如果文件存在，则覆盖原有内容，文件指针在文件的开头 |
|    a     | 以追加模式打开文件，如果文件不存在则创建，文件指针在文件开头，如果文件存在，则在文件末尾追加内容，文件指针在文件末尾 |
|    b     | 以二进制方式打开文件，不能单独使用，需要与其他模式一起使用，rb，或者wb |
|    +     | 以读写方式打开文件，不能单独使用，需要与其他模式一起使用，a+ |

**文件的类型**

按文件中数据的组织形式，文件分为以下两大类

- 文本文件：存储的是普通“字符”文本，默认为Unicode字符集，可以使用记事本程序打开
- 二进制文件：把数据内容用“字节”进行存储，无法用记事本打开，必须使用专用的软件打开，举例：MP3音频文件，JPG图片，.doc文档等

------

## 文件对象的常用方法

|        方法名         |                             说明                             |
| :-------------------: | :----------------------------------------------------------: |
|     read([size])      | 从文件中读取size个字节或字符的内容返回。若省略[size]，则读取到文件末尾，即一次读取文件所有内容 |
|      readline()       |                   从文本文件中读取一行内容                   |
|      readlines()      | 把文本文件中每一行都作为独立的字符串对象，并将这些对象放入列表返回 |
|      write(str)       |                   将字符串str内容写入文件                    |
|  writelines(s_list)   |         将字符串列表s_list写入文本文件，不添加换行符         |
| seek(offset[,whence]) | 把文件指针移动到新的文职，offset表示相对于whence的位置。<br />offset:为正往结束方向移动，为负往开始方向移动。<br />whence不同的值代表不同含义：<br />0:从文件头开始计算(默认值)。<br />1：从当前位置开始计算。<br />2：从文件尾开始计算 |
|        tell()         |                    返回文件指针的当前位置                    |
|        flush()        |             把缓冲区的内容写入文件，但不关闭文件             |
|        close()        |  把缓冲区的内容写入文件，同时关闭文件，释放文件对象相关资源  |

------

## with语句

​	with语句(上下文管理器)可以自动管理上下文资源，不论什么原因跳出with块，都能确保文件正确的关闭，以此来达到释放资源的目的。

```python
with open('a.txt','r') as file:
	print(file.read())
```

[(7条消息) Python 中 with用法及原理_python with语句_cltdevelop的博客-CSDN博客](https://blog.csdn.net/u012609509/article/details/72911564?ops_request_misc=%7B%22request%5Fid%22%3A%22168509983216800227455910%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=168509983216800227455910&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-72911564-null-null.142^v88^koosearch_v1,239^v2^insert_chatgpt&utm_term=with&spm=1018.2226.3001.4187)