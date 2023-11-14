# 1.基本概念

## 注释

单行注释，多行注释和c一样，还有文档注释。

## 关键字

被java赋予了特定含义的英文单词

- 关键字的字母全部小写

- 常用的代码编辑器，针对关键字有特殊的颜色标记。

  ------

  **class**

  用于（创建/定义）一个类，类是java最基本的组成单元。

## 字面量

​		告诉程序员：数据在程序中的书写格式。

**类型**：

- 整数类型
- 小数类型
- 字符串类型
- 字符类型
- 布尔类型
  - 空类型 null

```java
public class Helloworld
{
  public static void main(String[] args)
  {
​    System.out.println(111);
​    System.out.println(-1.3);
​    System.out.println('a');
​    System.out.println("aaa");
​    System.out.println(true);
​    System.out.println(false);
​    System.out.println("null");//null不能直接被打印，只能以字符串的形式打印。
  }
}
```

```java
public class Helloworld
{
  public static void main(String[] args)
  {
​    System.out.println("name"+"age");//字符串拼接
     System.out.println("name"+'\t'+"age");
  }
}
```

# 2.数据类型

byte  -128~127

short int long float double char

**boolean**

**long类型变量：需要加入L标识（大小写都可以）**

**float类型变量：需要加入F标识（大小写都可以）**

```java
long num1 =123L;

float num2= 12.3F;
```

​	也可以**String name="   "**

# 3.标识符

命名规则：由数字、字母、下划线和美元符组成

​					不能以数字开头，不能是关键字，区分大小写。

```java
import java.util.Scanner;//导包，找到Scanner类（键盘输入）
public class Helloworld
{
  public static void main(String[] args)
  {
​    Scanner sc = new Scanner(System.in);//创建对象，表示我现在准备使用Scanner这个类.sc是变量名 可以改
​    int i=sc.nextInt();//i是变量名 可以改，这一句相当于scanf
​    System.out.println(i);
​    sc.close();//使用sc这个Scanner对象后要关闭 不然会增加耗费的内存
  }
}
```

# 4.运算

**隐式转换**（取值范围小的转化为取值范围大的）

int a=10

double b=a

那么b=10.0。

若加上c=a+b

那么先提升a的值，再与b相加，所以c也为double。

**取值范围小的，和取值范围大的进行运算，小的会提升为大的，再进行运算**

**byte	short	char三种类型的数据在运算的时候（不管取值范围是否相同），都会直接先提升为int，然后再进行运算。**

**取值范围**：byte<short<int<long<float<double

------

**强制转换**

```java
double b=12.3

int a=(int)b;
```

------

**字符串拼接**

```java
public class demo
{
    public static void main(String[] args)
    {
        System.out.println(1+2+"name"+2+1);//3name21
    }
}
```

从左到右运算，1+2=3，3再与name拼接，3name再和2和1拼接。

------

## 逻辑运算符

^ 逻辑异或 	相同为false，不同为true

！逻辑非  	取反

------

## 短路逻辑运算符

&&和||

**用户名正确 & 密码正确**

不管用户名是否正确，都会判断密码是否正确

**用户名正确 && 密码正确**

先判断用户名是否正确，如果是false，则不会执行判断密码是否正确

||同理。

都是先判断左边是否为true，再判断是否***执行*右边这条语句**

------

三元运算符

和c一样

# 5.switch

```java
import java.util.Scanner;
public class demo
{
    public static void main(String[] args)
    {
        Scanner sc=new Scanner(System.*in*);
        int week=sc.nextInt();
        switch (week)
        {
            case 1,2,3,4,5:
                System.*out*.println("工作日");
                break;
            case 6,7:
                System.*out*.println("周末");
                break;
            default:
                System.*out*.println("输入错误");
        }
    }
}
```

可以简化为如下代码。

```java
import java.util.Scanner;
public class demo
{
    public static void main(String[] args)
    {
        Scanner sc=new Scanner(System.*in*);
        int week=sc.nextInt();
        switch (week)
        {
            case 1,2,3,4,5-> System.*out*.println("工作日");
            case 6,7-> System.*out*.println("周末");
            default-> System.*out*.println("输入错误");
        }
    }
}
```

## case穿透

