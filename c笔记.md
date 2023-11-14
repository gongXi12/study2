# 1.基本语法的含义

```c
#include<stdio.h>
//stdio拆分来就是 standard 标准input输入out输出  h指head 头文件 stdio.h。include是预命令。
//这个文件可能会包含一个标准输入输出的头文件
int main(void)
{
	/* 我的第一个C程序 */
	printf("Hello,World!\n");
	//print 打印 f format 格式化
	//printf 格式化输出
	return 0;
}
```

# 2.char ch的作用

```c
#include<stdio.h>
int main(void)
{
	char ch = 'a';//存储a
	//char-字符类型 像abc。。。 //ch是 向内存申请空间的变量【可以理解为指令】

return 0;

}
```

# 3.%c与\n的含义

```c
#include<stdio.h>
int main(void)
{
	printf("%c\n,ch");  //%c--打印字符格式的数据【指令】\n表示换行  整个意思是 我以字符的形式来打印ch
	return 0;
}
```

# 4.printf() 

printf()函数的格式:

printf(格式字符串，待打印项1，待打印项2....);

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h> 
int main()
{
	printf("qwer");
		return 0;
}

```

双引号内就是格式字符串。

待打印项可以是常量，变量，甚至是在打印之前先要计算的表达式。

# 5.理解变量

```c
#include<stdio.h>
int main(void)
{
	float a = 2.0;//像float int 等等后面是变量 不仅是a 等等
	printf("%f\n", a);
	return 0;
}
```

# 6.全局变量与局部变量

```c
int num1 = 20;//全局变量，定义在代码块{}外的变量
#include<stdio.h>
int main(void)
{
	int num2 = 10;//局部变量，定义在代码块{}内的变量  
	return 0;
}
```

# 7.计算两个数的和

```c
#include<stdio.h>
int main(void)
{
	int num1 = 10;
	int num2 = 20;
	int sum = 0;//c语言语法规定，变量要定义在当前代码块的最前面 不然会报错
	scanf("%d%d", &num1, &num2);//scanf是输入函数，输入数据时使用.scanf是C语言标准。但新版vs要用scanf_s
	sum = num1 + num2;
	printf("sum = %d\n", sum);
	return 0;
}
```

# 8.变量的作用域与生命周期

```c
#include<stdio.h>
int main(void)
{
	{
		int num = 10;
	}//这里面的括号才是num的作用域
	printf("%d\n", num);//这里会出现报错是因为printf所在位置不是num的作用域【就是可以发挥作用的区域】
	return 0;
}//生命周期 局部变量 进入作用域 开始 出作用域结束 
 //全局变量 整个程序的生命周期
```

# 9.声明符号 extern

```c
#include<stdio.h>
int main(void)
{
	extern int wwf;//声明符号。若我创建了另一个c文件 在其中定义  例  int wwf = 10
	//那么在此文件中我需要输入 extern int wwf;来声明 int wwf这个外部符号【即不在本c文件内的符号】
	printf("%d\n", wwf);
    //只有这样才能打印出wwf = 10
	return 0;

}
```

# 10. 宏定义

**C预处理器**

比如

```c
#define A 1
```

那么程序中所有的A会被替换为1，这一过程叫做**编译时替换**。

在运行程序时，程序中所有的替换均已完成。通常，这样定义的常量也称为**明示常量**。

符号常量名用**大写**，这样便于区分，提高程序可读性。也可用c_  和 k_前缀来表示常量。

可以认为 符号常量 = 明示常量。

**切记不要写成#define A=1，这样A就被赋予=1，而不是1.**

```c
#define _CRT_SECURE_NO_WARNINGS 1//像scanf等c语言传统函数是不安全的，一些编译器会报错并且给出安全的版本。但也可以像前面一样宏定义来让他不警告。

int main(void)
{
	int num1 = 0;
	int num2 = 0;
	int sum = 0;
	scanf("%d%d", &num1, &num2);
	sum = num1 + num2;
	printf("sum =%d", sum);
		return 0;
}
```

#define指令还可以定义字符和字符串常量。前者使用单引号，后者使用双引号。

```c
#define BEEP '\a'

#define TEE 'T'

#define ESC '\033'

#define OOPS "Now you have done it!"
```



# 11.scanf与scanf_s的认知

​        scanf()在读取数据时不检查边界，所以可能会造成内存访问越界：

1     //例如：分配了5字节的空间但是用户输入了10字节，就会导致scanf()读到10个字节


2     char buf[5]={'\0'};

3     scanf("%s", buf);

4     //如果输入1234567890，则5以后的部分会被写到别的变量所在的空间上去，从而可能会导致程序运行异常。

-----------------------------------------------------------------------------------------------------------------------------------------------------------

​       以上代码如果用scanf_s（）则可避免此问题：

1     char buf[5]={'\0'};

2     scanf_s("%s",buf,5); //最多读取4个字符，因为buf[4]要放'\0' 

3     //如果输入1234567890，则buf只会接受前4个字符

# 12.const的含义与用法     

```c
#include <stdio.h>
int main(void)
{
	int num = 4;
	printf("%d\n", num);
	num = 8;
	printf("%d\n", num);
	return 0;
}
//打印出来后有4和8

