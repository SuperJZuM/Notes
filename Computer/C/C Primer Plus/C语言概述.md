# C语言概述

## 2.1 简单的C程序
```c
#include<stdio.h>
int main(void)
{
    int num;        //定义一个名为num的变量
    num = 1;        //为num赋一个值

    printf("I am a simple");//使用printf()函数
    printf("computer.\n");
    printf("My favorite number is &d because it is first.\n",num);

    return 0;
}
```

### 分析

#### 1. #include指令和头文件

`#include<stdio.h>` &larr; 包含另一个文件  
它的作用相当于把stdio.h文件中的所有内容都输入该行所在的位置  
 #include这行代码是一条**C预处理器指令**，通常C编译器在编译前会对源代码做一些准备工作，即预处理  
 所有的C编译器软件包都提供stdio.h文件。该文件中包含供编译器使用的输入和输出函数（如，printf()）信息。**该文件名的含义是标准输入/输出头文件**  
 **头文件（header）：在C程序顶部的信息集合被称为头文件**  
 **#include中的#符号表明，C预处理器会在编译器接手之前处理这条指令**

#### 2. main()函数
`int  main(void)` &larr; 函数名  
C程序一定从main()函数开始执行，圆括号用于识别main()是一个函数
C程序包含一个或多个函数，它们是C程序的基本模块。圆括号表面main()是一个函数名。  
**int是main()函数的返回类型，int表明main()函数返回一个整数，返回给操作系统。void表明main()不带任何参数**

#### 3. 注释
`/*一个简单的C程序*/` &larr;注释
注释在/*和 */之间，提高程序可读性。**注释只是为了帮助读者理解程序，编译器会忽略它们**  
`//` &larr; 单行注释

#### 4. 花括号、函数体和块
```c
{
    ...   
}
```
左花括号表示函数定义开始，右花括号表示函数定义结束  
**花括号还可用于把函数中的多条语句合并为一个单元或块**

#### 5. 声明（declaration）
`int num;` &larr; 声明  
在函数中有一个名为num的变量（variable），int表明num是一个整数。int是一种数据类型。分号在C语言中是大部分语句和声明的一部分  
int是C语言的一个**关键字（keyword）**,表示一种基本的C语言数据类型。  
num是一个**标识符（identifier)**,也就是变量、函数和其他实体的名称  
**在C语言中，所有变量都必须先声明才能使用**  
**数据类型**：C语言可以处理多种类型的数据，如整数、字符、浮点数。把变量声明为整型或字符类型，计算机才能正确地存储、读取和解释数据  
**命名：可以用小写字母、大写字母、数字和下划线（_）来命名。名称的第一个字符必须是字母或者下划线不能是数字**，C语言的名称区分大小写

#### 6. 赋值 
`num = 1;` &larr; 赋值表达式语句  
把值1赋给名为num的变量  
**该赋值表达式语句从右侧把值赋给左侧，语句以分号结尾**

#### 7. printf()函数
```c
    printf("I am a simple")；
    printf("computer.\n");
    printf("My favorite number is %d because it is first.\n",num);
```
圆括号表明printf是一个函数名
**实际参数是传递给函数的特定值；形式参数是函数用于存储的变量**  
**\n代表一个换行符（newline character）**，代码\n告诉计算机另起一行，即把光标移至下一行  
**换行符是一个转义序列（escape sequence）**，转义序列用于代表难以表述或无法输入的字符。每个转义序列都以反斜杠（\）开始  
参数中的%d被数字1替代了，而1就是变量num的值。**%d相当于是一个占位符，其作用指明输出num值的位置**
**%提醒程序，要在该处打印一个变量，d表明把变量作为十进制整数打印**

#### 8. return 语句
`return 0;`  
在C语言中，return语句是一种跳转语句
C函数可以给调用放提供（或返回）一个数。目前可暂时看作是结束main()函数的要求

## 2.2 简单程序的结构
程序由一个或者多个函数组成，必须由main()函数。**函数由函数头和函数体组成**。函数头包含函数名、传入该函数的信息类型和函数的返回类型。函数体被花括号括起来，由一系列语句、声明组成。  

## 2.3 进一步使用C