**case穿透**：在switch语句中，如果case控制的语句体后面不写break，将出现穿透现象，在不判断下一个case值的情况下，向下运行，直到遇到break，或者整体switch语句结束。

# 6.数组

使用数组时，需要结合隐式转换考虑。但还是建议数据和数组类型相同。

​	有两种格式

int [] array

int array []

**数组的静态初始化**

```java
public class demo
{
    public static void main(String[] args)
    {
        int[] array = new int[]{11,22};//完整格式
        int[] array = {11,22};//简化格式
        String[] arr = new String[]{"zhangsan"};
        String[] arr = {"zhangsan"};
    }
}
```

# 7.方法（method）

方法是程序中最小的执行单元，main方法就是主方法。

与c语言中的函数差不多。

```java
public static void 方法名()
{
    方法体（就是打包起来的代码）;
}
```

调用:

​		方法名();

**方法重载**

在同一个类中，定义了多个**同名方法**，这些同名方法具有同种功能。

每个方法具有**不同的参数类型**或**参数个数**，这些同名的方法，就构成了重载关系。

就是**方法名相同，参数不同**的方法，与**返回值**无关。

**参数不同：个数不同，类型不同，顺序不同**。

```java
public class demo
{
    public static void fn(int a)
    {
    }
    public static int fn(int a,int b)
    {
    }
}
```

## 内存原理

**堆栈**

栈：方法运行时使用的内存，方法进栈运行，运行完毕就出栈。

堆：new出来的，都在堆内存中开辟了一个小空间。

```java
public class demo
{
    public static void main(String[] args)
    {
        fn();
    }
    public static void fn(int a)
    {
    }
    public static int fn(int a,int b)
    {
    }
}
```

main先进栈，然后fn进栈，fn出栈，main出栈。

## 引用数据类型

使用其他空间中数据的数据。

```java
public  class demo
{
    public static void main(String[] args)
    {
        int[] arr={1,2,3};
    }
}
```

栈内存中进 main后 int[] arr= 地址

然后根据地址进入堆内存来找值。

## 基本数据类型

数据值是存储在自己的空间中。

**特点**：赋值给其他变量，也是赋的真实的值。

------

**引用数据类型**：数据值是存储在其他空间中，自己空间中存储的是地址值，例如数组。

**特点**：赋值给其他变量，赋的地址值。

# 8.类和对象

```java
public class phone
{
    String brand;
    int price;//属性（成员变量）

​    public void call()//行为（方法）
​    {
​        System.*out*.println("正在打电话");
​    }
​    
​    public void playGame()
​    {
​        System.*out*.println("正在玩游戏");
​    }
}
```

如何得到类的对象

​		**类名	对象名	=	new	类名();**

**demo.java**

```java
public  class demo
{
    public static void main(String[] args)
    {
        phone p=new phone();
        p.brand="小米";
        p.price=4999;
        System.*out*.println(p.brand);
        System.*out*.println(p.price);
        p.call();
        p.playGame();
    }
}
```

小米
4999
正在打电话
正在玩游戏

**phone.java**

```java
public class phone
{
    String brand;
    int price;

​    public void call()
​    {
​        System.*out*.println("正在打电话");
​    }

​    public void playGame()
​    {
​        System.*out*.println("正在玩游戏");
​    }
}
```

注意：

一般不在类里面直接赋值。

## 封装和private关键字和this

```java
public class person
{
    private int age;
    private double height;
    private double weight;

​    public void setAge(int age)
​    {
​        this.age=age;
​    }
​    public int getAge()
​    {
​        //System.*out*.println(age);
​        return age;
​    }
}
```

**private修饰成员**（成员变量和方法）

被修饰的成员只能在本类中访问，这也引出封装的重要。

**封装思想**很重要，比如人关门，人只是使用了**关门**这个**门类**中所包含的关门**方法**。所以关门应该写在**门类**中。

上述代码我把age height weight都封装好了，只能通过**set**，get函数改变和得到age height weight。

而这又涉及到方法和类中变量重名的问题，这个时候用到**this**关键字。

**this关键字**

this的本质：代表方法调用者的地址值。

------



## 构造方法的格式

**构造	**方法

1.空参构造	2.带参构造

特点

