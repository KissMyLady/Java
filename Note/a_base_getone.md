Java入门级知识引导  
====

### 1. 什么是编程?  
编程就是让计算机为解决某个问题而使用某种程序设计语言编写程序代码，并最终得到结果的过程。   
为了使计算机能够理解人的意图， 人类就必须要将需解决的问题的思路、方 法、和手段通过计算机能够理解的形式  
告诉计算机，使得计算机能够根据人的指令一步一步去工作，完成某种特定的任务。    
这种人和计算机之间交流的过程就是编程。   

### 2. Java能干吗?  
Java语言主要应用在互联网程序的开发领域。
常见的互联网程序比如天猫、京东、物流系统、网银系统等，以及服务器后台处理大数据的存储、查询、数据挖掘等也有很多应用      
1. 1995年推出    
2. 面向Internet的编程语言       
3. Web首选开发语言     
4. 简单易学，完全面向对象，安全可靠，与平台无关的编程语言    

### 3. 三大技术框架   
#### java5.0  之后的三大技 术框架    
J2EE(Java 2 Platform Enterprise Edition) 企业版       
在 jdk5.0 版本后称为 JAVAEE,是为开发企业环境下的应用程序提供的一套解决方案。该技术体系中包含的技术如      
Servlet Jsp 等，主要针对于 Web 应用程序开发。 是市面上培训机构主要学习内容之一.。       

#### J2SE （Java 2 Platform Standard Edition ）标准版    
在 jdk5.0 版本后称为 JAVASE,这是在 java 基础阶段主要学习的内容,也是 java 的基础,以后不管从事 Android 开发或    
者是物联网+云计算的开发,等是建立在 JSE 基础上的,因此该技术是 java 的最核心技术,是传智播客基础班的主要上    
课内容.。

#### J2ME(Java 2 Platform Micro Edition) 小型版    
在 jdk5.0 版本以后称为 JAVAME,该技术多应用于一些电子产品的嵌入式开发,以前在手机开发上应用的也比较多,但    
是随着智能手机的发展,现在手机应用程序(比如 Android 程序)的开发已经不再使用该技术    


### 4. JRE和JDK       
JRE:(Java Runtime Environment)，java  运行环境。    
包括 Java 虚拟机(JVM Java Virtual Machine)和 Java 程序所需的    
核心类库等，如果想要运行一个开发好的 Java 程序，计算机中只需要安装 JRE 即可。    

JDK:(Java Development Kit Java) 开发工具包。    
JDK 是提供给 Java 开发人员使用的，其中包含了 java 的开发工具，也包括了 JRE。        
所以安装了 JDK，就不用在单独安装 JRE 了。    
其中的开发工具：编译工具(javac.exe)  打包工具(jar.exe) 等    
    
简单而言: 使用JDK开发完成的Java程序，交给JRE去运行。
大佬总结: 必须熟练的记忆， 核心类库，开发工具！    

### 5. JVM(Java Virtual Machine)
它是运行所有 Java 程序的抽象计算机,是 Java 语言的运行环境，它是 Java 最具吸引力的特性之一   
1. JVM 读取并处理编译过的与平台无关的字节码(class)文件。   
2. Java 编译器针对 JVM 产生 class 文件，因此是独立于平台的。  
3. Java 解释器负责将 JVM 的代码在特定的平台上运行。  
4. Java 虚拟机是不跨平台的.   

### 6. Java运行机制
`.Java文件 -- .class文件 -- 运行`   
先编译, 后运行, 属于编译型语言, python是解释型语言  

### 7. Java几个简单注意点    
Java语言拼写上区分大小写      
一个 Java源文件里可以定义多个 Java类， 但其中最多只能有一个类被定义成 public类    
了 若源文件中包括了 public类，源文件必须和该 public类同名；   
一个源文件中包含 N个 Java类时，编译后会生成 N份字节码文件，即每个类都会生成一份单独的 class文件，且字节码文件名和其对应的类名相同      
   
总结: 
1. 一个 Java  源文件只定义一个类, 不同的类使用不同的源文件定义;
2. 将每个源文件中单独定义的类都定义成 public 
3. 保持Java源文件的主文件名与源文件中的类名一致    

### 8. Java语法格式      
1. 都定义在类中, 类由class来定义，区分 public class和  class       
2. 区分大小写,如main 和 Main  是不一样的;   
3. Java中的标识符与关键字;   
4. 注释;   
5. main方法的作用：
> 程序的入口   
> 保证程序的独立运行   
> 被JVM调用   
注意在Python中没有入口一说, 怎么写, 顺序执行, 不过也有[if __name__ == "__main__"]这种入口(https://github.com/KissMyLady/Python/blob/master/Nont/ppy_base_ifname.md)   

