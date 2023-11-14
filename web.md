# 一.难度1

## 1.WWW-Robots

![image-20230916211449333](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916211449333.png)

可知robots.txt会泄露目录结构，所以我们直接通过网址访问它。

![image-20230916211618597](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916211618597.png)

这个disallow是不被接受的意思，不想被我们访问，那我们再访问它，通过相同的方式。

![image-20230916211703996](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916211703996.png)

flag值出来了。

## 2.PHP2

![image-20230916215732650](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916215732650.png)

首先，就一行字。没有什么信息。

​		看一下源代码![image-20230916215817854](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916215817854.png)

发现没什么东西，那么试一下index.php![image-20230916215859867](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916215859867.png)

还是这个界面，那么再看一下网页。按F12，看一下数据包。![image-20230916215956651](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916215956651.png)

再看下源代码。![image-20230916220007720](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916220007720.png)

ok，发现还是没什么东西，看下备份文件，常用后缀  **.bak**

![image-20230916220045341](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916220045341.png)

发现没东西，那么再试一试  **.phps**，也是一种备份后缀。

![image-20230916220124673](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916220124673.png)

ok，出现信息了。读代码可知，用变量id去接受经过url编码过后的 admin才会出现答案。那么我们使用burpsuite进行编码。

![image-20230916220240940](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916220240940.png)

得到编码之后。在index.php界面后加变量id后缀

![image-20230916220331902](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916220331902.png)

回车之后发现浏览器自动解码了，使用火狐的hacker bar也有此问题。![image-20230916220448030](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916220448030.png)**那么就双重编码。**

![image-20230916220612431](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916220612431.png)

ok，再输入进去

![image-20230916220622365](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230916220622365.png)

得到了key

## 3.unserialize3

![image-20230917094921078](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917094921078.png)

定义了一个类 xctf，这里的wakeup是php的一个魔术方法

当使用 `unserialize()` 反序列化一个对象成功后，会自动调用该对象的 `__wakeup()` 魔术方法。

该方法的原型如下

```
public function __wakeup()
{
    // 一些其它初始化操作
}
```

该魔术方法既没有参数，也没有返回值

既然是一段php代码，那么我们将其移到vscode上进行

![image-20230917095139246](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917095139246.png)

通过这个魔术方法可知，会进行反序列化。

那么我们就要序列化

![image-20230917095343930](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917095343930.png)

然后运行。

![image-20230917095450355](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917095450355.png)

### 漏洞产生原因

如果类中存在__wakeup方法，调用 unserilize() 方法前则先调用__wakeup方法，当序列化字符串中表示对象属性个数的值大于 真实的属性个数时会跳过__wakeup的执行

```
O:4:"xctf":1:{s:4:"flag";s:3:"111";}

O代表object（为A时代表Array），4代表"test"占4个字符长度，1代表着对象具有1个变量，s代表string，字符型（如果为i，代表int型）
```

对象属性指 类中方法外的变量，在此题中也就是flag

个数为1，那么我们只需要把1改成比1大的就可以了。

![image-20230917100402182](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917100402182.png)

## 4.ics-06

![image-20230917101831335](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917101831335.png)

打开之后。![image-20230917101848754](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917101848754.png)

所有按钮都点一遍，发现只有报表中心可以进去。

![image-20230917101921442](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917101921442.png)

选择日期范围点确认也没有响应。

那么网址上的 ?id=1 有一点痕迹。

用burpsuite抓一下包

![image-20230917102021365](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917102021365.png)

没有东西，那么我们爆破一下id。![image-20230917102101685](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917102101685.png)

这里选择sniper （狙击），把  id = 1 中的1标上。

然后![image-20230917102134153](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917102134153.png)

选出起始，终止，步长，从1到10000开始爆破

![image-20230917102224102](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917102224102.png)

发现有一个返回的数据包长度不一样，那么里面就有额外的东西。

![image-20230917102314848](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917102314848.png)

![image-20230917102334116](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230917102334116.png)

得到答案。

## 5.view_source

![image-20230918121230651](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918121230651.png)

没啥难度，F12也可查看源代码。

![image-20230918121255130](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918121255130.png)

## 6.get_post

![image-20230918121938221](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918121938221.png)