#include <stdio.h>
int main(void)
{  //num是一个变量，但在前面加上const后就拥有了常属性，所以const num中的num是常变量-num是变量，但拥有常属性。
   //但是在需要用到常量表达式(包含常量，例一个数字9)时，不能用常变量。
   // int arr[10]      创建数组，[]中只能输入常量表达式,不能const int num = 10,再int arr[num]这是错误的。
   //const-const是一个C语言（ANSI C）的关键字，具有着举足轻重的地位。它限定一个变量不允许被改变，产生静态作用。
	const int num = 4;//但如果我们在int num前加上const，那么这个代码就跑不起来了，因为const修饰常变量，num用const修饰以后就不能变了

​	printf("%d\n", num);
​	num = 8;//而我们又在这里定义为8，所以发生错误
​	printf("%d\n", num);
​	return 0;

}
```

# 13.define 定义标识符常量

```c
#include<stdio.h>
int main(void)
#define max 10
{
	int arr[max] = { 0 };//不像12中用int定义的一样，用define定义一个常量 define max 10 ----定义max为常量10，此时int arr []中可以写入max
	printf("%d\n", max);//此时max也是可以打印的 打印出为10.而且max不在代码块里面，所以他是一个全局常量【应该可以这样理解】
	return 0;
}
```

# 14.枚举常量,enum-枚举名

为什么要用枚举？
#define MON  1
#define TUE  2
#define WED  3
#define THU  4
#define FRI  5
#define SAT  6
#define SUN  7
用枚举后
enum DAY{MON=1,TUE,WED, THU, FRI, SAT, SUN};
枚举后默认的第一个元素的整型为0 往后以此类推加一加一

# 15.常量总结

###           一.字面常量

###           二.const定义的常变量

###           三.define定义的常量

###           四.枚举常量

# 16.枚举

enum 分类名{常量，常量。。。}

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
enum color
{
	red,
	yellow = 10
};

int main(void)
{
	printf("%d\n", yellow);
	return 0;
}
//打印出是10  red默认为0 yellow默认为1 但在enum的代码块中我将他 = 10
//但如果我是在int main的代码块中将yellow = 10 写入 那么会产生错误
```

```c
enum{red,yellow,bule};
```

enum定义的常量，从左到右  依次加一  开始为0。

即red为0，yellow为1，bule为2

```c
enum{red,yellow=2,bule};
```

如果这样定义 那么red依然为0，bule为3.

enum定义的是常量 与 const int等同。

# 17.字符串以及其结束标志\0

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{   //字符串---由双引号引起来的一串字符称为字符串字面值，或者简称字符串.
	char arr1[] = "abc";//数组
	char arr2[] = { 'a','b','c'};
	printf("%s\n", arr1);//打印出来是 abc
	printf("%s\n", arr2);//打印出来是abc烫烫烫烫
    //用调试中的监控来监控"abc"和{'a','b','c'}我们可以发现 前者除了abc外还有个\0 而后者没有.
    //但如果我们把arr2改成{'a','b','c',\0},  (\0也可改为0)因为\0也表示0再来打印就是只打印abc了。\0是一个转义字符，计算字符串长度时是结束标志，不算作字符内容。
    // \0是字符串结束的标志，printf中检测到\0就会停止打印了。而出现烫烫烫烫是因为打印完abc后没有结束标志 继续随机生成的。
	return 0;
}
```

# 18.ASCII表

​         //数据在计算机上存储的时候，是以二进制来存储的。那么像一些特殊字符 %￥a等等，就用数字来指代他们。而为此制定了一个ASCII表
​         //例如a-97 A-65  字符所对的值叫做 ASCII码值
[ASCII表](http://t.csdn.cn/wy9S7)

# 19.srtlen---计算字符串长度

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	char arr1[] = "abc";
	char arr2[] = { 'a','b','c'};
	printf("%d\n", strlen(arr1));//输出为3 ( \0 ) 不计为字符串长度
	printf("%d\n", strlen(arr2));//输出为42，不是3是因为读完c后，后面有一些随机值被读取，因为没有\0结束标志所以会继续读取。
    //如果回答，第一个 3   第二个  随机值
    //如果arr2定义为 { 'a','b','c','\0'};则也是3
	return 0;
}
```

strlen不会将\0计入字符长度。

# 20.转义字符--把原来的意思转变了

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	printf("abcn");//会打印出abcn
	return 0;
}
```

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	printf("abc\n");//此时只会打印abc，因为\n是一个转义字符，意思为换行。上面\0 是字符串读取的中止标志是一样的转义字符
	return 0;
}
//    \加一些字符有一些特殊作用，称为转义字符 除了上面的\n  \0  还有\t--水平制表符   【在\t的位置加上一个tab大小的空】  空格只是一个字符  tab是一段字符
```

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	printf("c:\test\32\tect.c");//此时打印出来并不是我们想要的内容，是因为\加一些字符被识别成了转义字符。
	return 0;  
    //  c:\\test\\32\\tect.c   如果改成这个样子，那么\\t表示我将\t中的\转义成了普通\，而不是转义字符中的\
    //   \\用于表示一个反斜杠，防止它被解释为一个转义序列符
}
```

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	printf("%c\n",''');//此时会报错，因为前两个''是括字符串的 而里面又是空的，那么我们只需要'\''这样写就可以打印出'了。\'让他变成了一个普通的'。一个字符
	return 0;
}//   \'   \"也是转义字符。\'用于表示字符常量'         \"用于表示一个字符串内部的双引号
```

![image-20221011114543087](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221011114543087.png)

# 21.选择语句if,else

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	int input = 0;
	printf("会好好学习吗，会请输入1；不会请输入0.>:");
	scanf("%d",&input);//&去地址，%d以十进制打印符号整数,scanf输入函数
	if (input == 1)
	{
		printf("好工作\n");
	}
	else//else是其他的意思，如果你不输入if定义的1，那么无论你输入什么都会得到farmer。
        //但我们也可以不写else，写两个if也是可以的。如果输入两个if定义以外的就不会有输出。
	{
		printf("farmer\n");
	}
	return 0;
}
```

# 22.循环语句

## while循环

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	int line = 0;
	while (line < 5)//while循环语句
	{
		line++;//行数加一，一开始设定行数是0，如果去掉这个，那么会陷入死循环打印"代码".虽然输出代码有很多"行"，但真正的行数还是为0(开启显示行数就知道了)，所以要加line++
		printf("代码\n");//如果要显示行数则改为 printf("代码:%d\n",line);
	}
	if (line >= 5)
		printf("good job\n");//这个if后可加{}可不加
}
```

易错点:while语句不加;且要花括号.

## do-while循环

![image-20221014202127065](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221014202127065.png)

```c
#include<stdio.h>
int main(void)
{
	int line = 0;
	do
	{
		line++;
		printf("代码\n");
	} while (line < 5);
	if (line >= 5)
		printf("good job\n");
	return 0;
}
```

上述while循环的代码转换为do-while如上所示。

## for循环

## ![image-20221014210347827](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221014210347827.png)

![image-20221014210422537](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221014210422537.png)

