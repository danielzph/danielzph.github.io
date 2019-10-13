---
layout: post
title: c++简单程序设计(二)
date: 2019-08-31
tags: c++语言学习笔记
---

说明：本系列博客用来记录在学习c++语言时的笔记，便于与同学相互之间的学习讨论。（注：笔记会记录我学习过程中的重难点，不包括学习的所有知识点。）

### C++简单程序设计（二）
#### 1,数据的输入和输出
(1)I/O流
在C++中，将数据从一个对象到另一个对象的流动抽象为“流”。流在使用前要被建立，使用后要被删除。数据的输入与输出是通过I/O流来实现的，cin和cout是预定义的流类对象。cin用来处理标准输入，即键盘输入。cout用来处理标准输出，即屏幕输出。从流中获取数据的操作称为提取操作，向流中添加数据的操作称为插入操作。

(2)预定义的插入符和提取符
“<<”是预定义的插入符，作用在流类对象cout上便可以实现项标准输出设备输出。
cout << 表达式 << 表达式...
标准输入是将提取符作用在流类对象cin上。
cin >> 表达式 >> 表达式...
提取符可以连续写多个，每个后面跟一个表达式，该表达式通常是用于存放输入值的变量。例如：
int a, b;
cin >> a >> b;

(3)常用的I/O流类库操纵符
<br />
![](/images/posts/cpp_learning_process/13.png)

#### 2，选择结构
(1)if语句
<br />
![](/images/posts/cpp_learning_process/14.png)

(2)switch语句
<br />
![](/images/posts/cpp_learning_process/15.png)
例子：


```c++

#include <iostream>

using namespace std;

int main() {
   
  int day;

     cin >> day;

     switch (day) {

     case 0: cout << "Sunday" << endl; break;

     case 1: cout << "Monday" << endl; break;

     case 2: cout << "Tuesday" << endl; break;

     case 3: cout << "Wednesday" << endl; break;

     case 4: cout << "Thursday" << endl; break;

     case 5: cout << "Friday" << endl; break;

     case 6: cout << "Saturday" << endl; break;

     default:

        cout<<"Day out of range Sunday .. Saturday"<< endl;   break;

     }

     return 0;
}

```

#### 3,循环结构


(1) while语句   
语法形式： while(表达式)语句   
执行顺序： 先判断表达式的值，若为 true 时，执行语句。   






<br>

转载请注明：[张鹏辉的博客](http://danielzph.github.io) >> [c++简单程序设计(二)](https://danielzph.github.io/2019/08/cpplearningprocess3/)








