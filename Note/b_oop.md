Java面向对象基础知识引导   
====
<!-- GFM-TOC -->
* [一、面向对象描述](#一面向对象描述)
* [二、类与对象的举例](#二类与对象的举例)
* [三、成员变量与局部的关系](#三成员变量与局部的关系)
* [四、匿名对象的应用](#四匿名对象的应用)
* [五、封装](#五封装)
* [六、构造--初始化](#六构造--初始化)
* [七、This关键字](#七This关键字)
<!-- GFM-TOC -->


# 一、面向对象描述 
#### 本质核心: 通过封装组件，隐藏复杂度
举 例: 
1. 要去北京看长城, 什么都不用管, 旅行(不用看红绿灯, 都交给司机),  拍照(不用管怎么拍, 交给手机内部复杂逻辑电路)   
2. 要翻墙, 什么都不用管, 给钱(调用软件功能即可, 软件内部的具体细节我们不用管)   
3. 去吃饭, 调用服务员, 不用管菜怎么做   


所以: 使用OOP, 我们可以把复杂的问题封装, 然后简单的调用接口使用即可   
#### [软件工程](https://github.com/KissMyLady/Computer/blob/master/Note/Software_Engineering.md)

Java: 万物皆对象   
Python: 万物皆对象   




# 二、类与对象的举例
### 一个类演示:  
```Java
package to.today.my09__oop;
class Car{
    String name = "鲲鹏";
    int nums = 4;
    void run(){
        System.out.println(name+nums);
    }
}

class Demo{
    public static void main(String[] args){
        Car q = new Car();
        show(q);
    }
    
    public static void show(Car c){
        c.nums = 2;
        c.name = "先知";
        c.run();
    }
}
```
```Java
package to.today.my08;
public class test_oop {
    public static void main(String[] args){
        String[] arr = {"hah","hhe","heihei","xixi","hiahia"};

        MainTest.main(arr);
    }
}

class MainTest{
    public static void main(String[] args){

        for (int i=0; i<args.length;i++){
            System.out.println(args[i]);
        }
    }
}
```    
#### 详细说明:     
```
主函数: 是一个特殊的函数。 作为程序的入口，可以被jvm调用。  
 
主函数的定义：
public: 权限修饰符
static: 代表主函数随着类的加载就已经存在了。
void: 主函数没有具体的返回值。
main: 不是关键字，但是是一个特殊的单词，可以被jvm识别。
(String[] arr): 函数的参数，参数类型是一个数组，该数组中的元素是字符串。字符串类型的数组。
   
主函数是固定格式的: jvm识别。

jvm在调用主函数时, 传入的是new String[0];
```

## Private使用 
```Java
package to.today.my09__oop;
class Person{
    // private修饰成员, 函数, 只在本类中有效
    private int age = 18;
    String name = "智子";

    public void setAge(int a){//注意命名规范
        if (a>0 && a<3000){
            age = a;
            System.out.println("setAge is success");
            speak();
        }
        else age = 0;
    }

    public int getAge(){
        return age;
    }

    void speak(){
        System.out.println("My name is : "+name+" and I am "+age+"yeas old");
    }
}

class PersonDemo{
    public static void main(String[] args){
        Person p = new Person();
        // p.age = 22;
        p.setAge(32);
        System.out.println("");
        p.name = "程心";
        p.speak();
        int cc = p.getAge();
        System.out.println(cc);
    }
}
```
输出结果:  
```
setAge is success
My name is : 智子 and I am 32yeas old

My name is : 程心 and I am 32yeas old
32
```



# 三、成员变量与局部的关系
成员变量:  
* 1. 成员变量定义在类中，在整个类中都可以被访问    
* 2. 成员变量随着对象的建立而建立，存在于对象所在的堆内存中    
* 3. 成员变量有默认初始化值。

局部变量：
* 1. 局部变量只定义在局部范围内，如: 函数内，语句内等   
* 2. 局部变量存在于栈内存中   
* 3. 作用的范围结束，变量空间会自动释放   
* 4. 局部变量没有默认初始化值   



# 四、匿名对象的应用
匿名对象是对象的简化形式

匿名对象两种使用情况
* 1. 当对对象 方法仅进行 一次调用的时   
* 2. 匿名对象可以作为实际参数进行传递   



# 五、封装
封装: 是指隐藏对象的属性和实现细节，仅对外提供公共访问方式   

好处：
* 1. 将变化隔离   
* 2. 便于使用   
* 3. 提高重用性   
* 4. 提高安全性   

封装原则: 
* 1. 将不需要对外提供的内容都隐藏起来   
* 2. 把属性都隐藏，提供公共方法对其访问   


# 六、构造--初始化   
特 点: 
1. 函数名与类名相同
2. 不用定义返回值类型
3. 不可以写return语句
* 作 用: 给对象进行初始化。

注 意: 
1. 默认构造函数的特点   
2. 多个构造函数是以重载的形式存在的   
#### 3. 初始化的Person与类名一致     
### 构造函数, 一建立, 立马调用与之构造的函数, 构造函数的作用就体现出开了: #### 初始化      
初始化举例: 人: 出生就会哭, 就会吃奶

#### 没调用函数, 函数执行了:  
```Java
class Person{
    Person(){
        System.out.println("person run");
    }
}

class PersonDemo2{
    public static void main(String[] args
        Person p = new Person(); //person run
    }
}
```
解 释:  
new方法调用一次, 执行一次, 例如这样, `new Person();`   
```Java
class Person{
    Person(){
        System.out.println("person run");
    }
}
class PersonDemo2{
    public static void main(String[] args){
        System.out.println("入口");

        Person p = new Person(); //person run
        new Person(); // 第二次执行 
    }
}
```
#### 如果没有定义`Person(){}`, 系统会默认加入`Person(){}`, 否则对象建立不出来      
```Java
Person(){
     System.out.println("person run");
}
```
故: `Person(){}`是初始化的方法  

## 初始化实例:   
```Java
class Person{
    private String name;
    private int age;

    Person(){
        System.out.println("This is 1: "+name+" "+age);
    }

    Person(String n){
        name = n;
        System.out.println("This is 2: "+name+" "+age);
    }
    Person(String n, int a){
        name = n;
        age = a;
        System.out.println("This is 3: "+name+" "+age);
    }
}

class PersonDemo2{
    public static void main(String[] args){
        Person p1 = new Person();
        Person p2 = new Person("妲己");     
        Person p3 = new Person("貂蝉", 18);  
    }
}
```
放个大招, 虽然开发见不着, 但是会出现   
```Java
class Person{
    private String name;
    private int age;

    { //构造代码块, 初始化运行, 无论是否满足初始化条件, 都要执行
        cry();
    }


    Person(){
        System.out.println("This is 1: "+name+" "+age);
    }

    Person(String n){
        name = n;
        System.out.println("This is 2: "+name+" "+age);

    }
    Person(String n, int a){
        name = n;
        age = a;
        System.out.println("This is 3: "+name+" "+age);
    }

    public void cry(){
        System.out.println("Cry.......");
    }
}

class PersonDemo2{
    public static void main(String[] args){
        Person p1 = new Person();
        Person p2 = new Person("妲己");
        Person p3 = new Person("貂蝉", 18);

        p1.cry();
    }
}
```



# 七、This关键字 
特点: this代表其所在函数所属对象的引用   
换言之: this代本类对象的引用   

什么时候使用this关键字? 
当在函数内需要用到调用该函数的对象时，就用this   
this: 区分局部变量和成员变量   
### this使用方法:  
```Java
class Person{

    private String name;
    private int age;

    { //构造代码块, 初始化运行, 无论是否满足初始化条件, 都要执行
        System.out.println("person code run");
        cry();
    }

    Person(){
        System.out.println("This is 1: "+name+" "+age);
    }

    Person(String name){
        this.name = name; //本类的对象引用
        System.out.println("This is 2: "+name+" "+age);

    }
    Person(String name, int age){
        this.name = name; 
        this.age = age; 
        System.out.println("This is 3: "+name+" "+age);
    }

    public void cry(){
        System.out.println("Cry.......");
    }
}

class PersonDemo2{
    public static void main(String[] args){
        Person p1 = new Person();
        Person p2 = new Person("妲己");
        Person p3 = new Person("貂蝉", 18);

        p1.cry();
    }
}
```
this解释: 对象的name   
* 变量出现同名情况下加上  




