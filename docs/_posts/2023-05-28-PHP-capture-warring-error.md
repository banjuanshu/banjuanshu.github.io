---
layout: post
title: "PHP 如何捕获 Warring、Notice 错误"
info: "PHP 如何捕获 Warring、Notice 错误"
tech: "PHP"
type: "Other"
---



## 介绍

PHP 的 try catch 无法捕获 **Warring**、**Notice** 错误



## 解决办法

### 方法一、注册错误处理函数来全局捕捉

缺点，不能try catch马上捕捉到，进行处理

```php
set_error_handler([__CLASS__, 'error']);
set_exception_handler([__CLASS__, 'exception']);
register_shutdown_function([__CLASS__, 'shutdown']);

```



**set_error_handler**

```
一般用于捕捉： E_NOTICE 、E_USER_ERROR、E_USER_WARNING、E_USER_NOTICE
 
不能捕捉：
E_ERROR, E_PARSE, E_CORE_ERROR, E_CORE_WARNING, E_COMPILE_ERROR and E_COMPILE_WARNING。

一般与trigger_error("...", E_USER_ERROR)，配合使用。
```



**set_exception_handler**

```
设置默认的异常处理程序，用于没有用 try/catch 块来捕获的异常。 在 exception_handler 调用后异常会中止。 
与throw new Exception('Uncaught Exception occurred')，连用。
```



**register_shutdown_function**

```
执行机制是：php把要调用的函数调入内存。当页面所有PHP语句都执行完成时，再调用此函数。
一般与trigger_error("...", E_USER_ERROR)，配合使用。
```



**restore_error_handler**

```
定义和用法 restore_error_handler() 函数恢复之前的错误处理程序，该程序是由 set_error_handler() 函数改变的。
该函数永远返回 true。
是 set_error_handler()的反函数。
```



### 方法二

**error_get_last**

```php
try {
  	// code...
  
    $error = error_get_last();
    if($error)
        throw new \Exception('Redis server went away');
} catch (\Exception $e) {
    // 
}
```



