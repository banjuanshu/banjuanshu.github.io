---
layout: post
title: "设置浏览器最大持久连接数"
info: "设置浏览器最大持久连接数 浏览器无法支持多个"
tech: "browser"
type: "browser"
---



# 设置浏览器最大持久连接数





#### 三、说一下Firefox浏览器

在`Firefox`地址栏中输入：`about:config`

在搜索项输入：`network.http.max-connections`

老版本值是30，我这个版本是256，说明有改进。



我们再输入：`network.http.max-persistent-connections-per-server`进行搜索，发现是6。



你可以写个Demo测试一下，写个小循环，然后访问同一个域名（推荐用[ Ajax  ](https://cloud.tencent.com/developer/tools/blog-entry?target=http%3A%2F%2Fwww.sojson.com%2Ftag_ajax.html&source=article&objectId=1683127)方式），然后后台`sleep`一会，你就能看出效果。之前有人做过低版本的测试，得出结论。