- 方法名与类名相同，大小写也要一致
- 没有返回值类型，连void也没有
- 没有具体的返回值(不能由return待会结果数据)

执行时机

- 创建对象的时候由虚拟机调用，不能手动调用构造方法
- 每创建一次对象，就会调用一次构造方法

```java
//person.java
public class person
{
    private int age;
    private String name;
    public person()
    {
        System.*out*.println("执行否？");
    }
    public person(String name,int age)
    {
        this.name=name;
        this.age=age;
    }
}
```

```java
//demo.java
public class demo
{
    public static void main(String[] args)
    {
        person p=new person();//执行否
        person p1=new person("张三",20);
        p.getPerson();//0 null
        p1.getPerson();//20，张三
    }
}
```

这两种情况都有**应用场景**。

空参构造用于先创建对象，再等待用户输入。

带参构造用于直接创建对象时赋值。

**注意事项**

**构造方法的定义**

- 如果没有定义构造方法，系统将给出一个**默认**的**无参数构造方法**
- 如果定义了构造方法，系统将不再提供默认的构造方法

**构造方法的重载**

​		带参构造方法，和无参数构造方法，两者方法名相同，但是参数不同，这叫做构造方法的重载。

**使用方式**

无论是否使用，都手动书写无参数构造方法，和带全部参数的构造方法。

## 标准的JavaBean类

- 类名需要见名知意

- 成员变量使用private修饰

- 提供至少两个构造方法

  - 无参构造方法

  - 带全部参数的构造方法

    

    

    成员方法

  ​		提供每一个成员变量对应的setXxx()/getXxx()

  ​		如果还有其他行为，也需要写上

```java
public class person
{
    private int age;
    private String name;

​    public person() {
​    }

​    public person(int age, String name) {
​        this.age = age;
​        this.name = name;
​    }

​    */**
\*     *** *获取
\*     *** **@return** *age
\*     **/
\*    public int getAge() {
​        return age;
​    }

​    */**
\*     *** *设置
\*     *** **@param** *age
\*     **/
\*    public void setAge(int age) {
​        this.age = age;
​    }

​    */**
\*     *** *获取
\*     *** **@return** *name
\*     **/
\*    public String getName() {
​        return name;
​    }

​    */**
\*     *** *设置
\*     *** **@param** *name
\*     **/
\*    public void setName(String name) {
​        this.name = name;
​    }

​    public String toString() {
​        return "person{age = " + age + ", name = " + name + "}";
​    }
}
```

# 9.字符串

API：应用程序编程接口。

API就是别人已经写好的东西，我们不需要自己编写，直接用就可以。

Java API：指的就是JDK中提供的各种功能的Java类。

------

String是java定义好的一个类。定义在java.lang包中。

String类在创建后是**不可更改**的。

------

## 创建String对象的两种方式

1.直接赋值（大多数使用）

2.new

|            构造方法            |               说明               |
| :----------------------------: | :------------------------------: |
|        public String()         |   创建空白字符串，不含任何内容   |
| public String(String original) | 根据传入的字符串，创建字符串对象 |
|   pubilc String(char[] chs)    |   根据字符数组，创建字符串对象   |
|   public String(byte[] chs)    |   根据字节数组，创建字符串对象   |

网络当中传输的数据其实都是字节信息，一般要把字节信息进行转换，转成字符串，此时就要用到这个字节构造。

## 字符串比较

boolean equals方法(要比较的字符串)					完全一样结果才是true

boolean equalsignoreCase(要比较的字符串)		 忽略大小写的比较

```java
public class demo
{
    public static void main(String[] args)
    {
        String a="abc";
        String b=new String("abC");
        boolean result = a.equalsIgnoreCase(b);//false
        System.*out*.println(a.equals(b));//true
        System.*out*.println(result);
    }
}
```

```java
import java.util.Scanner;
public class demo
{
    public static void main(String[] args)
    {
        Scanner sc=new Scanner(System.*in*);
        String s1=sc.next();//abc  通过看java源码可知，是new出来的。
        String s2="abc";
        System.*out*.println(s1==s2);//false
    }
}
```

**Java中，==是用来比较字符串引用是否是同一字符串的判定，而equals()是用来比较字符串内容是否一致。与C不同！！！**

------

## StringBuilder

StringBuilder可以看成一个容器，创建之后里面的内容是可变的

