---
title: 如何将现有的github pages绑定自定义域名，备案，实现国内CDN加速（更新中)
date: 2020-12-11 15:53:55
tags: [学习,建站]
---

> gitee pages服务貌似并不支持自定义域名绑定，根据[官方说明](https://gitee.com/help/articles/4228)，该服务现在仅由gitee pages Pro服务支持，而该服务个人用户现已无法购买。

# 购买自定义域名

这个的实现方法很多，我是直接在腾讯云旗下的DNSPOD买了个首年一块钱的（真实穷逼）。

# 将自定义域名绑定到github pages

github官方教程：[Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#further-reading)  
下面是我自己在DNSPOD上的流程：
1. ~~打开自己的github仓库，打开`setting`，在`github pages`那里把`Custom domain`改成自己的自定义域名，`save`~~  
   试过以后我才发现被划去的步骤对于使用hexo搭建博客的我来说是完全错误的，对于github pages来说，被划去的步骤实际上执行了一个操作，那就是在你的仓库master分支下生成了一个叫CNAME的文件，而这个文件的内容就是你的提交的子域名，但倘若你使用诸如hexo这样的框架去实现推送，它每次都会自动地把CNAME覆盖掉，为了实现在推送以后也不覆盖掉CNAME文件，你必须自己在`source`文件夹下创一个叫CNAME的文件(大写无后缀)，然后用随便什么文本编辑器(ep.记事本)把内容写成你的域名即可(例如我的就是flylee.club)，hexo的原理就是在`source`文件夹下的非markdown文件都会原模原样地上传到github仓库文件夹下，所以这样就成功了。
2. 在DNSPOD上把自己在github pages上的域名写到CNAME里去，详见[DNSPOD官方教程](https://docs.dnspod.cn/dns/5f2d4664e8320f1a740d9cf9/)。
![CNAME](https://cdn.jsdelivr.net/gh/flyleeee/flyleeee.github.io/images/CNAME.png)(这两步先后顺序无所谓)。
3. 