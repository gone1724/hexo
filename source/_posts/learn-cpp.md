---
title: C语言备考笔记
comments: true
toc: true
date: 2021-06-03 13:42:23
updated: 2021-06-14 13:42:23
categories:
- 学习笔记
tags:
- C语言
- 经验分享
sticky:
---

这学期开了C语言课，马上也就要期末考试了，就把最近[PTA](https://pintia.cn/)上的一些题整理一下下发到这里，非计算机专业，学术不精。

<!-- more -->

# **结构**
三种程序结构是C语言的基础了：顺序结构、选择结构、循环结构。

# **数组**
数组最应注意初始化，别忘记定义数组个数。下面是一些不好记的库函数：
- **puts(str)** 等于 printf("%s",ste)
- **gets(str)** 约等于 scanf("%s",str)
  + gets()以回车结束输入，会舍弃最后的回车符。
  + scanf()以空白字符结束一次输入,包括空格、回车等。
  + scanf()遇到回车结束后，不会舍弃'\n',而是留在了输入缓冲区中。
- **strcmp(str1,str2)** 字符串比较函数
  + str1大于2,返回正值
  + 逐位比较ASCII码，如z>a>>Z>A>>9>0
  + scanf在读取非空白符之前会忽略回车.
- `strcat(str1,str2)` 用连字符连接字符串
- `strcpy(str1,str2)` 对str1作用，把str2复制到str1
- `strlen(str)` 测字符串长度函数
- `strlwr(str)` 转化为小写函数
- `strupr(str)` 转化为大写函数

# **函数**
- 判断一个素数

```c
int is(int n) //判断一个素数
{
	int i,a=0; //赋初值！！！
	for(i=2;i<=n-1;i++)
	{
        if(n%i==0)
        {
            a++;
            break;
        }
    }
	if(a!=0) return 0;
	else return 1;
}
```

# **指针**
指针相对于之前的知识还是有些难度的！
## 判断题
- 直接访问就是直接利用变量的地址直接进行访问。
T
- char *s="C Language";表示s是一个指向字符串的指针变量，把字符串的首地址赋予s。
T

## 单选题
- 设变量定义为 int a[2]={1,3}, *p=&a[0]+1; ，则*p的值是( )。{% collapse 点击展开答案和解析 %}
答案为3

*p=&a[1]值为3。
{% endcollapse %}

- 若变量已正确定义并且指针p已经指向某个变量x，则(*p)++相当于____。
A.p++	B.x++	C.*(p++)	D.&x++{% collapse 点击展开答案和解析 %}
答案为B

*p=x，(*p)++自然等于x++。
{% endcollapse %}

- 若有如下定义，则（ ）的值是34。
int a[] = {5, 15, 34, 54, 14, 2, 52, 72};int *p = &a[1];
A.p[1]	B.p[2]	C.p[0]	D.p[3]{% collapse 点击展开答案和解析 %}
p指向a[1]，p[1]的内容就是a[2]了，也就是34。
{% endcollapse %}

- 根据声明int a[10], *p=a; ，下列表达式错误的是（ ）。
A.a[9]  B.p[5]  C.a++ D.*p++{% collapse 点击展开答案和解析 %}
答案为C

p[5]就是 *(p+5),也就是a[5]。
{% endcollapse %}

- 若定义pf为指向float类型变量f的指针，下列语句中__是正确的。
A.float f, *pf = f; B.float f, *pf = &f;
C.float *pf = &f, f;  D.float f, *pf =0.0;{% collapse 点击展开答案和解析 %}
答案为B

float f, *pf = f;含义同赋值语句*pf = f不同，而是相当于float f, *pf;pf = f;pf被初始化指向地址值为f的指针，而地址值不可能是float的，这不合语法，所以出错。

定义时初始化 float *pf = &f;等价的语句是:float *pf;pf = &f;是正确的。
{% endcollapse %}

# **后记**
写个东西，排版有点费事，有这时间还不如滚去复习去~ 