作用：提高字符串的操作效率

### 构造方法

空参构造和含参构造

|                                  |                                              |
| :------------------------------: | :------------------------------------------: |
|      public StringBuilder()      | 创建一个空白可变字符串对象，不含有任何内容。 |
| public StringBuilder(String str) |   根据字符串的内容，来创建可变字符串对象。   |

### 成员方法

|                方法名                 |                        说明                         |
| :-----------------------------------: | :-------------------------------------------------: |
| public StringBuilder append(任意类型) |              添加数据，并返回对象本身               |
|    public StringBuilder reverse()     |                  反转容器中的内容                   |
|          public int length()          |              返回长度(字符出现的个数)               |
|       public String toString()        | 通过toString()就可以实现把StringBuilder转换为String |

```java
public class demo
{
    public static void main(String[] args)
    {
        StringBuilder sb=new StringBuilder();
        System.*out*.println(sb);//(无)
    }
}
```

因为StringBuilder是Java已经写好的类

java在底层对他做了一些特殊处理

打印对象不是地址值而是属性值

```java
public class demo
{
    public static void main(String[] args)
    {
        StringBuilder sb=new StringBuilder("abc");
        System.*out*.println(sb);//abc
    }
}
```

```java
public class demo
{
    public static void main(String[] args)
    {
        StringBuilder sb=new StringBuilder("abc");
        System.*out*.println(sb);//abc
        sb.append(123);
        System.*out*.println(sb);//123
        sb.reverse();
        System.out.println(sb);//321cba
        System.out.println(sb.length());//6
    }
}
```

**链式编程**

调用一个方法的时候，不需要用变量接收他的结果，可以继续调用其他方法

```java
import java.util.Scanner;
public class demo
{
    public static void main(String[] args)
    {
        int length=*getString*().length();//链式编程
        System.*out*.println(length);
    }
    public static String getString()
    {
            Scanner sc=new Scanner(System.*in*);
            System.*out*.println("请输入一个字符串");
            String str=sc.next();
            return str;
    }
}
```

## StringJoiner

也可以看成一个容器，创建之后里面的内容是可变的。

作用：提高字符串的操作效率，而且代码编写特别简洁。

### 构造方法

|                      方法名                       |                             说明                             |
| :-----------------------------------------------: | :----------------------------------------------------------: |
|          public StringJoiner (间隔符号)           |        创建一个StringJoiner对象，指定拼接时的间隔符号        |
| public StringJoiner(间隔符号，开始符号，结束符号) | 创建一个StringJoiner对象，指定拼接时的间隔符号，开始符号，结束符号 |

### 成员方法

|                方法名                |                                            |
| :----------------------------------: | :----------------------------------------: |
| public StringJoiner add (添加的内容) |          添加数据，并返回对象本身          |
|         public int length()          |          返回长度(字符出现的个数)          |
|       public String toString()       | 返回一个字符串(该字符串就是拼接之后的结果) |

```java
import java.util.StringJoiner;

public class demo
{
    public static void main(String[] args)
    {
        StringJoiner sj=new StringJoiner("--");
        StringJoiner sj1=new StringJoiner("--","[","]");
        sj.add("aaa").add("bbbb").add("cc");
        System.*out*.println(sj);//aaa--bbbb--cc
        sj1.add("aaa").add("bbbb").add("cc");
        System.*out*.println(sj1);//[aaa--bbbb--cc]
    }
}
```

结论：如果很多字符串变量拼接，不要直接+。在底层会创建多个对象，浪费时间，浪费性能。

# 10.集合

集合可以自动扩容。

数组可以存基础数据类型和引用数据类型

但集合只能存引用数据类型，如果要存基础数据类型需要先对其使用包装类。

集合也有很多类，**ArrayList**是用的最多的。

| 方法名               | 说明                                 |
| -------------------- | ------------------------------------ |
| boolean add(E e)     | 添加元素 ，返回值表示是否添加成功    |
| boolean remove(E e)  | 删除指定元素，返回值表示是否删除成功 |
| E remove(int index)  | 删除指定索引的元素，返回被删除元素   |
| E set(int index,E e) | 修改指定索引下的元素，返回原来的元素 |
| E get(int index)     | 获取指定索引的元素                   |
| int size()           | 集合的长度，也就是集合中元素的个数   |

