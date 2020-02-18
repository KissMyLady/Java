# Java多线程

<!-- GFM-TOC -->

* [一、多线程启动---实例方法](#一多线程启动---实例方法)
* [二、自定义线程名称](#二自定义线程名称)
* [三、同步代码块](#三同步代码块)
* [四、 同步函数使用的朔是this](#四同步函数使用的朔是this)  
* [五、单例设计--懒汉模式](#五单例设计--懒汉模式)
* [六、死 锁](#六死 锁)
<!-- GFM-TOC -->
##  一、多线程启动---实例方法:   

```java
package my03;
//1. 找api文档说明
class Demo1 extends Thread {
    public void run() {
        for (int i=0; i<60; i++){
            System.out.println(i+"Demo111 run");}}}

class Demo2 extends Thread {
    public void run() {
        for (int i=0; i<60; i++){
            System.out.println(i+"Demo222 run");}}}

class Demo3 extends Thread {
    public void run() {
        for (int i=0; i<60; i++){
            System.out.println(i+"Demo333 run");}}}

public class threading{
    public static void main(String[] args){
        Demo1 t1 = new Demo1();
        Demo2 t2 = new Demo2();
        Demo3 t3 = new Demo3();

        new Thread(t1).start();
        new Thread(t2).start();
        new Thread(t3).start();}}}
```

*   CPU升级的情况下,  内存是瓶颈  

Thread用于描述线程,  该类就定义了一个功能用于存储要运行的代码, 存储功能就是run方法   

Thread的run方法是开辟线程运行的位置 

**注意一点:**  

```JAVA
package my03;
public class threading{
    public static void main(String[] args){
        Thread t4 = new Thread();
        t4.start();
    }
}
```

可以直接使用Thead创建对象, 但是不能start, 因为文档写的很清楚了:   `导致此线程开始执行; Java虚拟机调用此线程的run方法`。 

###### 注意调 Run 和 Start 方法的区别:  

```java
package my03;
class Demo3 extends Thread {
    public void run() {
        for (int i=0;i<60;i++){
            System.out.println(i+"Demo333 run"); }}}

public class threading{
    public static void main(String[] args){
        Demo3 d3 = new Demo3();
        d3.start(); // 开启线程并执行
        d3.run();   //仅调用类的run方法
    }}
```



#### 打印线程名称:   

```Java
package my03;

class Demo3 extends Thread {
    public void run() {
        for (int i=0;i<60;i++){
            System.out.println(i+"Demo333 run");
            System.out.println(this.getName()); }}}

public class threading{
    public static void main(String[] args){
        Demo3 d3 = new Demo3();
        new Thread(d3).start();}}
```



## 二、自定义线程名称:  

```Java
package my03;
class Demo1 extends Thread {
    Demo1(String name){
        super(name);}
    
    public void run() {
        for (int i=0;i<60;i++){
            System.out.println(this.getName()+"..."+i);}}}

public class threading{
    public static void main(String[] args){

        Demo1 d1 = new Demo1("Aab++");
        new Thread(d1).start();}}
```

输出结果 :

```
Aab++...0
Aab++...1
Aab++...2
Aab++...3
Aab++...4
......
```

### 卖票多线程:  
```Java
package my03;
// 卖票程序
class Sell_1 extends Thread {
    public void run() {
        for (int i=0; i<60; i++){
            //System.out.println(i+"Demo111 run");
            System.out.println(this.getName()+"..."+i);
        }
    }
}
class Sell_2 extends Thread {
    public void run() {
        for (int i=0; i<60; i++){
            //System.out.println(i+"Demo111 run");
            System.out.println(this.getName()+"..."+i);
        }
    }
}
class Sell_3 extends Thread {
    public void run() {
        for (int i=0;i<60;i++){
            //System.out.println(i+"Demo111 run");
            System.out.println(this.getName()+"..."+i);
        }
    }
}

public class threading{
    public static void main(String[] args){
        Sell_1 t1 = new Sell_1();
        Sell_1 t2 = new Sell_1();
        Sell_1 t3 = new Sell_1();
        Sell_1 t4 = new Sell_1();
        t1.start();
        t2.start();
        t3.start();
        t4.start();
    }
}
```

[小问题: 使用cmd运行java程序错误](https://blog.csdn.net/weixin_39085109/article/details/80189899) 
```java
Microsoft Windows [版本 10.0.16299.611]
(c) 2017 Microsoft Corporation。保留所有权利。

D:\Java初级工程师\todat\src\my03>javac -d . threading.java // 解决办法1

D:\Java初级工程师\todat\src\my03>java my03/threading

D:\Java初级工程师\todat\src\my03>java threading  		  // 解决办法2
错误: 找不到或无法加载主类 threading
原因: java.lang.ClassNotFoundException: threading

D:\Java初级工程师\todat\src\my03>
```

#### 启动方式二

```Java
package my03;

class Sell_1 extends Thread {
    public void run() {
        for (int i=0; i<60; i++){
            System.out.println(this.getName()+"..."+i);}}}
            
public class threading{
    public static void main(String[] args){
        Sell_1 s1 = new Sell_1();

        Thread t1 = new Thread(s1);
        Thread t2 = new Thread(s1);
        Thread t3 = new Thread(s1);
        Thread t4 = new Thread(s1);

        t1.start();
        t2.start();
        t3.start();
        t4.start();}}
```



#### 额外启动方法

```Java
package my03;
class Sell_3 implements Runnable {
    private int ticks = 100;
    public void run() {
        while (true){
            if(ticks>0){
                System.out.println(Thread.currentThread().getName()+"...."+ticks--);}}}}

public class threading{
    public static void main(String[] args){
        Sell_3 s1 = new Sell_3();

        Thread t1 = new Thread(s1);
        Thread t2 = new Thread(s1);
        Thread t3 = new Thread(s1);
        Thread t4 = new Thread(s1);

        t1.start();
        t2.start();
        t3.start();
        t4.start();}}
```

注意`class Sell_3 implements Runnable {}`



### 线程共享全局变量

```java
package my03;
class Sell_3 implements Runnable {
    private int tick = 100;
    public void run(){
        while (true){
            if (tick>0){
                try{Thread.sleep(10);}
                catch (Exception e){
                    System.out.println("抛出异常: "+e);
                }
                System.out.println(Thread.currentThread().getName()+"..."+tick--);
            }}}}

public class threading{
    public static void main(String[] args){
        Sell_3 s1 = new Sell_3();

        Thread t1 = new Thread(s1);
        Thread t2 = new Thread(s1);
        Thread t3 = new Thread(s1);
        Thread t4 = new Thread(s1);

        t1.start();
        t2.start();
        t3.start();
        t4.start();}}
```

==打印出了 0, -1, -2等==

## 三、同步代码块:   

```java
syncheonized(object){
	code
}
```
`Synchronized`使用方法:   使用自建空对象

```java
package my03;
class Person{  //创建空对象
}

class Sell_3 implements Runnable {
    private int tick = 100;
    private String name = "ZH";
    Person p1 = new Person();

    public void run(){
        while (true){
            synchronized (p1){  //传入空对象
                if (tick>0){
                    try{Thread.sleep(10);}
                    catch (Exception e){
                        System.out.println("抛出异常: "+e);}
                        System.out.println(Thread.currentThread().getName()+"..."+tick--);
}}}}}

public class threading{
    public static void main(String[] args){
        Sell_3 s1 = new Sell_3();

        Thread t1 = new Thread(s1);
        Thread t2 = new Thread(s1);
        Thread t3 = new Thread(s1);
        Thread t4 = new Thread(s1);

        t1.start();
        t2.start();
        t3.start();
        t4.start();}}
```

##### 简单同步实例:   使用上帝对象

```java
package my03;
class Banck {
    private int sum;
    Object obj = new Object(); // Java中的上帝对象
    public void add(int n){
        synchronized(obj){  //引入对象
            sum = sum + n;
            try {Thread.sleep(10);}catch (Exception e){
                System.out.println(e);
            }
            System.out.println("金额和合计数量是:  "+sum);
        }}

    public void show(){
        System.out.println("余额:　"+ sum);}}

class Cus implements Runnable{
    private Banck b1 = new Banck();

    public void run(){
        for (int i=0; i<3; i++) {
            b1.add(100);}
        
        b1.show();}}

public class threading{
    public static void main(String[] args){
        Cus c1 = new Cus();
        Thread t1 = new Thread(c1);
        Thread t2 = new Thread(c1);
        t1.start();
        t2.start();}}
```

##### 同步方法,  函数同步   

```java
package my03;
class Banck {
    private int sum;
    public synchronized void add(int n){
            sum = sum + n;
            try {Thread.sleep(10);}catch (Exception e){
                System.out.println(e);
            }
            System.out.println("金额和合计数量是:  "+sum);
        }

    public void show(){
        System.out.println("余额:　"+ sum);}}

class Cus implements Runnable{
    private Banck b1 = new Banck();

    public void run(){
        for (int i=0; i<3; i++) {
            b1.add(100);}
        
        b1.show();}}

public class threading{
    public static void main(String[] args){
        Cus c1 = new Cus();
        Thread t1 = new Thread(c1);
        Thread t2 = new Thread(c1);
        t1.start();
        t2.start();}}
```

## 四、 同步函数使用的朔是this  

```Java
package my03;

class Ticket implements Runnable{
    private int tickets = 500;
    Object obj = new Object();

    boolean flag = true;

    public void run(){
        if(flag)
        {
            while (true)
            {
                synchronized (this)
                {

                    if (tickets <= 1)
                    {
                        System.out.println("有钱人的生活, 就是这么单调枯燥, 且乏味" + tickets--);
                        break;
                    }
                }
            }

        }else
            while(true)
                show();
    }

    public synchronized void show(){ //this
        if (tickets>0){
//            try{Thread.sleep(10);}catch (Exception e){
//                System.out.println(e);
//            }
            System.out.println(Thread.currentThread().getName()+"..code.."+ tickets--);
        }
    }

}


public class threading{
    public static void main(String[] args){
        Ticket t = new Ticket();

        Thread t1 = new Thread(t);
        Thread t2 = new Thread(t);

        t1.start();
        try{Thread.sleep(10);}
            catch(Exception e)
            {};

        t.flag = false;
        t2.start();
    }
}
```

## 静态同步函数的锁是Class对象   

静态修饰后的锁是:   class对象

```java
package my03;


class Ticket implements Runnable{
    private static int tickets = 500;
    Object obj = new Object();

    boolean flag = true;

    public void run(){
        if(flag)
        {
            while (true)
            {
                synchronized (Ticket.class) //字节码文件对象
                {

                    if (tickets <= 1)
                    {
                        System.out.println("有钱人的生活, 就是这么单调枯燥, 且乏味" + tickets--);
                        break;
                    }
                }
            }

        }else
            while(true)
                show();
    }

    public static synchronized void show(){ //this
        if (tickets>0){
//            try{Thread.sleep(10);}catch (Exception e){
//                System.out.println(e);
//            }
            System.out.println(Thread.currentThread().getName()+"..code.."+ tickets--);
        }
    }

}


public class threading{
    public static void main(String[] args){
        Ticket t = new Ticket();

        Thread t1 = new Thread(t);
        Thread t2 = new Thread(t);

        t1.start();
        try{Thread.sleep(10);}
            catch(Exception e)
            {};

        t.flag = false;
        t2.start();
    }
}
```

## 单例设计--懒汉模式

云里雾里,  先跳过吧

```Java
package my03;

//饿汉式
class Single{
    private static final Single s = new Single();
    private Single(){}
    public static Single getInstance(){
        return s;
    }
}

//懒汉式
class Single_hungry{
    private static Single_hungry s = null;
    private Single_hungry(){};
    public static Single_hungry getInstance(){
        if (s==null)
            s = new Single_hungry(); //延迟加载
            return s;
    }
}

public class threading{
    public static void main(String[] args){
        System.out.println("Hello World");
    }
}
```

## 六、死 锁

```Java

```
