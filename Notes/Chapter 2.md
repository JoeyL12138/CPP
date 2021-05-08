# Chapter 2

#### 声明与定义

声明：在变量前添加关键字extern，且不要显式的声明初始化变量。**包含初始化的声明即成为定义。**

```c++
extern int a; // 声明一个全局变量 a
int a; // 定义一个全局变量 a
extern int a =0 ; // 定义一个全局变量 a 并给初值。
int a =0;    // 定义一个全局变量 a, 并给初值，
```

<font color=red>声明可以多次，定义只能一次</font>

在多个文件之间共享const对象，必须在变量的定义之前添加extern。



#### 指向常量的指针与指向常量的引用

通常情况下，指向常量的指针与指向常量的引用必须与其所指类型一致。但是指向常量的指针与指向常量的引用可以指向非常量对象。

<font color=red>**指向常量的指针和引用不过是”自以为是“罢了，是一种对自我的约束。**</font>



#### 指向常量的指针与常量指针

```c++
//指常量的指针
const double pi = 3.14;
const int *p = &pi;

//常量指针
double x = 1.21;
double *const p = &x;

//指向常量的常量指针
const double *const p = &pi;
```



#### 顶层const与底层const

顶层const表示对象本身不可修改

```c++
//顶层const
const int i = 0;
double = pi = 3.14;
double *const p = &pi;

//底层const
const int *p = &i;
```

  <font color=red>constexpr是顶层const</font>

```c++
constexpr int *p = &i;
等价于int *constexpr p = &i;
```



#### 为什么C++中常量引用可以绑定非常量的对象、字面值和一般表达式

[https://blog.csdn.net/Colsum/article/details/79095462](https://blog.csdn.net/Colsum/article/details/79095462)



#### 处理类型

##### 1.类型别名

```c++
typedef int count;
typedef count base, *p;

//c++11
using count = int;
```

<font color=red>**注意：**</font>

```c++
typedef char *pstring;

const pstring cstr = 0;
//等价于
char *const cstr = 0; 	//正确
//直接用文本替换是一种错误的理解：
const char *cstr = 0; 	//错误
```



#### 预处理器

```c++
//防止头文件重复包含
#ifndef SALES_DATA_H
#define SALES_DATA_H
#include <string>
.......
   
#endif
```



#### void* 指针

void* 指针可以存放任意对象的指针，但不能直接操作void* 指针所指的对象。

从内存的角度来看，void* 仅仅是指向了一块内存空间，无法访问内存空间中的内容。