![image-20230918121953165](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918121953165.png)

明确提示：

1. GET方式：GET作为四种HTTP请求方法之一（剩下三种分别为HEAD、POST、PUT。常见只有GET和POST两种HTTP请求方式），GET请求主要是用于'传参'，但参数会直观地显示在URL中；POST请求主要是用于隐藏’传参‘，POST请求常见用于账户密码登录。

2. 提交一个名为a，值为1的变量：提交的变量即为参数，这个参数就叫a=1（其中，a是参数也就是变量的名称，1是参数也就是变量的值，汉字 ’ 为‘ 是参数赋值的 ’赋‘ 一字，在URL中表示为 =

3. 还需要理解和分析一个URL所具有的含义。
   例如对于下面这个URL：
   https://security.alibaba.com/announcement/announcement?spm=0.0.0.0.i9HwTE&id=45
   ①https://表示该网站使用https协议；
   ②security.alibaba.com表示该网站所有者的域名；
   ③/announcement/announcement表示所有者的域名下的文件（资产）
   ④?spm=0.0.0.0.i9HwTE&id=45表示以“？”作为起始符，后续内容
     皆为参数，每个参数之间以“&”作为连接符，参数以“=”作为赋
     值符。其中，第一个参数为spm，值为0.0.0.0.i9HwTE，第二个参
     数为id，值为45。

   ------

   而HTTP请求一般以数据包为介质。所以启动burpsuite开始抓包。![image-20230918122542750](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918122542750.png)

先把它发送到repeater，这样可以看到实时提交数据包后网站返回的数据包。

![image-20230918122718549](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918122718549.png)

添加变量a=1。

![image-20230918122740681](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918122740681.png)

然后点击send发送。

![image-20230918123953639](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918123953639.png)

得到新信息。![image-20230918124021165](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124021165.png)

所以我们要把GET改为POST，**但是**

		GET请求和POST请求的包格式是有不同之处的。主要体现在“传参”所在位置不同：GET请求的“传参”位处于开头“GET”之后的位置，而POST请求的“传参”位处于最后分段的最后一行。其余不同之处在于请求包的中间段，从GET请求到POST请求需要在中间段末尾行添加Content-Type: application/x-www-form-urlencoded这段语句。
![image-20230918124218631](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124218631.png)

再发送。

![image-20230918124230950](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124230950.png)

得到了key。

## 7.robots

![image-20230918124435611](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124435611.png)

首先我们要知道robots协议是什么。百度一下。![image-20230918124456393](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124456393.png)

里面提到了 **robots.txt文件**，所以我们可以通过浏览器访问这个文件。

先打开给的网址![image-20230918124617962](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124617962.png)

发现什么都没有。直接访问 robots.txt![image-20230918124640494](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124640494.png)

![image-20230918124649315](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124649315.png)

那么这个php文件再进行访问。![image-20230918124708078](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124708078.png)

## 8.backup

![](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918124955365.png)

打开之后

![image-20230918125028361](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918125028361.png)

这个很简单了，index.php.bak，直接访问。

![image-20230918125100916](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918125100916.png)

得到一个文件，通过vs code打开。

![image-20230918125120304](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230918125120304.png)

得到了key。

## 9.cookie

![image-20230919125224130](C:\Users\龚曦\AppData\Roaming\Typora\typora-user-images\image-20230919125224130.png)

![image-20230919125231524](C:\Users\龚曦\AppData\Roaming\Typora\typora-user-images\image-20230919125231524.png)

熟悉数据包的都知道，cookie是其中一项。不知道cookie没关系，上网搜索

![image-20230919125329004](C:\Users\龚曦\AppData\Roaming\Typora\typora-user-images\image-20230919125329004.png)

返回数据包中

![image-20230919125428947](C:\Users\龚曦\AppData\Roaming\Typora\typora-user-images\image-20230919125428947.png)

输入。

![image-20230919125520653](C:\Users\龚曦\AppData\Roaming\Typora\typora-user-images\image-20230919125520653.png)

F12查看返回数据包。

![image-20230919125538809](C:\Users\龚曦\AppData\Roaming\Typora\typora-user-images\image-20230919125538809.png)

## 10.disabled_button