```java
import java.util.ArrayList;

public class demo
{
    public static void main(String[] args)
    {
        ArrayList<String>list=new ArrayList<>();
        System.*out*.println(list);//[]
        list.add("aaa");
        list.add("bbb");
        list.add("ccc");
        System.*out*.println(list);//[aaa, bbb, ccc]
        list.remove("aaa");
        System.*out*.println(list);//[bbb, ccc]
        list.remove(0);
        System.*out*.println(list);//[ccc]
        list.set(0,"111");
        System.*out*.println(list);//[111]
        String result =list.get(0);
        System.*out*.println(result);//111
        int length= list.size();
        System.*out*.println(length);//1
    }
}
```

ArrayList是java已经写好的类，打印对象不是地址值，而是集合中存储数据内容。在展示的到时候会拿[]把所有的数据进行包裹。

# 11.static静态

java中的一个修饰符，可以修饰成员方法，成员变量。

## 静态变量

特点：被该类所有对象共享

调用方式：**类名调用**，对象名调用

```java
//student.java
public class student
{
    private String name;
    private int age;
    public String teacherName;
    
    public student() {
    }
    public student(String name, int age) {
        this.name = name;
        this.age = age;

​    }

​    public String getName() {
​        return name;
​    }

​    public void setName(String name) {
​        this.name = name;
​    }
​    
​    public int getAge() {
​        return age;
​    }

​    public void setAge(int age) {
​        this.age = age;
​    }

​    public void study()
​    {
​        System.*out*.println(name+"正在学习");
​    }

​    public void show()
​    {
​        System.*out*.println(name+","+age+","+teacherName);
​    }
}
```

```java
//demo.java
public class demo
{
    public static void main(String[] args)
    {
        student p1=new student("张三",20);
        p1.teacherName="王老师";
        p1.study();//张三正在学习
        p1.show();//张三,20,王老师
        student p2=new student("李四",21);
        p2.study();//李四正在学习
        p2.show();//李四,21,null
    }
}
```

所有学生共享一个老师，用static不用多次使用学生对象给老师名字赋值。

```java
public class demo
{
    public static void main(String[] args)
    {
        student.*teacherName*="王老师";//student.java里
        //变成了 public static void teacherName
        student p1=new student("张三",20);
        p1.study();
        p1.show();
        student p2=new student("李四",21);
        p2.study();
        p2.show();
    }
}
```

静态对象随着类的加载而加载，优于对象出现。

且不属于对象，属于类。

## 静态方法

多用在**测试类**和**工具类**中

Javabean类中很少会用

调用方法：**类名调用**，对象名调用

**注意事项**：

- 静态方法中，只能访问静态
- 非静态方法可以访问所有
- 静态方法中没有this关键字

# 12.继承

extends

public class Student **extends** Person{}

Student称为**子类**，Person称为**父类**

**java只支持单继承，但可以多层继承。**

```java
//animal.java
public class animal
{
    
    public void drink()
    {
        System.*out*.println("drink");
    }
    public void eat()
    {
        System.*out*.println("吃东西");
    }
}
```

```java
//cat.java
public class cat extends animal
{
        public void show()
        {
            System.*out*.println("猫在抓老鼠");
        }
}
```

```java
//demo.java
public class demo
{
    public static void main(String[] args) {
        cat c1 = new cat();
        c1.drink();//drink
    }
}
```

## 重写和隐藏父类方法

### 重写父类方法

当一个子类中一个实例方法具有与其父类中的一个实例方法相同的签名（指名称、参数个数和类型）和返回值时，称子类中的方法“重写”了父类的方法。

和python一样

**注意**：重写的方法具有与其所重写的方法相同的名称、参数数量、类型和返回值。

### 隐藏父类方法

如果一个子类定义了一个**静态类**方法，而这个类方法与其父类的一个类方法具有相同的签名（指名称、参数格式和类型）和返回值，则称在子类中的这个类方法“隐藏”了父类中的该类方法。

- 当调用被重写的方法时，调用的版本是子类的方法；
- 当调用被隐藏的方法时，调用的版本取决于是从父类中调用还是从子类中调用。

**方法重写和隐藏后的修饰符**

