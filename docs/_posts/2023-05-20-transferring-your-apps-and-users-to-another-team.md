---
layout: post
title: "将您的应用程序和使用AppleID登录的用户转移到另一个团队"
info: "将您的应用程序和使用AppleID登录的用户转移到另一个团队"
tech: "iOS"
type: "tools"
---



## 背景介绍

公司因一系列的原因，现在需要将APP转移到另一个主体（新账号），苹果提供了转移APP的操作。所以我们现在需要把APP转到新主体，并且也要将用户迁移到新主体，这样使用`Apple ID`登录的用户登录以后可以关联到老账号，既在老主体下登录所产生的账号。



## 操作步骤

1、在Apple开发者后台向新主体发起转移APP的操作

​	（开发者后台上点点，不赘述）



2、调用API迁移用户，产生 `transter_sub`



​	



3、在新主体的Apple开发者后台接收应用

4、调用API，用transter_sub 换取新的sub，并用新sub更新原有sub





## 什么是JWT？















##### 参考资料

https://developer.apple.com/documentation/sign_in_with_apple/transferring_your_apps_and_users_to_another_team

https://developer.apple.com/documentation/sign_in_with_apple/bringing_new_apps_and_users_into_your_team

https://www.belmeng.com/sign-in-with-apple-transfer/