for(1;2;3)1是初始条件，2是循环继续的条件，3是每一轮循环要做的事情(变量作运算来调整循环)。

且for循环的每一个表达式都是可以省略的，for( ;条件; )==while(条件)。

```c
#include<stdio.h>
int main(void)
{
	int line = 0;

	for (line = 0; line < 5; line++)
		printf("代码\n");
	
	if (line >= 5)
		printf("good job\n");
    
	return 0;
}
```

for循环转换上述代码如上所示。

选用循环语句:

1. 如果有固定循环次数，用for。
2. 如果必须先执行一次循环体再循环，用do-while。
3. 其他情况用while。

# 23.函数

## 一.自定义函数

在使用自定义函数时，要把函数定义写在所有使用函数地方的前面。

且自定义函数有声明和定义，两个要一致。	

需要说明的是：每个函数有自己的变量空间，参数也位于这个独立的空间，与其他函数没有关系。

用下面的代码进一步说明

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h> 
void swap(int a, int b);//参数

int main()
{
	int a = 5;
	int b = 6;
	swap(a, b);//值
	printf("a=%d b=%d\n", a, b);

	return 0;

}

void swap(int a, int b)//参数
{
	int t = a;
	a = b;
	b = t;
}
```

这个函数不能交换出a b的值，main中的a和b和swap中的int a int b除了传递值外没有任何关系。swap中的a，b和main中的a，b没有任何关系，更不相等。

![image-20221024133514027](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221024133514027.png)

```c
#include<stdio.h>
int add(int x, int y)
{
	int z = x + y;
	return z;
}
//上面称为函数体。
//这个add就是自定义函数，意义：用于定义一些反复使用的方法，例如上面举例的相加，当然还有更复杂的。
//简化代码，代码复用。
-------------------------------------------------------------------------------------
int main(void)
{
	int a = 10;
	int b = 20;
	int sum = 0;
	sum = add(a, b);
	printf("sum =%d\n", sum);
	return 0;
}
```

以下面这段代码来进行自定义函数转换。（代码复制是代码质量低的一种体现）

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	int i;
	int sum;

	for (i = 1, sum = 0; i <= 10; i++) {
		sum += i;
	}
	printf("1到10的和是%d\n", sum);
	for (i = 20, sum = 0; i <= 30; i++) {
		sum += i;
	}
	printf("20到30的和是%d\n", sum);
	return 0;

}
```

转换结果如下

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
void sum(int begin, int end)//函数头
//(int begin,int end)是参数表
//sum是函数名
//void是返回类型-没有，就是说sum函数不返回任何东西。
//{}内是函数体
{

	int i;
	int sum = 0;
	for (i = begin; i <= end; i++)
	{
		sum += i;
	}
	printf("从 %d到 %d的和是 % d\n",begin, end, i);

}
int main(void)
{
	sum(10, 20);//函数知道每一次是哪里调用它，会返回到正确的地方。
	sum(20, 30);//第一个sum执行完返回到第二个sum，再返回到return 0;
    
	return 0;

}
```

上面是void类型的，那我们下面再跑一个int类型的。

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int bj(int a,int b)
{
	int max;
	if (a > b)
	{
		max = a;
	}
	else {
		max = b;
	}
    
	return max;//void换成int，表明bj这个函数要返回一个int类型的值，即max。

}

int main(void)
{
	int end;
	end = bj(20, 30);
	printf("%d\n", end);
	return 0;
}
```

调用函数时给的值必须要和参数的类型匹配，虽然编译器会帮你转换好，但结果可能不是你想要的，C中不严格，C++/Java这方面严格。

同样的，这里面也有return的作用，在下节会讲。

当我们需要调用函数时，需要注意几点：

1. 函数名(参数值);
2. ()起到了表示函数调用的重要作用
3. 即使没有参数也需要()
4. 如果有参数，则需要给出正确的数量和顺序
5. 这些值会被按照顺序以此用来初始化函数中的参数

**圆括号()**

自定义函数时，如果圆括号内不填写任何东西，则不代表没有参数，只是表示这个自定义函数的参数不知道。

那么编译器遇到swap(a,b)时会猜测参数是什么类型

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h> 
void swap();

int main()
{
	int a = 5;
	int b = 6;
	swap(a, b);
	printf("a=%d b=%d\n", a, b);

	return 0;

}

void swap(int a, int b)
{
	int t = a;
	a = b;
	b = t;
}
```

当然这里没有任何问题，如果把swap定义中的换成void swap(double a,double b)

那结果就会有偏差。

还有就是main函数的圆括号。

以后我们就不止会用到main函数，有时会需要main函数返回一个值，而main(void)表示main不返回任何值。



## 二.库函数

常用的头文件有**<ctype.h>**  **<time.h>**  **<stdio.h>** **<stdlib.h>** **<math.h>**  **<string.h>**

每个头文件中都包含着不同的库函数。详情移步----------->:[C语言标准库函数大全](https://blog.csdn.net/weixin_44793491/article/details/107644666?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166546623316782417032511%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=166546623316782417032511&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-107644666-null-null.142^v52^new_blog_pos_by_title,201^v3^add_ask&utm_term=c%E5%BA%93%E5%87%BD%E6%95%B0&spm=1018.2226.3001.4187)

# 24.return

return停止函数的执行，并送回一个值。

return;

return 表达式;

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int bj(int a,int b)
{
	int max;
	if (a > b)
	{
		max = a;
	}
	else {
		max = b;
	}
	

	return max;//可以把这个值传递给变量，或者函数，也可以丢掉(没有把这个值给任何东西)
    //函数要单一出口，虽然多个return不会报错，但是不好维护，所以最好单一出口.

}

int main(void)
{
	int end;
	end = bj(20, 30);//上面bj中的return max;送回max这个值就是在这里体现，把送回的max赋给end，打印end就是sum的值
	printf("%d\n", end);//即bj(20,30) = 30
	return 0;
}
```

如果函数有返回值，则必须使用带值的return。

没有返回值的函数

- void 函数名(参数表)
- 不能使用带值的return
- 可以没有return
- 调用的时候不能做返回值的赋值

# 25.数组