在子类中被重写的方法，其访问权限允许大于但不允许小于被其重写的方法，例如：父类中一个受保护的**实例方法(protected)**在子类中可以是**公共的(public)**的，但不可以是**私有的(private)**。如果一个方法在父类中是static方法，那么在子类也必须是static方法；如果一个方法在父类中是实例方法，那么在子类中也必须是实例方法。

**子类访问父类私有成员**

子类继承其父类的所有public和protected成员，但不能继承其父类的private成员。那么如何在子类中访问到父类中的字段呢，我们可以在父类中提供用来访问其私有字段的public或protected方法，子类使用这些方法来访问相应的字段。

### **super关键字**

**使用super调用父类中重写的方法、访问父类中被隐藏的字段**

子类重写了父类中的某一个方法，隐藏父类中的字段，假如想在子类中访问到父类中被重写的方法和隐藏父类的字段，可以在子类中通过使用关键字super来调用父类中被重写的方法和访问父类中被隐藏的字段。

```java
//A.java
public class A
{
    public String name="张三";
    public void say()
    {
        System.*out*.println("我是类A的方法say");
    }
}
```

```java
//B.java
public class B extends A
{
    public String name="李四";
    public void say()
    {
        super.say();
        System.*out*.println("我是类B的方法say");
        System.*out*.println("父类的名字"+super.name);
    }
}
```

```java
//demo.java
public class demo
{
    public static void main(String[] args) {
        B c1 = new B();
        c1.say();
        System.*out*.println("子类的名字"+c1.name);
    }
}
```

我是类A的方法say
我是类B的方法say
父类的名字张三
子类的名字李四

**使用super调用父类的无参数构造方法/有参数构造方法**

子类不继承其父类的构造方法。

- 当使用无参数的super()时，父类的无参数构造方法就会被调用；
- 当使用带有参数的super()方法时，父类的有参数构造方法就会被调用。

**注意**

- 如果要初始化父类中的字段，可以在子类的构造方法中通过关键字super调用父类的构造方法；
- 对父类的构造方法的调用必须放在子类构造方法的第一行；
  如果父类构造器没有参数，则在子类的构造器中不需要使用 super 关键字调用父类构造器，系统会自动调用父类的无参构造器；
- 如果父类的构造器带有参数，则必须在子类的构造器中显式地通过 super 关键字调用父类的构造器并配以适当的参数列表；
- 子类是不继承父类的构造器（构造方法或者构造函数）的，它只是调用（隐式或显式）。
  

# 13.多态

指同一个实体同时具有多种形式，即同一个对象，在不同时刻，代表的对象不一样，指的是对象的多种形态。

##  特点

1. 多态的前提1：是继承和实现关系
2. 多态的前提2：要有方法的重写
3. 父类引用指向子类对象，如：Animal a = new Cat();



```java
//person.java
public class person
{
    private String name;
    private int age;

​    public person() {
​    }

​    public person(String name, int age) {
​        this.name = name;
​        this.age = age;
​    }

​    public String getName() {
​        return name;
​    }
​    
​    public void setName(String name) {
​        this.name = name;
​    }

​    public int getAge() {
​        return age;
​    }
​    
​    public void setAge(int age) {
​        this.age = age;
​    }

​    public void show()
​    {
​        System.*out*.println(name+age);
​    }
}
```

```java
//student.java
public class student extends person
{
    public void show()
    {
        System.*out*.println("学生的信息为"+getName()+","+getAge());
    }
}
```

```java
//teacher.java
public class teacher extends person
{
    public void show()
    {
        System.*out*.println("学生的信息为:"+getName()+","+getAge());
    }
}
```

```java
//demo.java
public class demo
{
    public static void main(String[] args) {
        student s=new student();
        teacher t=new teacher();
        s.setName("张三");
        s.setAge(18);
        t.setName("李四");
        t.setAge(20);

​        *register*(s);
​        *register*(t);
​    }

​    public static void register(person p)
​    {
​        p.show();
​    }
}
```

## 多态中调用成员的特点

- 变量调用：编译看左边，运行也看左边。
- 方法调用：编译看左边，运行看右边。

# 14.包

命名规则：公司域名反写+作用，全部小写。

