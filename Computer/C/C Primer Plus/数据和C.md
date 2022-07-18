# 数据和C

## 3.1 示例程序

```c
#include<stdio.h>
int main(void)
{
    float weight;  //你的体重
    float value;  //相等重量的白金价值

    printf("Are you worth your weight in platinum?\n");
    printf("Let's check it out.\n");
    printf("Please enter your weight in pounds:");

    /*获取用户的输入 */
    scanf("%f",&weight);
    /*假设白金的价格是每蛊司$1700 */
    /*14.5833用于把英镑常衡蛊司转换为金衡蛊司 */
    value = 1700.00 * weight *14.5833;
    printf("Your weight in platinum is worth $%.2f.\n",value);
    printf("You are easily worth that! If platinum prices drop,\n");
    printf("eat more to maintain your value.\n");

    return 0;
}
```

#### 程序调整
需要调用两次getchar()函数:  
```c
getchar();
getchar();
```  

getchar()函数读取下一个输入字符，因此程序会等待用户输入。在这种情况下，输入156并按下**Enter(或Return)** 键(发送一个换行符)，然后scanf()读取键入的数字，第1个getchar()读取换行符，第2个getchar()让程序暂定，等待输入  

### 3.1.1 程序中的新元素
- 注意，代码中使用了一种新的变量声明。前面的例子中只使用了**整数类型的变量(int)**，但是本例中使用了**浮点数类型(float)的变量**，以便处理更大范围的数据。**float类型可以存储带小数的数字**
- 为了打印新类型的变量，**在printf()中使用%f来处理浮点值。%.2f中的.2用于精确控制输出，指定输出的浮点数只显示小数点后两位**
- scanf()函数用于读取键盘的输入。%f说明scanf()要读取用户从键盘输入的浮点数，&weight告诉scanf()把输入的值赋给名为weight的变量。scanf()函数使用&符号表明找到weight变量的地点
- **scanf()函数读取用户从键盘输入的数据，并把数据传递给程序;printf()函数读取程序中的数据，并把数据显示在屏幕上。**
  
## 3.2 变量与常量数据
**有些数据类型在程序使用之前已经预先设定好了，在整个程序的运行过程中没有变化，这些称为常量(constant)。其他数据类型在程序运行期间可能会改变或被赋值，这些成为变量(variable)。**

## 3.3 数据：数据类型关键字
不同的数据类型之间也有差异。一些数据类型表示数字，一些数据类型表示字母(字符)。C通过识别一些基本的数据类型区分和使用这些不同的数据类型。如果数据是常量，编译器一般通过用户书写的形式来识别类型(如，42是整数，42.100是浮点数)。**对变量而言，要在声明时指定其类型**。

**C语言的数据类型关键字**

|最初K&R给出的关键字|C90标准添加的关键字|C99标准添加的关键字|
|----|----|----|
|int|signed|_Bool| 
|long|void|_Complex|
|short||_Imaginary|
|unsigned|||
|char|
|float|
|double|  


