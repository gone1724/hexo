---
title: 开启站长统计
toc: true
date: 2021-05-20 21:40:00
updated: 2021-06-01 18:51:41
categories:
- 建站日志
tags:
- Hexo
- 经验分享
sticky:
comments: true
---

经过今天的折腾，本站已成功开启 **站长统计** 功能。

服务依托于[cnzz.com](https://www.umeng.com/)，访问[站长统计](https://new.cnzz.com/v1/login.php?siteid=1279942268)即可查看我站统计数据。
<!-- more -->
****

# 如何添加cnzz.com站长统计代码到网页上？

据cnzz网站介绍，将统计代码粘贴到您网站所有页面的`</body>`前，添加成功后开始统计。

同时cnzz网站说明，*加载CNZZ统计代码不会影响您网页的正常显示和加载速度。*

# 如何将站长统计的文字/图片隐藏？

在统计代码 javascript 中的 ducument.write(unescape("%3Cspan 和 id='cnzz_stat_icon'中间加上`style='display:none`即可。

如本网站的代码实现如下。

```html
 <script type="text/javascript">document.write(unescape("%3Cspan style='display:none;' id='cnzz_stat_icon_1279942268'%3E%3C/span%3E%3Cscript src='https://v1.cnzz.com/z_stat.php%3Fid%3D1279942268' type='text/javascript'%3E%3C/script%3E"));</script>
```

# 本主题[KRATOS:REBIRTH](https://github.com/Candinya/Kratos-Rebirth)是如何实现的？

本博客使用[Hexo](https://hexo.io/)搭建，几乎无需触碰底层代码，当仍可通过修改主题文件对网站实现自定义。我当前使用的主题[KRATOS:REBIRTH](https://github.com/Candinya/Kratos-Rebirth)默认支持在页尾添加统计代码。

具体位置在`themes\Kratos-Rebirth\_config.yml`文件中`# Global 全局配置`的`site_analytics:`。

# 我做了什么？

通过下面的操作，当我更换域名，只需修改在配置文件中统计代码id号即可。

1. 在`themes\Kratos-Rebirth\_config.yml`中添加一个自定义项如下。

```yml
site_analytics_cnzz: 1279942268 #输入www.CNZZ.com的站长统计id号，默认在网页中隐藏
```

2. 在`themes\Kratos-Rebirth\layout\_partial\head.ejs`文件中，在文本最后， `</body>`之前，添加如下代码,自定义项与前面对应。

```html
<% if (theme.site_analytics_cnzz) { %><script type="text/javascript">document.write(unescape("%3Cspan style='display:none;' id='cnzz_stat_icon_<%- theme.site_analytics_cnzz %>'%3E%3C/span%3E%3Cscript src='https://v1.cnzz.com/z_stat.php%3Fid%3D<%- theme.site_analytics_cnzz %>' type='text/javascript'%3E%3C/script%3E"));</script><% } %>
```