- 使用同一个包中的类时，不需要导包
- 使用java.lang包中的类时，不需要导包
- 其他情况都需要导包
- 如果同时使用两个包中的同名类，需要用全类名

# 15.final关键字

可修饰 **方法 类 变量**

表明该方法是最终方法，不能被重写

表明该类是最终类，不能被继承

表明该变量叫做常量，只能被赋值一次

**常量**

命名规范：

​				单个单词：全部大写

​				多个单词：全部大写，单词之间用下划线隔开

细节：final修饰的变量是基本类型：那么变量存储的数据值不能发生改变。

final修饰的变量是引用类型：那么变量存储的地址值不能发生改变，对象内部的可以改变。

# 16.权限修饰符

用来控制一个成员能够被访问的范围

可以修饰成员变量，方法，构造方法，内部类

有四种作用范围由小到大：**private<空着不写<protected<public**

|  修饰符   | 同一个类中 | 同一个包中其他类 | 不同包下的子类 | 不同包下的无关类 |
| :-------: | :--------: | :--------------: | :------------: | :--------------: |
|  private  |     可     |                  |                |                  |
| 空着不写  |     可     |        可        |                |                  |
| protected |     可     |        可        |       可       |                  |
|  public   |     可     |        可        |       可       |        可        |

# 17.代码块

局部代码块，构造代码块，**静态代码块**

静态代码块：static{}，随着类的加载而加载，并且自动触发、**只执行一次**，用于**数据初始化**

```java
public class demo
{
    static
    {
        ArrayList<demo>list = new ArrayList<>();
    }
    public static void main(String[] args)
    {

​    }
}
```

如果在main中初始化数据，那么其他类在调用此类时，对象会被重复创建，所以用静态代码块最好。

# 18.抽象类和抽象方法

抽象方法的定义格式：public abstract 返回值类型 方法名（参数列表）;

抽象类的定义格式：public abstract class 类名{};

详细代码见**idea abstract1**

```java
public abstract class animal
{
    private int age;
    private String name;

​    public animal() {
​    }

​    public void drink()
​    {
​        System.*out*.println(name+"喝水");
​    }



​    public animal(int age, String name) {
​        this.age = age;
​        this.name = name;
​    }

​    */**
\*     *** *获取
\*     *** **@return** *age
\*     **/
\*    public int getAge() {
​        return age;
​    }

​    */**
\*     *** *设置
\*     *** **@param** *age
\*     **/
\*    public void setAge(int age) {
​        this.age = age;
​    }

​    */**
\*     *** *获取
\*     *** **@return** *name
\*     **/
\*    public String getName() {
​        return name;
​    }

​    */**
\*     *** *设置
\*     *** **@param** *name
\*     **/
\*    public void setName(String name) {
​        this.name = name;
​    }

​    public abstract void eat();
}
```

```java
public class dog extends animal {
    public dog() {
    }

​    public dog(int age,String name)
​    {
​        super(age,name);
​    }
​    public void eat()
​    {
​        System.*out*.println(getName()+"吃骨头");
​    }
}
```

```java
public class frog extends animal
{
    public frog() {
    }

​    public frog(int age,String name)
​    {
​        super(age, name);
​    }

​    @Override
​    public void eat() {
​        System.*out*.println(getName() +"吃虫子");
​    }
}
```

```java
public class sheep extends animal {

​    public sheep() {
​    }

​    public sheep(int age,String name)
​    {
​        super(age, name);
​    }
​    public void eat()
​    {
​        System.*out*.println(getName()+"吃草");
​    }
}
```

```java
public class test
{
    public static void main(String[] args)
    {
        sheep s=new sheep(5,"小羊");
        System.*out*.println(s.getName()+","+s.getAge());
        s.eat();
        s.drink();
        //小羊,5
		//小羊吃草
		//小羊喝水
    }
}
```

- 抽象类不能实例化

- 抽象类中不一定有抽象方法，有抽象方法的类一定是抽象类

- 可以有构造方法

- 抽象类的子类

  ​		要么重写抽象类中的所有抽象方法（常用）

  ​		要么是抽象类

**意义**

强制子类**必须按照**抽象类格式重写

这样可以让别人在调用父类的被子类重写一种方法时，不用去子类看这个方法怎样写的（特别是多个子类的情况下），可以直接看父类的抽象方法来使用这个方法

