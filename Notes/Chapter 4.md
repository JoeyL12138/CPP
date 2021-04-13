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

- 