---
title: C语言初学笔记
comments: true
toc: true
date: 2021-06-03 13:42:23
updated: 2021-06-03 13:42:23
categories:
- 学习笔记
tags:
- C语言
- 经验分享
sticky:
---

这学期开的C语言课，把最近[PTA](https://pintia.cn/)上的一些题整理一下下。如果早一点有这个博客，也许这个页面会更全面一些吧。

{% alertbox info "未完待续... ଘ(੭ˊᵕˋ)੭ " %}

<!-- more -->

# 三大结构
三个程序结构是C语言的基础了。
- 顺序结构
- 选择结构
- 循环结构

# 数组型数据
数组最应注意:初始化时定义个数。下面是一些不好记的库函数：
- 🌟puts(str) 等于 printf("%s",ste)
- 🌟gets(str) 约等于 scanf("%s",str) 
  + gets()以回车结束输入，会舍弃最后的回车符。
  + scanf()以空白字符结束一次输入,包括空格、回车等。
  + scanf()遇到回车结束后，不会舍弃'\n',而是留在了输入缓冲区中。
- 🌟strcmp(str1,str2) 字符串比较函数
  + str1大于2,返回正值
  + 逐位比较ASCII码，如z>a>>Z>A>>9>0
  + scanf在读取非空白符之前会忽略回车.
- strcat(str1,str2) 用连字符连接字符串
- strcpy(str1,str2) 对str1作用，把str2复制到str1
- strlen(str)测字符串长度函数
- strlwr(str)转化为小写函数
- strupr(str)转化为大写函数

# 模块化函数
## 判断一个素数
要点：一点要记得赋初值！！！
```cpp
int is(int n)
{
	int i,a=0; //赋初值！！！！！！！！！！！！！！
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

## 等
要点：
## 等等
要点：
# 善用指针
2333