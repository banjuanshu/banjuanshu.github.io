---
layout: post
title:  "Mac OS forces app icon not to be displayed on Dock"
info: "MacOS skills"
tech: "System"
type: "OS" 
---



```
xxx.app/Contents/Info.plist 增加：Application is agent (UIElement) ＝ YES
```
