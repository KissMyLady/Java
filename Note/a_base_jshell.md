
JShell脚本工具是JDK9的新特性
====
> 什么时候会用到 JShell 工具呢?    
1. 简单测试
2. 当代码非常少的时候, 而又懒, 这个时候可以使用JShell工具  

启动JShell工具，在DOS命令行直接输入JShell命令。
```
Microsoft Windows [版本 10.0.16299.611]
(c) 2017 Microsoft Corporation。保留所有权利。

C:\Users\Administrator>jshell
|  欢迎使用 JShell -- 版本 9.0.4
|  要大致了解该版本, 请键入: /help intro

jshell>
```

接下来可以编写Java代码，无需写类和方法，直接写方法中的代码即可，同时无需编译和运行，直接回车即可   
例子一: 
```jshell
jshell> int x=1; x=(x==2? 50:100); System.out.println(x);
x ==> 1
x ==> 100
100

jshell>
```
例子二:    
```jshell
jshell> int a=1; int b=2; System
System

jshell> int a=1; int b=2; System.out.println(a+b);
a ==> 1
b ==> 2
3
```