![image-20230919182249630](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230919182249630.png)

![image-20230919182255545](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230919182255545.png)

既然和前端有关，那么直接按下F12

![image-20230919182336268](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230919182336268.png)

我们看到class前面有个disabled，直接删去就好。

![image-20230919182407354](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230919182407354.png)

然后flag可以点击了。

![image-20230919182422788](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230919182422788.png)

## 11.weak_auth

![image-20230919183155683](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230919183155683.png)

![image-20230919183202788](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230919183202788.png)

随便输入一个用户名，他告诉我们要以admin登录。

![](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230919183229732.png)

那用户名输入admin后，密码随便输入一个，然后打开burpsuite开始爆破，导入中国网民弱密码字典.php然后开始爆破查看数据包长度是否相同。我这里运气好，试了个123456就对了。

![image-20230919183352848](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230919183352848.png)

## 12.simple_php

![image-20230920123714650](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230920123714650.png)

![image-20230920123737151](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230920123737151.png)

首先进行代码审计。由代码可知要以GET方式提交两个变量a和b。

判断1：`if($a==0 and $a)`，这里要保证a==0且a为真
由于PHP中的`==`是弱类型比较，即**如果比较一个数字和字符串或者比较涉及到数字内容的字符串，则字符串会被转换成数值并且比较按照数值来进行**，由此我们可以令`a=0a`（后接任意字符或字符串均可）

判断2：`if(is_numeric($b))`，我们要令这句话不成立，否则会退出当前脚本，无法打印后续flag，和判断1相类似，只要b不是纯数字即可

**Tips：is_numeric() 函数用于检测变量是否为数字或数字字符串**

判断3：`if($b>1234)`，b要大于1234，结合判断2，b不能是纯数字,因此可令`b=1235a`（后接任意字符或字符串均可）

![image-20230920124038146](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230920124038146.png)

## 13.baby_web

![image-20230920124624421](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230920124624421.png)

![image-20230920124633609](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230920124633609.png)

初始页面一般都是index.php。但是我们输入后还是1.php，应该是重定向了。

这里需要知道一个知识点

![image-20230920124728976](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230920124728976.png)

打开F12，看下响应标头。

![image-20230920124855280](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230920124855280.png)

可以从时间线看到，确实先打开index.php后转到1.php，而且index.php的状态也是302。

由HTTP状态码可知重定向到1.php了。那我们看下index.php里有没有什么内容。![image-20230920125017004](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230920125017004.png)

## 14.easyphp

![image-20230924173017248](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230924173017248.png)

首先进行代码审计。

![image-20231021102755087](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231021102755087.png)

**isset()**函数函数用于检测变量是否已设置并且非 NULL。返回类型为bool类型。

**intval()** 函数用于获取变量的整数值。

所以这一行代码要求我们输入的a，被设置且不为NULL，其值大于6000000但字符长度要小于等于3。

那么我们可以用科学计数法，令a=1e9或更大。反正比6e6大就可以。

![image-20230924173448505](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230924173448505.png)

**substr(字符串，start，length)**函数。从一个字符串中从start截取length长度的子串。

此子串是否等于'8b184b'。md5($b)的意思就是b经过md5编码得到的字符串。

所以这里我们要找一个经过md5编码后最后六位是 8b184b 的明文。

那么这里只能用py写一个哈希爆破。

![image-20230924185121174](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230924185121174.png)

得到明文。

```python
import random
import hashlib

value = "8b184b"
while 1:
    plainText = random.randint(10 ** 11, 10 ** 12 - 1)#random.randint(start, stop)返回指定范围内的整数
    plainText = str(plainText)#将得到的整数转化为字符串
    MD5 = hashlib.md5()#初始化一个md5()实例对象
    MD5.update(plainText.encode(encoding='utf-8'))#然后通过update()方法，指定需要加密的字符串，别忘了要先进行encode编码，因为hashlib是对二进制进行加密的，所以需要encode将字符串转码为二进制格式。
    cipherText = MD5.hexdigest()#对指定需要加密的字符串进行MD5加密。得到密文。
    if cipherText[-6:] == value:#如果密文的最后六位等于value则
        print("碰撞成功:")
        print("密文为:" + cipherText)
        print("明文为:" + plainText)
        break
    else:
        print("碰撞中.....")
```

