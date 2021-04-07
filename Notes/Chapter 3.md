# Chapter 3

#### 命名空间

using声明：

```c++
//格式如下：
using namespace::name;

//示例
using std::cin;
using std::cout;
```

using指示

```c++
//格式
using namespace name;

//示例
using namespace std;
```

<font color=red>**注意：避免使用using指示**</font>



#### 标准库类型String

- 初始化方法：

```c++
string s1;
string s2 = s1;
string s2(s1);
string s3 = "String Value";
string s3("String Value");
string s4(3, 'c')			//s4 == "ccc"
```



- 读操作（cin >> ）：

  忽略两端空白，即忽略开头空白，从一个非空白字符读取，遇到空白后结束



- 整行读取 getline()

```c++
//格式
string s;
getline(cin, s);
```

读取整行，换行符结束。换行符也被读取了，但并未存入string，而是丢弃了。




- string运算

  <, <=, >, >=, ==, !=, +=, +

  string相加，表达式可以含有字符串字面值，字符，但每个加法运算符都要有一个string对象。

  <font color=red>**字符串字面值与string是不同类型**</font>

  

- 范围for语句（range for）

```c++
//格式
for (declaration : expression)
    statement

//示例
string s = "Hello world!";
for (auto c : s)
    cout << c << endl;
```

<font color=red>**涉及到string大小，最好使用string::size_type类型**</font>



#### 标准库类型Vector

- 模板本身不是类或函数，其根据额外提供的信息进行实例化。
- 信息提供方式：模板名<额外信息>
- vector不能包含引用类型，因为引用不是对象。
- 早期的C++标准中vector<vector<int>>需写成vector<vector<int> >，及两个右括号间需要空格。

```c++
vector<vector<int>>		//早期版本C++编译错误，新版本编译成功
vector<vector<int> >	//早期版本规定格式
```



-  <font color=red>range for循环体内禁止改变其所遍历序列的大小，例如：</font>

```c++
//错误示例
//可以编译运行，但会出错
vector<int> vint = {1,2,3};
for (auto v : vint)
{
    auto.push_back(v);
}
```



- <font color=red>任何可能改变vector对象容量的操作，都会使该vector对象的迭代器失效</font>



#### 数组

- 数组的维度（大小）必须是常量表达式

```c++
int length = 10;
int a[length];		//不符合c++标准语法，但可以编译通过，原因在于编译器扩展 
```



- 定义数组时，不支持auto
- 不存在引用的数组

```c++
int &refs[10] = {...};		
//错误，数组元素因为对象，不存在引用的数组
```



- 复杂数组的声明

  <font color=red>阅读顺序：**由里到外，从右向左**</font>

```c++
int *ptrs[10];					//ptrs是长度为10，类型为整型指针（int*）的数组
int &refs[10] = /*.....*/;		//错误，不支持引用的数组
int (*pArray)[10] = &arr;		//pArray是一个指针，指向长度为10，类型为int的数组
int (&arrRef)[10] = arr;		//arrRef是一个引用，绑定长度为10，类型为int的数组
```