```c
//把2英寻转换成英尺
#include<stdio.h>
int main(void)
{
    int feet, fathoms;
    
    fathoms = 2;
    feet = 6 * fathoms;
    printf("There are %d feet in %d fathoms!\n",feet,fathoms);
    printf("Yes,I said %d feet!\n",6 * fathoms);
    
    return 0;
}
```

### 分析

#### 多条声明

程序在一条声明中声明了两个变量，而不是一个变量。要在声明中用逗号隔开两个变量（feet和fathoms）  
`int feet, fathoms;`  
和  
`int feet;`  
`int fathoms;`  
等价

#### 乘法

*表示乘法  
`feet = 6 * fathoms;`的意思是“查找变量fathoms的值，用6乘以该值，并把计算结果赋给变量feet”

#### 打印多个值

```c
输出结果是：
    There are 12 feet in 2 fathoms!
    Yes,I said 12 feet!
```

第一个printf()中进行了两次替换，双引号后面的第一个变量（feet）替换了双引号中的第1个%d；双引号后面的第2个变量（fathoms）替换了双引号中的第2个%d。**待输出的变量列于双引号后面，变量之间要用逗号隔开**

## 2.4 多个函数

 ```c
 //一个文件中包含两个函数
 #include<stdio.h>
 void butler(void);//ANSI/ISO C函数原型
 int main(void)
 {
     printf("I will summon the butler function.\n");
     butler();
     printf("Yes.Bring me some tea and writeable DVDs.\n");
     
     return 0;
 }
 void butler(void) //函数定义开始
 {
     printf("You rang,sir?\n");
 }
 ```

```c
该程序输出结果如下：
    I will summon the butler function.
    You rang,sir?
    Yes.Bring me some tea and writeable DVDs.
```

`butler()`函数被调用了三次。第一次是函数原型（prototype），告知编译器在程序中要使用该函数；第2次是以函数调用（function call）的形式出现在main()中；最后一次出现在函数定义（function definition）中；**函数定义即是函数本身的源代码**  
函数原型是一种声明形式，告知编译器正在使用某函数，因此函数原型也被称为**函数声明（function declaration）**  
**注意：何时执行butler()函数取决于它在main()中被调用的位置，而不是butler()的定义在文件中的位置。无论main()在程序文件中处于什么位置，所有的C程序都从main()开始执行**

## 2.5 调试程序

程序的错误通常叫作bug，找出并修正错误的过程叫作**调试（debug）**

```c
//有错误的程序
#include<stdio.h>
int main(void)
(
    int n,int n2,int n3; 
    
 	/*该程序有多处错误
    n = 5;
    n2 = n * n;
    n3 = n2 * n2;
    printf("n = %d, n squared = %d, n cubed = %d\n",n,n2,n3)
    
    return 0;
)
```

#### 语法错误

**C语言的语法错误指的是，把有效的C符号放在错误的地方**   

1. main()函数体使用圆括号代替花括号。这就是把C符号用错了地方

2. 变量声明应该这样写:
   `int n, n2 ,n3;`
   或者：

   ```c
   int n;
   int n2;
   int n3;
   ```

3. main()中的注释末尾漏掉了`*/`（另一种修改方案是，用//替换/*）

4. printf()语句末尾漏掉了分号        

#### 语义错误

**语义错误是指意思上的错误**

`n3 = n2 * n2;`

此处，n3愿意表示n的3次方，但是代码中的n3被设置成了n的4次方（n2 = n * n）  
**程序无法检测语义错误，因为这类错误并未违反C语言的规则

## 2.6 关键字和保留标识符

<center>ISO C关键字</center>

| auto  | extern | short | while |
| -----| ------ | ----- | ----- |
| break | float | signed | _Alignas |
| case | for | sizeof | _Alignof |
| char | goto | static | _Atomic |
| const | if | struct | _Bool |
| continue | inline | switch | _Complex |
| default | int | typedef | _Generic |
| do | long | union | _Imaginary |
| double | register | unsigned | _Noreturn |
| else | restrict | void | _Static_assery |
| enum | return | volatile | _Thread_local |

**关键字是C语言的词汇。不能用它们作为标识符（如，变量名）。许多关键字用于指定不同的类型，如int**  
**保留标识符（reserved identifier)包括那些以下划线字符开头的标识符和标准库函数名，如printf()**