------

这里讲一下哈希的来历：

无限多转化为固定的这一过程称为Hashing，哈希。

哈希不可逆。

我们都知道数组是用索引来检索存储的数据。

索引不好记忆，如果我们将索引换成我们容易理解的，查找数据时，效率就很高了。

哈希表时用**键值对**的形式进行表示，python中的**字典**也是用哈希表实现的。

哈希表里的键可以是字符串或者整数，但是这个键不会直接对应相应的内存地址，这个键只是方便我们找到索引，要找到对应的内存地址，我们还需要对这个键进行运算，运算后得到的值就是内存地址。这个运算就是哈希函数。

哈希函数多种多样，但有基本原则：不可逆

比如现在要放USA这个键进入哈希表，那么对U、S、A分别进行ASCII转换并相加值后取余，得到一个个位数就是放入哈希表的键。这个过程就是哈希函数。

但是哈希函数有时候不同的输入会产生相同的输出，这种现象被称为**哈希冲突**或者**哈希碰撞**。

其中涉及到的数据存放会出现聚集现象，这里先不展开。

 哈希算法：这些算法可以把数据运算为固定的值，这个值称为摘要。

MD5系列输出固定128bits的摘要

SHA-256则是256bits

SHA-512则是512bits

------



![image-20230924183435254](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230924183435254.png)

再来看看这一段。

c需要传入一个json格式的字符串，is_numeric()函数就是检测变量是否为数字或数字字符串。is_array用来检测是否是一个**数组**。

![image-20230924184345063](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230924184345063.png)

​		**注意：这里的value是字符串才加引号！！！**

第一层if	其中键为m的值不能为数字，且要大于2022。前面我们说过字符串与整数作比较会被强行转化为数字。

第二层if	**count函数返回数组中元素的数目**，也就是说键为n的元素应该有两个，且第一个是数组

​				进入第二层if，这里可以看出 array_search函数找不到 "DGGJ" 就不能进入下一步，而foreach函数找不到 "DGGJ"才能进入下一步。

​				所以这里矛盾起来了，那么我们就要**绕过其中一个函数**，array_search函数是**可以绕过的**，当函数将字符串与数字进行匹配时，会将字符串强制转换为整型进行比较，"**DGGJ**"转化为整型为0

​		 		所以

```
c={"m":"5555a","n":"[["2"],0]"}
```

综上，url为

```
?a=1e9&b=282662388872&c={"m":"5555a","n":[["2"],0]}
```

![image-20230924185345698](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20230924185345698.png)

## 15.inget

提交数据的方式是GET，注入点的位置在GET参数部分。

xxx/xxx/xxx.php?id=1，id就是注入点。

![image-20231015143702736](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231015143702736.png)

开始简单的sql注入尝试。

输入

?id=1' and 1=1-- -

?id=1' and 1=2-- -

?id=1' or 1=2-- -

后发现均无回显。

使用万能密码。

```
"or "a"="a
')or('a'='a
or 1=1--
'or 1=1--
a'or' 1=1--
"or 1=1--
'or'a'='a
"or"="a'='a
'or''='
'or'='or'
1 or '1'='1'=1
1 or '1'='1' or 1=1
'OR 1=1%00
```

输入 id=1' or '1=1

后端会处理成 'id=1' or '1=1'。

我们知道or只要其中一个为真那么就为真。所以为真，通过。

后出现回显。

![image-20231015144231582](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231015144231582.png)

## 16.fileinclude

![image-20231015152011226](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231015152011226.png)

查看网站源码

![image-20231015152036084](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231015152036084.png)

可知，如果不传入language那么默认设置为english。

如果传入了language那么就是 language.php

所以我们要通过cookie方式传入language。

打开抓包软件

![image-20231015152219339](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231015152219339.png)

发现只有9行，没有cookie。那么自己手动添加一个。

![image-20231015152254417](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231015152254417.png)

name为language。

value为php://filter/read=convert.base64-encode/resource=**/var/www/html/flag**

php://filter/read=的用法请见[PHP: php:// - Manual](https://www.php.net/manual/zh/wrappers.php.php)

convert.base64-encode是以base64编码。

