---
layout: post
title: c++类与对象
date: 2019-10-10
tags: c++语言学习笔记
---

说明：本系列博客用来记录在学习c++语言时的笔记，便于与同学相互之间的学习讨论。（注：笔记会记录我学习过程中的重难点，不包括学习的所有知识点。）

## 类与对象
### 1. 面向程序设计的基本特点

#### 1.1 抽象

对同一类对象的共同属性和行为进行概括，形成类。抽象主要包括两个方面：**数据抽象**和**功能抽象**。

```c++

int hour, int minutu,int second //数据抽象

showTime(), setTime() //功能抽象

```

#### 1.2 封装

将抽象出的数据、代码封装在一起，形成类。clock、{、}、public、private

#### 1.3 继承

在已有类的基础上，进行扩展形成新的类。

#### 1.4 多态

同一名称，不同的功能实现方式。

### 2. 类与对象 

**类是面向对象程序设计的核心**。

#### 2.1 类的定义

```

class 类名称

{

   public:      公有成员（外部接口）

   private:     私有成员 (只允许本类中的函数访问，而类外部的任何函数都不能访问。)

   protected:   保护型成员

};

```

#### 2.2 对象

**表示该类的某一特定实体**

声明形式：  *Clock myCLOCK*  (类名 对象名)

访问数据成员的一般形式：  *myClock.showTime()* (对象名.数据成员名)

#### 2.3 类的成员函数

**表示类的行为**

1) 成员函数的实现

```

返回值类型 类名：：函数成员名（参数表）
{
	函数体
}

```

2) 例子

```

#include <iostream>
using namespace std;

class Clock{       //时钟类的定义

public:            //外部接口
    void setTime(int newH=0, int newM=0, int newS=0);
    void showTime();

private:          //私有数据成员
    int hour,minute,second;

};

//时钟类函数的实现
void Clock::setTime(int newH, int newM, int newS) {
    hour = newH;
    minute = newM;
    second = newS;
}

inline void Clock::showTime() {
    cout<<hour<<":"<<minute<<":"<<second<<endl;
}

//主函数
int main(){
    Clock myClock;    //定义对象myClock
    cout<<"First time set and output:"<<endl;
    myClock.setTime();
    myClock.showTime();
    cout<<"Second time set and output:"<<endl;
    myClock.setTime(22,10,30);
    myClock.showTime();
    return (0);
}

```

### 3. 构造函数和析构函数

#### 3.1构造函数的作用
 
  **在对象被创建时利用特定的值构造对象，将对象初始化为一个特定的状态**。

#### 3.2构造函数的形式

  函数名与类名相同；

  不能定义返回值类型，也不能有return语句；

  可以有形式参数，也可以没有形式参数；

  可以是内联函数；

  可以重载；

  可以带默认参数值

#### 3.3析构函数

  **完成对象被删除前的一些清理工作。**

  例子：

```

#include 
using namespace std;
class Point {     
public:
  Point(int xx,int yy);
  ~Point();
  //...其他函数原型
private:
  int x, y;
};

```

### 4.类的组合

#### 4.1组合的概念

类中的成员是另一个类的对象。

可以在已有抽象的基础上实现更复杂的抽象。

#### 4.2类组合的构造函数设计

**声明形式：**

```

类名::类名(对象成员所需的形参，本类成员形参)

:对象1(参数)，对象2(参数)，......

{

//函数体其他语句

}

```

**类组合的例子**

```

#include <iostream>
#include <cmath>      //数学函数
using namespace std;

class Point{          //Point 类定义
public:
    Point(int xx=0, int yy=0){      // 构造函数
        x=xx;
        y=yy;
    }
    Point(Point &p);                //复制构造函数
    int getX(){
        return x;
    }
    int getY(){
        return y;
    }

private:                            // 私有数据
    int x, y;

};

// 成员函数的实现
Point::Point(Point &p) {
    x=p.x;
    y=p.y;
    cout<<"呼叫复制构造函数"<<endl;
}

// 类的组合
class Line{           // Line类的定义
public:
    Line(Point xp1, Point xp2);
    Line(Line &l);
    double getLen() { return len;}

private:
    Point p1, p2;
    double len;
};
// 组合类的构造函数
Line::Line(Point xp1, Point xp2) :p1(xp1),p2(xp2){
    cout<<"呼叫Line的构造函数:"<<endl;
    double x= static_cast<double>(p1.getX()-p2.getX());
    double y= static_cast<double>(p1.getY()-p2.getY());
    len = sqrt(x*x+y*y);
}
// 组合类的复制构造函数
Line::Line(Line &l):p1(l.p1),p2(l.p2) {
    cout<<"呼叫Line的复制构造函数:"<<endl;
    len=l.len;
}


// 主函数
int main(){
    Point myp1(1,1), myp2(4,5);
    Line line(myp1,myp2);
    Line line2(line);
    cout<<"Line的长度为:"<<endl;
    cout<<line.getLen()<<endl;
    cout<<"Line2的长度为:"<<endl;
    cout<<line2.getLen()<<endl;
    return (0);

}

```



<br>

转载请注明：[张鹏辉的博客](http://danielzph.github.io) >> [c++ 类与对象](https://danielzph.github.io/2019/10/cpplearningprocess4/)
