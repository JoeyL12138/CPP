# Chapter 4

#### 逻辑与关系运算符

- 判别式尽量使用如下格式，：

```c++
if (val) {//pass}
if (!val) {//pass}
    
//不要将非布尔值直接与布尔值进行比较
if (val == true) {//pass}
```



#### 赋值与递增递减运算符

- 赋值运算满足右结合律
- <font color=red>尽量使用前置递增递减运算符，即（++i；--i；），P132</font>



- 常用写法：

```c++
auto iter = v.begin();
while (iter != v.end())
{
	cout << *iter++ << endl;		//
}
```



#### 条件运算符

- *cond ? expr1 : expr2 ;*

- 可以嵌套，满足 **右结合律**



#### 位运算符(P.137)

```c++
位与：&，位或：|，位反：~
左移：<< 右移：>>    
```

- 移位运算符满足左结合律



#### 逗号运算符

- 返回的结果为右侧表达式的值



#### 显式类型转换

- 格式： cast-name<type> (expression);

  cast-name：static_cast，const_cast，



- <font color=red>**尽量避免使用强制类型转换**</font>