## 一.数组的定义

一组相同类型元素的集合。

<类型>变量名称[元素数量];//元素数量是整数。

eg:

int grades[100];

double weight[20];

```c
#include<stdio.h>
int main(void)
{
	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };//定义一个存放10个整型的数组.
	float arr2[2];//定义一个存放2个浮点型的数组.
	char ch[3];//定义一个存放3个字符的数组.
	return 0;
}
```

## 二.数组的特点

1. 其中所有的元素具有相同的数据类型(int,double等)。
2. 一旦创建，不能改变大小。
3. 数组中的元素在内存中是连续依次排列的。

## 三.数组的使用

如上 int arr[10] = ......

其中的 1,2,3,4,5,6,7,8,9,10其实是有下标的，如下

​             0,1,2,3,4,5,6,7,8,9

这个下标是编译时机器识别的序号。

而编译器和运行环境都不会检查数组下标是否越界，无论对数组单元做读还是写。所以一旦程序运行，越界的数组访问可能造成问题，导致程序崩溃。所以要保证程序只使用有效的下标值。

> **有效的下标范围[0,数组的大小-1]**



```c
#include<stdio.h>
int main(void)
{
	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };
	printf("%d\n",arr[4]);//数组的下标默认从0开始，打印数组中下标为4的数，那么就是5。
	return 0;
}
```

代码跑起来打印出来的是5.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

那么再与while循环语句结合一下

```c
#include<stdio.h>
int main(void)
{
	int i = 0;
	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };
	while (i < 10)
	{
		printf("%d\n", arr[i]);//此处的i还是数组下标，因为arr中10的下标为9(<10)，所以可以打印10
		i++;
	}
	return 0;
}
```

**数组应用**

输入数，计算出平均数并给出大于平均数的数。的代码

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	int x;
	double sum = 0;
	int cnt = 0;
	int number[100];//定义数组
	scanf("%d", &x);
	while (x != 1)
	{
		number[cnt] = x;//对数组中的元素赋值
		sum += x;
		cnt++;
		scanf("%d", &x);
	}
	if(cnt>0)
	{
		int i;
		double average = sum / cnt;
		for (i = 0; i < cnt; i++)
		{
			if(number[i]>average)//使用数组中的元素
			{
			 printf("%d", number[i]);
			}//遍历数组
		}
	}
	return 0;
}
```

但这个代码有安全隐患，如果cnt超过数组的大小就会有隐患。

![image-20221027224818693](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221027224818693.png)

![image-20221027225157016](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221027225157016.png)

## 四.二维数组

![image-20221025222141721](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221025222141721.png)

![image-20221025222422994](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221025222422994.png)

a[i,j]=a[j]

**二维数组初始化**

![image-20221025222523538](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221025222523538.png)

## 五.数组运算

![image-20221026172125668](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221026172125668.png)

a[0]=2,a[2]=3,a[3]=6

**数组赋值**

![image-20221026173458599](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221026173458599.png)

# 26.操作符(简单介绍)

## 一.算数操作符

### +  -   *   /    %

-----------------------------------------------------------------------------------------------------------------------------------------------------------

前四个是加减乘除，不作过多赘述。

%是取模，例如

```c
#include<stdio.h>
int main(void)
{
	int a = 5%2;
	printf("%d\n", a);
	return 0;
}
```

5➗2 = 2......1 余数为1，

那么5%2=1。

## 二.移(二进制)位操作符

-----------------------------------------------------------------------------------------------------------------------------------------------------------

<<左移        >>右移

```c
#include<stdio.h>
int main(void)
{
	int a = 1;
	int b = a << 1;
	printf("%d\n", b);
	return 0;
}
```

整型1占4个字节，也就是32个bit位，也就是0000000000000...0001.

如果把1左移一个(二进制)位--b，成为0000000000000...0010.（想象32个bit位是一个框，左移最左边的0出去了，然后右边空出自动补0）.

那么再以十进制打印b的话就会打印出2.

所以上述代码打印出的是2

-----------------------------------------------------------------------------------------------------------------------------------------------------------

```c
#include<stdio.h>
int main(void)
{
	int a = 1;
	int b = a << 2;
	printf("%d\n", b);
	return 0;
}
```

同样，如果左移两个(二进制)位。b就是0000000000000...0100.

也就是二进制100打印输出为十进制数，也就是4.

## 三.(二进制)位操作符

&按位与            |按位或            ^按位异或

-----------------------------------------------------------------------------------------------------------------------------------------------------------

### &按位与

```c
#include<stdio.h>
int main(void)
{
	int a = 3;
	int b = 5;
	int c = a & b;
	printf("%d\n", c);
	return 0;
}
```

代码跑起来输出结果为1.

3的二进制数是011，5的二进制数是101.

011

101

001(结果)

按位与的运算法则就是，对位有0就得0，两个1才为1.

001为二进制数，转化为十进制仍然为1.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

### |按位或

```c
#include<stdio.h>
int main(void)
{
	int a = 3;
	int b = 5;
	int c = a|b;
	printf("%d\n", c);
	return 0;
}
```

输出结果为7.

011

101

111(结果)

按位或的运算法则就是，对位只要有1，那么结果就为1.

二进制数111转化为十进制为7.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

### ^按位异或

```c
#include<stdio.h>
int main(void)
{
	int a = 3;
	int b = 5;
	int c = a^b;
	printf("%d\n", c);
	return 0;
}
```

输出结果为6.

011

101

110(结果)

按位或与的运算法则就是，对位的二进制位相同则为0，二进制位相异则为1.(二进制位就是0和1)

二进制数110转化为十进制数为6.

## 四.赋值操作符

=     +=     -=     *=     /=     &=     |=     ^=     >>=     <<=

```c
#include<stdio.h>
int main(void)
{
	int a = 10;
	a = 20;//需要说明的是， = 是复制，== 判断相等.
		a = a + 10;
		a += 10;//这两种写法是等价的
    
		a = a & 10;
		a &= 10;//等价
	return 0;
}
```

其他的以此类推.

## 五.单目操作符

![image-20221011210846847](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221011210846847.png)

除了单目操作符还有双目操作符，三目操作符。

例如a+b。 +是一个双目操作符，因为它有两个操作数。

------

### ! 逻辑取反操作

```c
#include<stdio.h>
int main(void)
{
	int a = 10;
	printf("%d\n", a);//打印出10
	printf("%d\n", !a);//打印出0
	return 0;
}
```

在C语言中，0定义为假，非0为真。逻辑取反操作就是让假为真，真为假。

那么10是非0，为真，逻辑取反操作后就为假，即为0.

------

### sizeof

sizeof 计算变量/类型所占空间的大小，单位是字节.

```c
#include<stdio.h>
int main(void)
{
	int a = 10;
	printf("%d\n", sizeof(a));
	printf("%d\n", sizeof(int));
    printf("%d\n", sizeof a);
    printf("%d\n", sizeof int)://这种写法是错误的.
	return 0;
}
```

如上，我们给出了四行printf。第一二三行是正确的，第四行是错误的。

sizeof在计算变量所占空间的大小时，可以省略().而计算类型所占空间大小时不能省略.

第一行，第二行的结果是一样的.(int类型普遍占4个字节)

------

与数组结合

```c
#include<stdio.h>
int main(void)
{
	int arr[10] = { 0 };//10个整型元素的数组。1个整型4个字节。
	printf("%d\n", sizeof(arr));
}
```

格式化输出为40.

```c
#include<stdio.h>
int main(void)
{
	int arr[10] = { 0 };
	int number = 0;
	number = sizeof(arr) / sizeof(arr[0]);
	printf("number =%d\n", number);
}
```

上为计算数组内元素个数的方法，用数组大小除以元素大小(同类型元素大小相同，而数组是相同类型元素的集合).

输出为10.

### ++和--的前置与后置

设变量a。

++a是先执行a = a+1,然后再使用a。

a++是先使用a，再执行a = a+1。

--同原理

------

![image-20221015132031122](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221015132031122.png)

# 27.格式字符

![image-20221014120006854](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221014120006854.png)

# 28.关系运算符

![image-20221014193757929](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221014193757929.png)

------

![](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221015132130218.png)

------

![image-20221015132318000](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221015132318000.png)

![image-20221015132251524](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221015132251524.png)

------

![image-20221014194223203](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221014194223203.png)

------



#### 实例

![image-20221014201237180](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221014201237180.png)

# 29.逻辑运算

![image-20221015142650692](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221015142650692.png)

如果要表达数学中的区间 x∈(4,6).那么不能写成4<x<6.

这样写c语言会先将4<x看成一个逻辑运算，结果是0或1。

不论结果是0还是1都是小于6的，所以最后结果是1.

正确写法应为：x>4&&x<6.

下面看一些例子

![image-20221015143220929](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221015143220929.png)

1.20<age<30

2.小于0或大于99

3.虽然逻辑运算符优先级小于比较运算符，但！是单目运算符，单目运算符优先级高于双目运算符。

所以！age先处理，结果为1或0，然后再与20比较。整个表达式是1.（若要先处理age<20,则要加括号).

------

整体优先级：!>&&>||

------

![image-20221015152745984](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221015152745984.png)

# 30.switch-case（多分支处理代替if else)

![image-20221015181211904](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221015181211904.png)

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	int type = 0;
	scanf("%d", &type);
	if (type == 1)
		printf("你好");
	else if (type == 2)
		printf("早上好");
    else
        printf("what?");
    
	return 0;
}
```