/var/www/html/题干中已经给了，我们可以知道flag在flag.php中。

所以将flag提交给源代码中的$lan中，读取经过base64编码过后的flag值。

我尝试过用utf-8编码，但是什么都没有。至于为什么要使用base64编码。我认为这个flag.php文件是二进制文件，而要将二进制文件转化为纯文本那么只能使用base64编码。

![image-20231015153335010](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231015153335010.png)

然后将所给密文进行base64解码。![image-20231015153401583](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231015153401583.png)

得到flag。

## 17.file_include

![image-20231105173649825](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231105173649825.png)

先试试base64等，发现被过滤了。

再试试string过滤器，发现string也被过滤。

而php有两种转换过滤器

一种是string过滤器

一种是convert过滤器

那么我们使用convert过滤器

![image-20231105174404101](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231105174404101.png)

而php支持的编码格式部分以下有

- UCS-4*
- UCS-4BE
- UCS-4LE*
- UCS-2
- UCS-2BE
- UCS-2LE
- UTF-32*
- UTF-32BE*
- UTF-32LE*
- UTF-16*
- UTF-16BE*
- UTF-16LE*
- UTF-7
- UTF7-IMAP
- UTF-8*
- ASCII*
- EUC-JP*
- SJIS*
- eucJP-win*
- SJIS-win*
- ISO-2022-JP
- ISO-2022-JP-MS
- CP932
- CP51932
- SJIS-mac（别名：MacJapanese）
- SJIS-Mobile#DOCOMO（别名：SJIS-DOCOMO）
- SJIS-Mobile#KDDI（别名：SJIS-KDDI）
- SJIS-Mobile#SOFTBANK（别名：SJIS-SOFTBANK）
- UTF-8-Mobile#DOCOMO（别名：UTF-8-DOCOMO）
- UTF-8-Mobile#KDDI-A
- UTF-8-Mobile#KDDI-B（别名：UTF-8-KDDI）
- UTF-8-Mobile#SOFTBANK（别名：UTF-8-SOFTBANK）
- ISO-2022-JP-MOBILE#KDDI（别名：ISO-2022-JP-KDDI）

将以上格式编辑成一个txt文本。然后导入bp变量列表。

![image-20231105174624456](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231105174624456.png)

![image-20231105174757161](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231105174757161.png)

发现长度不同的里面没有flag

那么看一下是不是在flag.php中。

![image-20231105175323354](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231105175323354.png)

继续爆破

![image-20231105175336285](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231105175336285.png)

得到flag

## 18.fileclude

![image-20231105190423414](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231105190423414.png)

文件包含漏洞位于file1与file2两个变量中。其中，file2被放入了file_get_contents函数中，并要求返回值为hello ctf，我们可以用php://input来绕过；而file1被放入include函数中，并且根据题目提示，我们应该获取当前目录下flag.php的文件内容。因此我们可以使用php://filter伪协议来读取源代码。最终可以得到flag.php经过Base64编码后的结果

构造URL后，在火狐中

![image-20231105191125924](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231105191125924.png)

因为绕过后还要输入满足if，所以在post data上添加 hello ctf

即可得到base64编码的flag，然后解码。

![image-20231105191251920](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231105191251920.png)

# 二.难度2

## 1.web2

![image-20231113141314833](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231113141314833.png)

代码审计一下。

miwen是经过加密后的密文，encode函数就是加密过程。

strrev函数可以反转字符串，所以明文经过反转后，再进入for。

对后生成的字符串中的每个字符，获取其ASCII值，加1，然后将结果转换回字符，并连接到一个新的字符串中。

对得到的字符串进行Base64编码，再次出现，最后应用ROT13加密。

那我们逆向思维，只要先解密rot13，base64解码，对字符串中的每个字符的ASCII-1再转换成字符再反转就是明文。

本来想让gpt审计 代码的，结果它直接给你写出解密脚本了。

![image-20231113143239037](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231113143239037.png)

运行了一下，有一点小问题，就是它反转了两次，我们只需要去掉最外面的strrev就可以了。

![image-20231113143335741](https://tuchuang1-1.oss-cn-beijing.aliyuncs.com/D:/picgo/image-20231113143335741.png)

得到flag。
