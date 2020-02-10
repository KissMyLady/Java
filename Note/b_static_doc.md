
<!-- GFM-TOC -->
* [一、Static关键字](#一Static关键字)
* [二、Main主函数](#二Main主函数)
* [三、帮助文档的制作Javadoc--Document](#三帮助文档的制作Javadoc--Document)
<!-- GFM-TOC -->
# 一、Static关键字   
static关键字: 用于修饰成员(成员变量和成员函数)   

### 静态内容被修饰对象共享   
```Java
class PPPerson{
    String name; //成员变量, 实例化才有(实例变量)
    static String county = "CN";//静态类变量, 直接可以类名调用  
    public void show(){
        System.out.println("name: "+name+" County: "+county);
    }
}

class StaticDemo{
    public static void main(String[] args){
        System.out.println("Enter");
        PPPerson p1 = new PPPerson();
        p1.name = "王昭君";
        p1.show();
        System.out.println(p1.county);
        System.out.println(PPPerson.county);
    }
}
```
当使用静态方法后, 多了一种新方法: 
* 1. 可以直接调用类数据`p1.county`       
* 2. 可以直接调用类数据`PPPerson.county`   


	
被修饰后的成员具备以下特点:    
> 1. 随着类的加载而加载     
	也就是, static随着类的消失而消失, 生命周期最长   
> 2. Static优先于对象存在     
> 3. 被所有对象所共享     
> 4. 可以直接被类名调用: `PPPerson.county`  

内存: 栈区, 堆区, 方法区   
#### 实例变量与Static区别:   
1. 存放位置,  类变量(Static)存在于方法去中, 生命周期等于类  
	实例变量: 存在堆内存   

2. 生命周期  


#### 使用注意: 
* 1. 静态方法只能访问静态成员(成员: 包括方法和变量)   
* 2. 非静态可以都访问   
* 3. 静态方法中不可以写this，super关键字
>> 因为静态优先于静态存在     
* 4. 主函数是静态的  


#### 1.静态方法只能访问静态成员(类直接方法问静态方法):  
```Java
class PPPerson{
    String name; //成员变量, 实例化才有(实例变量)
    static String county = "CN"; //静态成员变量
    public static void show(){
        System.out.println("County: "+county);
        //System.out.println("name: "+this.name);
    }
}

class StaticDemo{
    public static void main(String[] args){
        System.out.println("Enter");

        PPPerson p1 = new PPPerson();
        p1.name = "王昭君";
        p1.show();

        System.out.println(p1.county);
        System.out.println(PPPerson.county);
        PPPerson.show(); //类直接方法问静态方法 
    }
}
```
这里的name无法直接用, 它不是静态
1. static先于name存在, 此时还没有name   
2. 不能加this, this代表对象, 此时还没有对象创建出来  


## 为什么用Static?  
优 点:    
* 1. 节省空间
* 2. 可直接被类调用   

弊端:  
* 1. 生命周期长  
* 2. 访问具有局限性(静态虽好, 只能访问静态, 访问不了非静态)  



# 二、Main主函数
```Java
class mainDemo{
}
class Main{
    public static void main(String[] args){//new String[]
        System.out.println("Enter");
        System.out.println(args);
        System.out.println(args.length);//0
        //虚拟机在调用主函数时, 传入的是new String[0]; 长度为0

        //故, 我们也可以往里面传入数值, 怎么传, 看下面   

        }
    }
}

//String[] args = new args;
//String[] args = null;


// 主函数, 程序入口, 可以被jvm调用
/*
public: 访问权限
static: 主函数随着类的加载而加载, 就已经存在了
void: (虚拟机)没有具体的返回值, 能用, 能运行就可以, 没有结果回来
main: 不是关键字, 但是是一个特殊的单词, 可以被jvm识别, 别的不认
函数参数: (String[] args): 字符串数组, 该数组中的元素是字符串(存储字符串类型元素的数组)
主函数, 固定格式jvm识别
*/
```


### args传入数据   
```Java
class mainDemo{
}

class Main{
    public static void main(String[] args){//new String[]
        System.out.println("Enter");
        System.out.println(args);
        System.out.println(args.length);//0
        //虚拟机在调用主函数时, 传入的是new String[0]; 长度为0
        for (int i=0;i<args.length;i++){
            System.out.println(args[i]);

        }
    }
}
```
#### args使用方法例子:  
```Python
D:\Python初级工程师\sublime\51--Java\02--面向对象 的目录

2020/02/10  04:45    <DIR>          .
2020/02/10  04:45    <DIR>          ..
2020/02/10  03:15            21,204 001--Object类, Time类, Systemle类, StringBuilder类, 包装类.rs
2020/02/10  03:18             9,445 002--Collection-泛型.rs
2020/02/10  03:16             9,423 003--面向对象基础引导.rs
2020/02/10  04:39             4,332 004--Static.rs
2020/02/10  04:45               312 demo.java
2020/02/10  04:45               515 Main.class
2020/02/10  04:45               186 mainDemo.class
               7 个文件         45,417 字节
               2 个目录 125,100,118,016 可用字节

D:\Python初级工程师\sublime\51--Java\02--面向对象>java Main hh jj hh asd fs
Enter
5
hh
hh
jj
hh
asd
fs

D:\Python初级工程师\sublime\51--Java\02--面向对象>
```

### 上面的高级写法: 
```Java
class Main{
    public static void main(String[] args){//new String[]
        String[] arr = {"haha", "hhe", "heihei", "xixi", "hiehie"};
        MainTest.main(arr);
    }
}

class MainTest{
    public static void main(String[] args){
        System.out.println(args);
        System.out.println(args.length);//0
        for (int i=0;i<args.length;i++){
            System.out.println(args[i]);
        }
    }
}
```
开发不用, 一个主类足够了  


## 什么时候使用静态
> 静态修饰的内容有成员变量和函数    
从两方面下手: 成员变脸和函数 


### 1. 什么时候定义静态变量(类变量)呢 ? 
1. 当对象中出现共享数据(值)时   
> 对象特有数据不共享     

### 当功能内部没有访问到非静态数据(对象特有数据), 那么该功能可以定义成静态的  
```Java
class onePerson{
    static String name;

    public void show(){
        System.out.println("hh");
    }
}

class main2{
    public static void main(String[] args){
        onePerson p1 = new onePerson();
        p1.show();
    }
}
```
#### 对象的出现是为了封装数据的, 建立对象, 还没有使用数据`name`, 那就没有必要使用数据   

## 静态的应用   
* 1. 有共性的功能, 可以分离, 独立封装, 以便复用  
编译一个文件, 里面有new方法, 先在本地文件下找java文件, 如果没有, 找class文件, 如果没有, 报错   

静态方法: 不用创建对象, 直接使用对象即可(不用建立对象浪费内存)  



# 三、帮助文档的制作Javadoc--Document   
找到加载文件设置方法: `set classpath=.;path`    
   
别人, 或直接编译了的文件`.class`, 能够直接执行的文件, 要写说明书   

## 说明书制作方法:  
```java
//Java的说明书通过文档的注释来完成

/**
类的描述信息:  这是一个可以对数组进行操作个工具类, 类提供了: 获取最大值, 排序等功能
 版本:
@author: 王昭君, 貂蝉
@version: 1.0
*/
public class Tool{
    {
        System.out.println("Enter");
    }
    /**
     获取一个数组中的最大值
    @param arr 接收一个int类型的数组
    @return 返回一个该数组的最大值
     */
    public static int getMax(int[] arr){
        int max = arr[0];
        for (int i=0; i<arr.length-1; i++){
            if (arr[i] > max){
                max = arr[i];
            }
        }
        System.out.println(max);
        return max;
    }


    /**
     获取一个数组中的最小值
     @param arr 接收一个int类型的数组
     @return 返回一个该数组的最小值
     */
    public static int getMin(int[] arr){
        int min = arr[0];
        for (int i=0; i<arr.length-1; i++){
            if (arr[i] < min){
                min = arr[i];
            }
        }
        System.out.println(min);
        return min;
    }

    /**
     给int排序
     @param arr 接收一个int类型的数组
     */
    public void selectSort(int[] arr){
        for (int x=0;x<arr.length-1;x++){
            for (int y=0;y<arr.length;y++){
                if (arr[x]>arr[y]){
                    swap(arr, x, y);
                }
            }
        }
    }

    /**
     给数组中元素进行位置的置换
     @param arr 接收int类型的数组
     @param a 要置换的位置
     @param b 要置换的位置
    */
    private static void swap(int[] arr, int a, int b){
        int temp = arr[a];
        arr[a] = arr[b];
        arr[b] = temp;
    }
    /**
     用于打印数组中的元素, 打印形式是: [element1, element2, ...]
     @param arr 接收int类型的数组
     @param a 要置换的位置
     @param b 要置换的位置
     */
    public static void printArray(int[] arr){
        for (int i=0;i<arr.length;i++){
            if (i != arr.length-1){
                System.out.println(arr[i]+", ");
            }
            else{
                System.out.println(arr[i]+"]");
            }
        }
    }
    /**
     用于打印
     */
    public static void main(String[] args){
        System.out.println("Enter");
    }
}
```
CMD生成文档方法:  [注意编码--Javadoc解决中文乱码问题](https://blog.csdn.net/nyh1006/article/details/51441732)
```
javadoc -d myhelp -encoding GBK -charset GBK tool.java

javadoc -d doc -encoding UTF-8 -charset UTF-8 *.java
```