转换为switch-case

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	int type;
	scanf("%d",&type);
    
	switch (type) {                
	case 1:printf("你好"); break;
	case 2:printf("早上好"); break;
    default:printf("what?");break;
            
    }
	return 0;
}
```

有几点需要说明的是

1. break是c语言中的一个关键字，在这里专门用于跳出switch语句。所谓“跳出”，是指一旦遇到 break，就不再执行 switch 中的任何语句，包括当前分支中的语句和其他分支中的语句；也就是说，整个 switch 执行结束了，接着会执行整个 switch 后面的代码。
2. 如果直到最后一个“整型数值n”都没有找到相等的值，那么就执行 default 后的“语句 n+1”。
3. 当和某个整型数值匹配成功后，会执行该分支以及后面所有分支的语句。
4. 由于 default 是最后一个分支，匹配后不会再执行其他分支，所以也可以不添加break;语句。
5. case 后面必须是一个整数，或者是结果为整数的表达式，但不能包含任何变量。
6. default 不是必须的。当没有 default 时，如果所有 case 都匹配失败，那么就什么都不执行。

在循环中，有两个词组是经常用到的

1. break，跳出循环。
2. continue，跳过循环这一轮剩下的语句进入下一轮。

# 31.嵌套循环

下面是用 1角 2角 5角 得到x元的程序

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)

{
	int x;
	int one, two, five;
	

	scanf("%d", &x);
	for (one = 1; one < x * 10; one++) 
    {
		for (two = 1;two < x * 10 / 2; two++) 
         {
			for (five = 1; five < x * 10 / 5; five++)
             {
				if (one + two * 2 + five * 5 == x * 10)
                 {
					printf("可以用%d个1角加%d个2角加%d个5角得到%d元\n", one, two, five, x);		
				}
			}
		}
	}
    
	return 0;
}


```

他可以罗列出所有可能，但如果我们只要他输出一种的话就要跳出这个嵌套的循环。

如果光用一个break加在printf后面那是不行的。

因为break和continue都只能跳出他所在的循环，也就是说如果放break只能跳出第三个for循环，第一个和第二个for循环仍然进行。

所以我们可以接力break，如下:

## 接力break

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	int x;
	int one, two, five;
	int exit=0;
	

	scanf("%d", &x);
	for (one = 1; one < x * 10; one++)
    {
		for (two = 1;two < x * 10 / 2; two++)
        {
			for (five = 1; five < x * 10 / 5; five++) 
            {
				if (one + two * 2 + five * 5 == x * 10) 
                {
					printf("可以用%d个1角加%d个2角加%d个5角得到%d元\n", one, two, five, x);
					exit = 1;
					break;
				
			    }
		    }if (exit == 1)break;
	    }if (exit == 1)break;
	}
	return 0;

}
```

加一个exit变量，在得到一个结果赋予他1，然后在第一个for第二个for循环末接上if-break。

还有一种更简单的方式goto out，如下:

## goto out

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main(void)
{
	int x;
	int one, two, five;
	

	scanf("%d", &x);
	for (one = 1; one < x * 10; one++) {
		for (two = 1;two < x * 10 / 2; two++) 
		{
			for (five = 1; five < x * 10 / 5; five++) 
			{
				if (one + two * 2 + five * 5 == x * 10) 
				{
					printf("可以用%d个1角加%d个2角加%d个5角得到%d元\n", one, two, five, x);
					goto out;
				
				}
			}
		}
	}
	out:
	return 0;

}
```

goto out 顾名思义 去到out的地方 ，out的地方用 out:来代替。

这种方法虽然看起来好，但是goto out是臭名昭著的。

因为goto 语句是在源码级上的跳转，这使其招致了不好的声誉。若一个程序总是从一个地方跳
到另一个地方，还有什么办法能识别程序的控制流程呢？随着 Edsger Dijkstra 著名的《Goto
considered harmful》论文的出版，众人开始痛斥 goto 的不是，甚至建议从关键字集合中扫
地出门。

所以尽量不要使用goto out，仅在break和continue需要用来跳出嵌套循环时再使用它。

# 32.system

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdlib.h>
int main(void)
{
	system("calc");
	return 0;
}
```

system用于打开系统应用，calc是计算器，那么这个程序运行后就会打开计算器。

需要注意的是system所对应的头文件是<stdlib.h>.

# 33.本地变量(自动变量)

- 函数的每次运行，就产生了一个独行的变量空间，在这个空间中的变量，是函数的这次运行所独有的，称作本地变量

- 定义在函数内部的变量就是本地变量

- 参数也是本地变量

- 对于本地变量来说，生存期和作用域是一样的:大括号内--块

- 本地变量是定义在块内的，这个块可以是函数的块内也可以是语句的块内

- 程序运行进入这个块之前，其中的变量不存在，离开这个块，其中的变量就消失了

- 块外面定义的变量在块里面仍然有效

- 块里面定义了和外面同名的变量则掩盖了外面的(全局变量和局部变量)

- 不能再同一个块内定义同名的变量

- 本地变量不会被默认初始化

- 参数在进入函数的时候被初始化了(调用函数的时候，一定要给参数对应的值，那个值会在进入函数时被用来初始化函数)

  ```c
  #define _CRT_SECURE_NO_WARNINGS 1
  #include <stdio.h> 
  
  int main()
  
  {
  
  int a;
  
  int b;
  
  scanf("%d %d",&a,&b)
  
  if(a<b)
  
  {
  
  int i =10;//i只在块里面
  
  }
  
  i++;//这里的i会显示未被声明，i只在块里面
  
  }
  ```

  

## 一.生存期

什么时候这个变量开始出现了，到什么时候它消亡了

称为自动变量是因为生存期是自动的。

## 二.作用域

前面也提到，在代码的什么范围内可以访问这个变量(这个变量可以起作用)

下面用代码来进一步说明

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h> 
void swap(int a, int b);//参数

int main()
{
	int a = 5;
	int b = 6;
	swap(a, b);//从这里开始就进入到下面的swap的变量空间，做完swap里的代码后，swap的变量空间就消失了，再调用时才会出现。
	printf("a=%d b=%d\n", a, b);

	return 0;

}

void swap(int a, int b)//参数
{
	int t = a;//swap变量空间中的a，b，t是swap自己的，和main里的a，b没有关系，无论怎么赋值，main中的ab都不会被影响
	a = b;
	b = t;
}
```

# 34.字符串

字符串是一个或多个字符的序列。如下:

"gong is playing computer games"

双引号不是字符串的一部分，双引号仅告知编译器它括起来的是字符串。

## 一.char和null

C中字符串都被储存在char类型的数组中。数组由连续的存储单元组成，字符串的字符被储存在相邻的存储单元中，每个单元一个字符。

gong is playing computer games\0

gong is占了7个单元，空格算入其中。

\0是空字符(null)，是字符串结束的标志，其ASCII码值也是0.

## 二.使用字符串

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h> 
int main()
{
	char name[40];
	scanf("%s", name);//存入gong xi
	printf("%s", name);//输出gong
	return 0;
}
```

使用%s转换说明来处理字符串的输入和输出。

有一点要注意name前没有&,这与之前的&变量不同，&变量和name 都是地址。

存入gong xi。输出gong。是因为scanf只读取了gong，它在遇到第1个空白(空格制表符或换行符)时就不再读取输入。

根据%s，scanf()只会读取字符串中的一个单词，而不是一整句。其他输入函数fgets()在后面介绍。

**字符串和字符**

"x"是字符串，'x'是字符。区别之一在于'x'是基本类型(char),"x"是派生类型(char数组)；区别之二是"x"实际上由两个字符组成:'x'和空字符\0

## 三.strlen()函数

strlen()函数用于给出字符串中的字符长度。

虽然1字节储存1字符，但sizeof与strlen应用于字符串得到的结果并不同。

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h> 
int main()
{
	char name[40];

	scanf("%s", name);//输入weixin
	printf("%d\n", sizeof (name));//打印出40
	printf("%d", strlen(name));//打印出6
	return 0;

}
```

40是name数组的总存储单元，6是只有6个单元用来储存weixin。（自动忽略空字符）

有40个存储单元的字符串要留一个给空字符，也就是说只能储存39个字符。

**string.h头文件**

string.h包含了strlen()和其他一些与字符串相关的函数。

# 35.printf()转换说明

