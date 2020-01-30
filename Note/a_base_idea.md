使用Java的编辑器(IDEA)RUN
====

## 1. 在cmd中执行Java程序:  
Java是编译型语言, 需要编译后才能在cmd中执行, 像这样:  
![java-1](https://github.com/KissMyLady/Java/blob/master/Img/java-1.jpg)   
第一步, 先编译: `javac HelloWorld.java`     
第二部, 执行: `java HelloWorld`     


## 2. 在IDEA中执行Java程序:  
![ScreenShot-00355](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00355.jpg)  

可能会出现的情况:  
#### Intellij idea 报错: [Error:java不支持发行版本5](https://blog.csdn.net/qq_22076345/article/details/82392236)        
解决办法:  
本地运行用的是JDK9，测试Java的Stream操作，报错应该是项目编译配置使用的Java版本不对，  
需要检查一下项目及环境使用的Java编译版本配置。  
  
1. 在Intellij中点击“File” -->“Project   Structure”，看一下“Project”和“Module”栏目中Java版本是否与本地一致：  
  
  
2. 点击“Settings”-->“Bulid, Execution,Deployment”-->“Java Compiler”，Target bytecode   version设为本地Java版本。  
（可以在Default Settings中把Project bytecode version一劳永逸地配置成本地Java版本）    



