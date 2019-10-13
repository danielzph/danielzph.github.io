---
layout: post
title: c++函数
date: 2019-09-10
tags: c++语言学习笔记
---

说明：本系列博客用来记录在学习c++语言时的笔记，便于与同学相互之间的学习讨论。（注：笔记会记录我学习过程中的重难点，不包括学习的所有知识点。）

## 1. 函数的定义

```

类型说明符     函数名（含类型说明的形参表）

{

​	语句序列

}

```

## 2. 函数的调用

### 2.1 调用函数需要先声明函数类型

若函数定义在调用点之前，可以不另外声明；

若函数定义在调用点之后，必须要在调用函数前声明函数原型：

函数原型：类型标识符 被调用函数名（含类型说明的形参表）

### 2.2 一般调用 

```

#include <iostream>

using namespace std;

//计算x的n次方

double power(double x, int n) {

double val = 1.0;

while (n--) val *= x;

return val;

}


int main() {

cout << "5 to the power 2 is "
<< power(5, 2) << endl;

return 0;

}

```

### 2.3 嵌套调用

嵌套调用：在一个函数的函数体中，调用另一函数。

```

//求两个数平方和
#include <iostream>
using namespace std;

int fun2(int m){
    return m*m;
}

int fun1(int x, int y){
    return fun2(x)+fun2(y);
}

int main(){
    int a, b;
    cout<<"请输入两个数：";
    cin>>a>>b;
    cout<<"它们的平方和为："<<fun1(a,b)<<endl;
    return 0;
}


```

### 2.4 递归调用

 函数直接或间接地调用自身，称为递归调用。

```

//求n的阶乘
#include <iostream>
using namespace std;

unsigned fac(unsigned n){
    unsigned f;
    if (n==0)
        f=1;
    else
        f=fac(n-1)*n;
    return f;
}
int main(){
    unsigned n;
    cout<<"输入一个正整数：";
    cin>>n;
    unsigned y=fac(n);
    cout<<n<<"!="<<y<<endl;
    return 0;
}

```

### 2.5 参数传递

#### 2.5.1 值传递     

值传递为**单项传递**

例子：交换xy的值

```

#include <iostream>
using namespace std;

void swap (int a, int b){
    int t = a;
    a=b;
    b=t;
}
int main(){
    int x=5, y=10;
    cout << "x="<<x<<"    y="<<y<<endl;
    swap(x,y);
    cout << "x="<<x<<"    y="<<y<<endl;
    return 0;
}  


```

输出：   

```
x=5    y=10
x=5    y=10

```

我们可以看出，x、y的值并没有交换，因为值传递在传递时传递的是实参的值，形参的改变对实参没有影响。

#### 2.5.2 引用传递 

引用传递为**双向传递**


```

#include <iostream>
using namespace std;

void swap (int &a, int &b){
    int t = a;
    a=b;
    b=t;
}
int main(){
    int x=5, y=10;
    cout << "x="<<x<<"    y="<<y<<endl;
    swap(x,y);
    cout << "x="<<x<<"    y="<<y<<endl;
    return 0;
}

```

输出：  

```

x=5    y=10
x=10    y=5

```

### 2.5 函数重载

两个以上的函数具有相同的函数名，但是形参的个数或者类型不同，编译器根据实参和形参的类型及个数的最佳匹配，自动确定调用哪一个函数，这就是函数的重载。

### 2.6 c++系统函数

c++的系统库中提供了几百个函数可以供程序员使用。例如：平方根函数（sqrt）、绝对值函数（abs）。   
只需要用include指令嵌入相应的头文件，就可以使用系统函数。如数学函数，只需在开头写：

```

#include <cmath>

```






<br>

转载请注明：[张鹏辉的博客](http://danielzph.github.io) >> [c++ 函数](https://danielzph.github.io/2019/10/cpplearningprocess3_5/)





