---
layout: post
title: "Github WARNING REMOTE HOST IDENTIFICATION HAS CHANGED"
info: "Github WARNING-REMOTE HOST IDENTIFICATION HAS CHANGED"
tech: "Git"
type: "Tools"
---



## 介绍

今天突然`git push`会报如下错误：

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
SHA256:uNiVztksCsDhcc0u9e8BujQXVUpKZIDTMczCvj3tD2s.
Please contact your system administrator.
Add correct host key in /Users/bjs/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/bjs/.ssh/known_hosts:3
RSA host key for github.com has changed and you have requested strict checking.
Host key verification failed.
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

```



## 解决方法

```
Warning: the ECDSA host key for 'github.com' differs from the key for the IP address '20.205.243.166'
Offending key for IP in /Users/bjs/.ssh/known_hosts:38
Matching host key in /Users/bjs/.ssh/known_hosts:40
Are you sure you want to continue connecting (yes/no)? yes  <------ 这里输入yes，然后按回车
```

