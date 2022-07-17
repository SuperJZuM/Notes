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

**<p align="center">C语言的数据类型关键字</p>**

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