在C语言中，<font color=red >用int关键字来表示基本的整数类型。</font>后3个关键字(long、short和unsigned)和C90新增的signed用于提供基本整数类型的变式，例如`unsigned short`和`long long int`。<font color = red>char关键字用于指定字母和其他字符</font>(如，#、$、%和*)。<font color = red>char类型也可以表示较小的整数。</font>float、double、和long double表示带小数点的数。Bool类型表示布尔值(true或false)，_Complex和 _Imaginary分别表示复数和虚数  
<font color = red>按计算机的存储方式可分为两大基本类型：整数类型和浮点数类型。</font>

#### 位、字节和字
位、字节和字是描述计算机数据单元或存储单元的术语、这里主要指存储单元  
<font color = red>最小的存储单元是位(bit)，可以存储0或1(或者说，位用于设置“开”或“关”)</font>  
字节(byte)是常用的计算机存储单位，**1字节均为8位**。1位可以表示0或1，那么8位字节就有256(2的8次方)种可能的0、1组合。  
字(word)是设计计算机时给定的自然存储单位。**计算机的字长越大，其数据转移越快，允许的内存访问也更多  

### 3.3.1 整数
**整数：没有小数部分的数**  
例如，2，-23和2456都是整数，计算机已二进制数字存储整数  

### 3.3.2 浮点数
浮点数与数学中实数的概念差不多。2.75、3.16E7、7.00和2e-8都是浮点数。<font color = red>注意，在一个值后面加上一个小数点，该值就成为一个浮点值。</font>。**7是整数，7.00是浮点数**。3.16E7表示$3.16 *10^7$(3.16乘以10的7次方)  

两种类型的实际区别：  
- 整数没有小数部分，浮点数有小数部分
- 浮点数可以表示的范围比整数大
- 对于一些算术运算(如，两个很大的数相减)，浮点数损失的精度更多
- 计算机的浮点数不能表示区间内所有的值。浮点数通常只是实际值的近似值  

## 3.4 C语言基本数据类型

### 3.4.1 int类型
int类型是有符号整型，即int类型的值必须是整数(正整数，负整数或0)。一般而言，存储一个int要占用一个机器字长。**ISO C规定int的取值范围最小为-32768~32767**。一般而言，系统用一个特殊位的值表示有符号整数的正负号。  
#### 1.声明变量
```c
int erns;  
int hogs,cows,goats;  
```
int +变量名;  
要声明多个变量，可以单独声明每个变量，或者在int后面列出多个变量名，变量名之间用逗号隔开。  

**获取值的两种途径**
- 第一种途径是赋值：`cows = 112;`  
- 第二种途径是，通过函数(如，`scanf()`)获得值  

#### 2.初始化变量
<font color = red>初始化(initialize)变量就是为变量赋一个初始值</font>  
在C语言中，初始化可以直接在声明中完成。  
```c
int hogs = 21;
int cows = 32, goats = 14;
int dogs ,cats = 94; /*有效，但是这种格式很糟糕*/
```

#### 3.int类型常量
上面示例中出现的整数(21、32、14和94)都是整型常量或整型字面量。C语言把不含小数点和指数的数作为整数。C语言把大多数整型常量视为int类型，但是非常大的整数除外。

#### 4.打印int值
可以使用`printf()`函数打印`int类型`的值,**`%d`指明了一行中打印整数的位置。`%d`称为转换说明**，它指定了printf()应使用什么格式来显示一个值。格式化字符串中的每个%d都与待打印变量列表中相应的int值匹配。  
```c
/* printl.c - 演示printf()的一些特性 */
#include<stdio.h>
int main(void)
{
    int ten = 10;
    int two =2;

    printf("Doing it right: ");
    printf("%d minus %d is %d\n",ten,2,ten-two);
    printf("Doing it wrong: ");
    printf("%d minus %d is %d\n",ten); //遗漏2个参数

    return 0;
}
```
编译并运行该程序，输出如下：
```c
Doing it right: 10 minus 2 is 8
Doing it wrong: 10 minus 16 is 1650287143
```

#### 5. 八进制和十六进制
0x或0X前缀表示十六金子值，所以十进制数16表示成十六进制是0x10或0X10  
0前缀表示八进制，十进制数16表示成八进制是020  
**无论把数字写成16，020或0x10，存储该数的方式都相同，因为计算机内部都以二进制进行编码**

#### 6.显示八进制和十六进制
**不同的进制要使用不同的转换说明**，以十进制显示数字，使用`%d`;以八进制显示数字，使用`%o`;以十六进制显示数字，使用`%x`。另外，要显示各进制数的前缀0、0x和0X，必须分别使用`%#o、%#x、%#X`

```c
/* bases.c --以十进制、八进制、十六进制打印十进制数100 */
#include<stdio.h>
int main(void)
{
    int x = 100;

    printf("dec = %d; octal = %o; hex = %x\n",x,x,x);
    printf("dec = %d; octal = %#o; hex = %#x\n",x,x,x);

    return 0;
}
```
编译并运行该程序，输出如下：
```c
dec = 100; octal = 144; hex = 64;
dec = 100; octal = 0144; hex = 0x64;
```

### 3.4.2 其他整数类型
C语言提供3个附属关键字修饰基本整数类型：`short、long、unsigned`  
- `short int`类型(或者简写为short)占用的存储空间可能比`int`类型少,常用于较小数值的场合以节省空间。与int类似，short是有符号类型
- `long int`或`long`占用的存储空间可能比`int`多，适用于较大数值的场合。与int类似，long是有符号类型
- `long long int`或`long long`占用的存储空间可能比long多，适用于更大数值的场合。该类型至少占64位。与int类似，long long是有符号类型
- `unsigned int`或`unsigned`只用于非负值的场合，这种类型与符号类型表示的范围不同。例如：16位`unsigned int`允许的取值范围是0-65535，而不是-32768-32767.用于表示正负号的位现在用于表示另一个二进制位，所有无符号整型可以表示更大的数
- 在任何有符号类型前面添加关键字`signed`，可强调使用有符号类型的意图。例如，`short、short int、signed short、signed short int`都表示同一种类型

#### 1. 声明其他类型
```c
long int estine;
long johns;
short int erns;
short ribs;
unsigned int s_count;
unsigned players;
unsigned long headcount;
unsigned short yesvotes;
long long ago;
```

#### 2.使用多种整数类型的原因
