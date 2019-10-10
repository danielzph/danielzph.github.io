---
layout: post
title: c++语言学习笔记4
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

声明形式： ` Clock myCLOCK ` (类名 对象名)

访问数据成员的一般形式： ` myClock.showTime()` (对象名.数据成员名)

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










<br>

转载请注明：[张鹏辉的博客](http://danielzph.github.io) >> [cpplearningprocess2](https://danielzph.github.io/2019/10/cpplearningprocess4/)