# 19.接口

- 接口用关键字interface来定义

  ​	public interface 接口名{}

- 接口不能实例化

- 接口和类之间是实现关系，通关implements关键字表示

  ​	public class 类名 implements 接口名{}

- 接口的子类（实现类）

  ​	要么重写接口中的所有抽象方法

  ​	要么是抽象类

**注意**：接口和类的实现关系，可以单实现，也可以多实现。

​			实现类还可以在继承一个类的同时实现多个接口。

## 接口中成员的特点

- 成员变量

  ​			只能是常量

  ​			默认修饰符：public static final

- 构造方法

  ​			没有

- 成员方法

  ​			只能是抽象方法

  ​			默认修饰符：public abstract

  ​			（JDK8后可以定义方法）

**接口与接口之间的关系**

继承关系，可以单继承也可以多继承。（这一点和类不同）

## 接口新增方法

### 默认方法

​		允许在接口中定义默认方法，需要用到关键字default修饰。

​		**作用：**解决接口升级的问题（接口加新规则时，避免新规则在实现类中报错）

接口中**默认方法**的定义格式：

​		格式：public default 返回值类型 方法名（参数列表）{}

​		范例：public default void show(){}

接口中默认方法的**注意事项**：

​		默认方法不是抽象方法，所以不强制被重写。但是如果被重写，重写的时候去掉default关键字

​		public可以省略，default不能省略

​		如果实现了多个接口，多个接口中存在相同名字的默认方法，子类就必须对该方法进行重写

### 静态方法

​		允许在接口中定义静态方法，需要用static修饰

接口中**静态方法**的定义格式：

​		格式：public static 返回值类型 方法名（参数列表）{}

​		范例：public static void show(){}

接口中静态方法的**注意事项**：

​		静态方法只能通过接口名调用，不能通过实现类名或者对象名调用

​		public可以省略，static不能省略

### 私有方法

​		接口中私有方法的定义格式：

格式1：private 返回值类型 方法名（参数列表）{}

范例1：private void show(){}

格式2：private static 返回值类型 方法名（参数列表）{}

范例2：private static void method(){}

私有方法给默认方法和静态方法服务。目的是不被外界访问

------

当一个方法的参数是接口时，可以传递接口所有实现类的对象，这种方式称之为**接口多态**。

```java
public interface 运输 {
    public abstract void transfer();
}
```

```java
public class interA{
    public void a(运输 c)
    {
//形成了一个接口类型 j=new 实现类对象();   也遵循编译看左边，运行看右边
​    }//此例中所有满足运输接口的实现类对象都可以传递，称之为接口多态
}
```

------

**适配器设计模式**

设计模式：简单理解下，设计模式就是各种解决问题的套路。

适配器设计模式：解决接口与接口实现类之间的矛盾问题

​		当一个接口中抽象方法过多，但是我只要使用其中一部分的时候，就可以使用适配器设计模式。

​		书写步骤：编写中间类XXXAdapter，实现对应的接口。

# 20.类

## 内部类

在一个类的里面，再定义一个类。

内部类表示的事物是外部类的一部分，内部类单独出现**没有意义**。

**内部类的访问特点**

​		内部类可以直接访问外部类的成员，包括私有。

​		外部类想要访问内部类的成员，必须创建对象。

```java
public class car {
    String carName;
    int carAge;
    String carColor;
    public void show(car this) {//car this指本类自己的对象
        System.*out*.println(carName);//括号里省略了this，原型是this.carName
        engine e = new engine();
        e.engineAge=5;
        System.*out*.println(e.engineAge);
    }
    public class engine{
        String engineName;
        int engineAge;
        public void show()
        {
            System.*out*.println(carName);
            System.*out*.println(engineAge);
        }
    }
}
```

### 成员内部类

写在成员位置的，属于外部类的成员。上面的engine类就属于此类。

成员内部类可以被一些修饰符所修饰，比如：private，默认，protected，public，static等。

JDK16后可以在**成员内部类中定义静态变量**。

#### 获取成员内部类对象

方式一：在外部类中编写方法，对外提供内部类的对象。

方式二：直接创建格式：外部类名.内部类名 对象名 = 外部类对象.内部类对象;