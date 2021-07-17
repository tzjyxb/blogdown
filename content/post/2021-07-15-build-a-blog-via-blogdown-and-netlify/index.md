---
title: Build a blog via blogdown and Netlify
author: Bin Xu
date: '2021-07-15'
slug: build-a-blog-via-blogdown-and-netlify
categories: ["blogdown"]
tags: []
---

本文记录如何通过`blogdown`package和Netlify建立个人blog，参考：[blogdown updates prompted a website overhaul: These are my notes](https://solomonkurz.netlify.app/post/2021-05-03-blogdown-updates-prompted-a-website-overhaul-these-are-my-notes/)；主要参考step 1-6，之后的step对应于文中应用的模板

如果step2的过程中遇到如下错误：
> Failed to connect to github.com port 443: Timed out

需要自行配置代理：设置-网络和Internet-代理，找到**地址**和**端口**，然后在CMD中分别运行：

```cmd
git config --global http.proxy http://127.0.0.1:7890

git config --global https.proxy http://127.0.0.1:7890
```

一些[较老的教程](https://cosx.org/2018/01/build-blog-with-blogdown-hugo-netlify-github/)，参考意义不大，有很多坑；如何commit/更新blog内容可参考该链接教程的最后一部分