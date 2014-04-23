---
layout: post
title:  Knowledge for Cpp Intern
category : others
tagline: 
tags : [cpp, intern]
---

Visual Studio Hot Key for Debug

F9 -> 设置断点

F10 -> 逐过程

F10 -> 逐语句

[More Information about VS hotkey](http://www.cnblogs.com/update158/articles/f23465.html)

---

C++程序变量在内存中的分配问题

* **栈区**（stack） 由编译器自动分配释放，存放函数的参数值，局部变量的值等，其操作方式类似于数据结构的栈。

* **堆区**（heap） 一般由程序员分配释放，若程序员不释放，程序结束时可能由系统回收。注意它与数据结构中的堆是两回事，分配方式倒类似于链表。

* **全局区**（静态区） 全局变量和静态变量的存储是放在一块的，初始化的全局变量和静态变量在一块区域，未初始化的全局变量和未初始化的静态变量在相信的另一块区域，程序结束后由系统释放。

* **文字常量区** 常量字符串就是放在这里的。 程序结束后由系统释放

* **程序代码区** 存放函数体的二进制代码。

{% highlight cpp linenos%}
//main.cpp 
int a = 0; //全局初始化区 
char *p1; //全局未初始化区 
main() 
{ 
  int b; //栈 
  char s[] = "abc"; //栈 
  char *p2; //栈 
  char *p3 = "123456"; //123456\0在常量区，p3在栈上。 
  static int c =0；// 全局（静态）初始化区 
  p1 = (char *)malloc(10); 
  p2 = (char *)malloc(20); 
  //分配得来得10和20字节的区域就在堆区。 
  strcpy(p1, "123456"); //123456\0放在常量区，编译器可能会将它与p3所指向的"123456"优化成一个地方。 
}
{% endhighlight %}

[More Information about This Problem](http://blog.renren.com/share/313938359/7254081401)
