---
title: 战略转移Cloudflare
comments: true
toc: true
date: 2021-05-23 13:23:10
updated: 2021-06-08 13:23:10
categories:
- 建站日志
tags:
- 经验分享
- Hexo
sticky:
---

[Cloudflare Page](https://www.cloudflare.com/zh-cn/)是一个替换GitHub Pages的方案。
# 缘起

在浏览本Hexo主题的作者的博客——[糖菓·部落](https://candinya.com/)时，发现他的博客没有托管在<a href="https://github.io" target="_blank">Github Pages</a>上，而是使用了<a href="https://pages.cloudflare.com" target="_blank">Cloudflare Pages</a>。虽然我有了解，现在国内外有很多静态网页托管平台，但GitHub Pages在各方面应该算是一个首选。（尤其对于我这种新手）
<!-- more -->

与此同时，我之前在[百度站长平台](https://ziyuan.baidu.com)上提交的博客网址至今一个索引量也没有。虽然我的网站刚刚开始不久，但没有一个索引量，使我开始怀疑是不是哪里出了问题。

于是，我开始在网上搜索“博客的搜索引擎收录”，偶然间发现了这么一篇文章[解决百度爬虫无法爬取Github Pages个人博客的问题](https://zpjiang.me/2020/01/15/let-baidu-index-github-page/)。
> **百度爬虫被拒绝访问**
>
>然而，2015年，因为一些不能细说的原因，Github 开始拒绝百度爬虫的访问，直接返回 403。官方给出原因是，百度爬虫爬得太狠，影响了 Github Page 服务的正常使用。这就导致了，但凡在 Github Page 搭建的个人博客，都无法被百度收录。

文中给出的解决方案有：
-  CDN解决最后一公里的资源分发，但无法完美解决问题，尤其对小流量的个人博客。
-  Coding Pages做镜像站，但访问时会先出现跳转页面，导致百度爬虫无法正常收录。
-  使用[ zeit.co ](zeit.co)提供的静态资源hosting服务，本质上他们提供了Storage+CDN+DNS这一套完整服务。

# 解决问题

受文章[解决百度爬虫无法爬取Github Pages个人博客的问题](https://zpjiang.me/2020/01/15/let-baidu-index-github-page/)的启发，我想<a href="https://pages.cloudflare.com" target="_blank">Cloudflare Pages</a>是不是也能解决相同的问题呢。

于是在网上继续搜索，找到以下博文：
- [迁移博客到 Cloudflare Pages](https://yanqiyu.info/2021/03/06/cloudflare-pages/)
- [利用CloudFlare Pages搭建一个Hexo博客](https://blog.794td.me/archives/14.html)

我开始了解到，<a href="https://pages.cloudflare.com" target="_blank">Cloudflare Pages项目</a>现在处于公测阶段 (Public Beta)，任何人都可以使用，只需要注册一个 CloudFlare 账户。免费套餐单月可部署500次，无限流量。Cloudflare Pages依托于成立于2009年7月的网络服务提供商[Cloudflare, Inc.](https://www.cloudflare.com/zh-cn/)，因此可以提供稳定的静态网页托管服务。

>  “ Cloudflare家大业大，并且是专门做网络服务的，做网页托管应该不会太菜吧。 ”

![屏幕截图 2021-05-23 213728.png](https://i.loli.net/2021/05/23/ldZbDFGcrsw3iU2.png)

转移到<a href="https://pages.cloudflare.com" target="_blank">Cloudflare Pages</a>能不能解决百度收录的问题，我不知道，但有人用它就说明Cloudflare不差。

# 转移部署

不行，我要给我的博客最好的环境，折腾开始！当然，如果已有GitHub Pages搭建好的博客，单纯想要把把托管转移到Cloudflare Pages，这个过程是不难的。

在[Pages](https://pages.cloudflare.com)注册好账号，点击那个大大的黄色的Get Started按钮，按照指引授权GitHub权限，选择构建使用的仓库(就是GitHub Pages的仓库地址)。

设置构建的命令，我不太懂，也没有改动，结果就部署完成了，就不管它了。

【部署完成】>> [https://gone1724-github-io.pages.dev](https://gone1724-github-io.pages.dev/)

我实测从上传完成，到部署完成用时在50s左右，实测站点IP支持IPV6！

# 域名解析

我的域名[huanz.top](https://huanz.top/)之前托管在[DNSPod](dnspod.cn)。由于Cloudflare也提供了DNS解析服务，就顺便也试用了一下它的免费的解析套餐。

![屏幕截图 2021-05-23 143416.png](https://i.loli.net/2021/05/23/y4iH3FZjhJIf7rn.png)

~~主观感觉上速度不太行，已换回[DNSPod](dnspod.cn)。~~

# 部署原理

以下是我的理解：

- Hexo把本地生成好的静态文件上传到GitHub仓库里。
- Cloudflare Pages会自动访问GitHub仓库，在自己的主机上生成一个网站，完成部署。
- 此时，博客网站已完全脱离GitHub/GitHub Pages，在访客访问[huanz.top](https://huanz.top/)时就会解析到Cloudflare的主机。
  + 同理，GitHub Pages则是在自己主机上生成，主机在国外。
  + ~~Cloudflare Pages在国内有主机，访问速度会较快。（官网介绍）~~
  + 但目前来看，主机还是美国节点，速度看[这里](https://www.ping.cn/ping/huanz.top)

![global-network.png](https://i.loli.net/2021/05/23/UdFsluekOYTfw7m.png)

# 更多细节

更多细节上的疑问，欢迎在下面评论区进行留言交流。