![image-20221101180527746](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101180527746.png![image-20221101181448188](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101181448188.png)

![image-20221101181401015](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101181401015.png)

## 转换说明修饰符

![image-20221101221809022](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101221809022.png)

![image-20221101224044158](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101224103963.png)

![image-20221101224121619](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101224121619.png)

**字段宽度**

```c
#include <stdio.h>
#define PAGES 959
int main(void)
{
	printf("*%d*\n", PAGES);
	printf("*%2d*\n", PAGES);
	printf("*%10d*\n", PAGES);
	printf("*%-10d*\n", PAGES);
	return 0;
}
```

输出结果

![image-20221101224432769](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101224432769.png)

第二个转换说明%2d的输出结果是2字段宽度。因为待打印的整数有3位数字，所以字段宽度自动扩大来符合整数的长度

第三个转换说明%10d，输出结果是10个空格官渡，两个星号之间有7个空格和3位数字，且数字位于字段右侧。

第四个转换说明%-10d,-标记说明打印的数字位于字段的左侧。

**浮点型格式**

```c
#include <stdio.h>
int main(void)
{
	const double RENT = 3852.99;
	printf("*%f*\n", RENT);
	printf("*%e*\n", RENT);
	printf("*%4.2f*\n", RENT);
	printf("*%3.1f*\n", RENT);
	printf("*%10.3f*\n", RENT);
	printf("*%10.3E*\n", RENT);
	printf("*%+4.2f*\n", RENT);
	printf("*%010.2f*\n", RENT);
	return 0;
}
```

![image-20221101224929028](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101224929028.png)

**打印不同大小的值**

```c
#include <stdio.h>
int main(void)
{
printf("%x %X %#x\n", 31, 31, 31);
printf("**%d**% d**% d**\n", 42, 42, -42);
printf("**%5d**%5.3d**%05d**%05.3d**\n", 6, 6, 6, 6);
return 0;
}
```

![image-20221101230019603](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101230019603.png)

**字符串格式**

```c
#include <stdio.h>
#define BLURB "Authentic imitation!"
int main(void)
{
printf("[%2s]\n", BLURB);
printf("[%24s]\n", BLURB);
printf("[%24.5s]\n", BLURB);
printf("[%-24.5s]\n", BLURB);
return 0;
}
```

![image-20221101230101878](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221101230101878.png)

## 转换说明的意义

转换不是说转换后的值替代了原来的值。

转换的意思是将储存在计算机里的二进制数翻译成。。。并打印出来

%d的意思是翻译成十进制并输出。 

**转换说明一定要转换匹配**

### printf()的返回值

```c
#include <stdio.h>
int main(void)
{
int bph2o = 212;
int rv;
rv = printf("%d F is water's boiling point.\n", bph2o);
printf("The printf() function printed %d characters.\n",rv);
return 0;
}
```

![image-20221102081341681](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221102081341681.png)

rv被赋予了printf()内的字符数。也就是printf()的返回值，这里的计算字符数针对所有的字符数，包括空格和不可见的换行符\n.

### 打印较长的字符串

打印较长的字符串有3种方法：

1.使用多个printf().

2.用反斜杠\和回车键组合来断行，但下一行代码必须从最左边开始，否则会有多余的空格。

```c
printf("hello,young lovers\
 why do you ?");//输出在一行。
```

3.字符串连接，在两个用双引号括起来的字符串之间用空白隔开

```c
printf("hello, young lovers "

 "why do you");//输出也在一行。上下两行的引号间的空白会被忽略。
```

# 36.scanf()

如果用scanf()读取基本变量类型的值，在变量名前加上一个&;

如果用scanf()把字符串读入字符数组中，不要使用&。

**转换说明**

%c例外，根据%c，scanf()会读取每个字符，包括空白。

scanf()与printf()转换说明的主要区别是:

对于float类型和double类型，printf()都使用%f,%e,%E,%g和%G.

而scanf()只把他们用于float类型，对于double要使用 1修饰符。

![image-20221102083841870](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221102083841870.png)

可以在转换说明间使用修饰符，但使用多个修饰符时必须要以表中的顺序来写。

![image-20221102083940943](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221102083940943.png)

![image-20221102083954878](http://rjhcx50lo.hn-bkt.clouddn.com/imagine/image-20221102083954878.png)

# 37.*修饰符

*修饰符在printf()和scanf()中有不同的用法。

**printf():**

如果你不想预先指定字段宽度，希望通过程序来指定，那么可以用*修
饰符代替字段宽度。但还是要用一个参数告诉函数，字段宽度应该是多少。

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main()
{
	int width;
	float num;
	num = 123.123;

	scanf("%d",&width);
	printf("%.*f", width, num);
	return 0;

}
```

*可以说是一个占位符，width的数据来代替他。

想把数据打印成列，指定固定字段宽度很有用。因为默认的字段宽度是
待打印数字的宽度，如果同一列中打印的数字位数不同，那么下面的语句：
printf("%d %d %d\n", val1, val2, val3);
打印出来的数字可能参差不齐。例如，假设执行3次printf()语句，用户
输入不同的变量，其输出可能是这样：
12 234 1222
4 5 23
22334 2322 10001
使用足够大的固定字段宽度可以让输出整齐美观。例如，若使用下面的
语句：
printf("%9d %9d %9d\n", val1, val2, val3);
上面的输出将变成：
12　　　234　　　1222
4　　　　5　　　　23
22334　　2322　　10001

如果要在文字中嵌入一个数字，通常指定一个小于或等于该
数字宽度的字段会比较方便。这样，输出数字的宽度正合适，没有不必要的
空白。

**scanf()**

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main()
{
	int width;
	float num;
	num = 123.123;

	scanf("%*d %*d %d",&width);
	printf("%.*f", width, num);
	return 0;

}
```

*在scanf里是跳过的意思。

我输入1 2 3 那么1 2 将不被读取 只有3会赋给width。

# 38.递归

C允许函数调用它自己，这种调用过程称为**递归**。

演示递归的代码

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
void(up_and_down)(int n);
int main(void)
{
	up_and_down(1);
	return 0;

}

void(up_and_down)(int n)
{
	printf("Level　%d:　n　location　%p\n", n, &n);//1
	if(n< 4)
		up_and_down(n+ 1);
	printf("LEVEL　%d:　n　location　%p\n", n, &n);//2
}
```

输出结果为:

Level　1:　n　location　0x0012ff48
Level　2:　n　location　0x0012ff3c
Level　3:　n　location　0x0012ff30
Level　4:　n　location　0x0012ff24
LEVEL　4:　n　location　0x0012ff24
LEVEL　3:　n　location　0x0012ff30
LEVEL　2:　n　location　0x0012ff3c
LEVEL　1:　n　location　0x0012ff48

到up_and_down(n+ 1);这里代码又会回到1这里，以此反复，然后再一级一级退出。

------

**尾递归**

最简单的递归形式，把递归置于return 0前，相当于循环。

**优缺点**

优点：

简单的解决方案

缺点:

耗费资源

# 39:条件运算符

条件运算符：?:
一般注解：
条件运算符需要3个运算对象，每个运算对象都是一个表达式。其通用
形式如下：
expression1 ? expression2 : expression3
如果expression1为真，整个条件表达式的值是expression2的值；否则，
是expression3的值。
示例：
(5 > 3) ? 1 : 2 值为1
(3 > 5) ? 1 : 2 值为2
(a > b) ? a : b 如果a >b，则取较大的值

# 40.指针

从根本上看，指针（pointer）是一个值为内存地址的变量（或数据对象）。
假设一个指针变量名是ptr，可以编写如下语句：
ptr = &pooh; // 把pooh的地址赋给ptr

对于这条语句，我们说ptr“指向”pooh。

**间接运算符***

后跟一个指针名或地址时，*给出储存在指针指向地址上的值。

因此，我们可以**初窥scanf**

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main()
{
	int a = 1;
	int* temp = &a;
	*temp = 2;
	printf("%d", a);
	return 0;
}
```

输出为2，也就是说上述代码和scanf的作用等同。

**交换变量值**

前面有提到过变量值互换的问题。自定义函数内的函数不能影响主函数中的函数，但指针可以做到。

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
void change(int *x,int *y);
int main()
{
	int x = 2;
	int y = 3;
	change(&x, &y);
	printf("%d %d", x, y);
	return 0;
}

void change(int *x, int *y)
{
	int temp = *x;
	*x = *y;
	*y = temp;
}
```

这可以实现x,y间值的交换。

# 41.数组变量本质是地址

数组变量是特殊的指针。

如果我们int a[10];

那么可以直接int *p=a;无需&取地址符。

但是对于数组单个的单元取地址需要&。

a==&a[0]

[]运算符可以对数组做，也可以对指针做。

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
int main()
{
	int num = 2;
	int* a=&num;
	printf("%d", a[0]);
}
```

对指针加[]运算符，编译器会认为这个a是数组。但有效下标只有[0].

同样，*运算符也可以对数组做。

其实数组变量是有const修饰的指针，所以不能被赋值。

```c
int b[]-->int * const b=...
```

# 42.结构类型

当我们需要把很多数据用一个变量表现出来时就要用到结构类型。

结构类型可以在函数外也可以在函数内，其内外的作用范围与变量一样。

声明结构的形式

```c
struct point {
		int x;
		int y;
	};

struct point p1, p2;
```

```c
struct{
		int x;
		int y;
	}p1,p2;
```

```c
struct point{
		int x;
		int y;
	}p1,p2;
```

**结构类型初始化**

```c
struct date {
		int day;
		int month;
		int year
	}today,yesterday;

struct date today = { 2,1,2023 };
	struct date yesterday = { .day = 1,.month = 3 };
```

```c
struct date {
		int day;
		int month;
		int year
	}today, yesterday;

today.day = 20;
today.month = 10;
today.year = 2023;//额外的一种赋值方式
```

有两种初始化方式，第一种直接给数字。第二种用.运算符来赋值，如果赋值的个数小于元素的个数，即year没有赋值，那么他就会被自动填充为0.

结构和数组有点像。数组用[]运算符和下标访问其成员，而结构用.运算符和名字访问其成员。

**结构运算**

1. 访问整个结构，直接用结构变量的名字。

2. 对于整个结构，可以做赋值、取地址，也可以传递给函数参数

   ```c
   p1 = (struct point){ 5,10 };//相当于p1.x=5;p1.y=10
   	p1 = p2;//相当于p1.x=p2.x;p1.y=p2.y
   ```

**结构指针**

和数组不同，结构变量的名字并不是结构变量的地址，必须使用&运算符。

```c
struct date *pdate = &today;
```

**结构作为函数参数**

```c
int num(struct date d)
```

整个结构可以作为参数的值传入函数

这时候是在函数内新建一个结构变量，并复制调用者的结构的值，这一点与前面的变量交换值类似。

也可以返回一个结构。

**输入结构**

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>

struct point {
	int x;
	int y;
};

void input();
void output();
int main()
{	
	struct point y = { 0,0 };
	input(y);
	output(y);

return 0;

}

void input(struct point p)
{
	scanf("%d", &p.x);
	scanf("%d", &p.y);
	printf("%d,%d", p.x, p.y);
}

void output(struct point p)
{
	printf("%d.%d", p.x, p.y);
}
```

input中的输入的值无法传递到main中。

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>

struct point {
	int x;
	int y;
};

struct point input();
void output(struct point);
int main()
{	
	struct point y = { 0,0 };
	y = input();
	output(y);
}

struct point input(void)
{
	struct point p;
	scanf("%d", &p.x);
	scanf("%d", &p.y);
	printf("%d,%d", p.x, p.y);
	return p;
}

void output(struct point p)
{
	printf("%d,%d", p.x, p.y);
}
```

这种input中的值就可以传回main了。还可以用指针。

```c
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>

struct point {
	int x;
	int y;
};

struct point* input();
void output(struct point);
int main()
{	
	struct point y = { 0,0 };
	input(&y);
	output(y);
}

struct point* input(struct point *p)
{
scanf("%d", &p->x);
scanf("%d", &p->y);
printf("%d,%d", p->x, p->y);
return p;
}

void output(struct point p)
{
	printf("%d,%d", p.x, p.y);
}
```

**->**运算符，用**->**表示指针所指的结构变量中的成员。

小技巧:

1. alt+方向键 可以把一行代码向上移或者向下移。
2. alt+caps+a 鼠标左键拉选要修改的连续行的同一列 或者 按住鼠标滚轮拉选要修改的连续行的同一列。
3. 



杂记:

每次召唤rand()就得到一个随机的整数。

x%n的结果是[0,n-1]的一个整数