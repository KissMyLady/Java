Java语法基础知识引导   
====

### 1. Java中的注释三种方式  
1. 单行注释`//`:    
`//`后到本行结束的所有字符会被编译器忽略;   
   
2. 多行注释`/* */`:   
`/* */`之间的所有字符会被编译器忽略   
   
3. 文档注释`/** */`:   
在`/** */`之间的所有字符会被编译器忽略, Java特有的(用于生成文档);    
总 结: 多行和文档注释不能嵌套使用      

   
### 2. Java标识符   
可简单理解为在Java程序中为了增强阅读性自定义的名称        
如: 类名，方法名，变量名等   
命名规则：   
(1) 由字母、 数字、 下划线、 $组成，不能以数字开头   
	注意: 此处的字母还可以是中文, 日文等;   
(2) 大小写敏感   
(3) 不得使用java中的关键字和保留字   
(4) 别用Java API里面的类名作为自己的类名。   
   
下面的标识符是正确的：    
   `myName，My_name，Points，$points,_sys_ta，OK，_23b，_3_`   

下面的标识符是错误的：      
   `#name，25name，class，&time，if`    


### 3. 数据类型分类   
基本数据类型   
1. 字符串常量: "abc", "Hello World"   
2. 整数型: byte short int long, 如: 101, 500      
3. 浮点型: float double 如: 2.5, -3.1415926
4. 字符型: char, 如:'A', 'B', '我', 注意, 有且仅有一个
5. 布尔型: boolean 只有两种: true, false   
6. 空常量: null 注意Python中的空常量是`None`   
```Python
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 
'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 
'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 
'try', 'while', 'with', 'yield']
``` 
引用数据类型   
字符串、 数组、 类、 接口、 Lambda      

实例举证:  
```Java
package to.today.my;

public class demo01 {
    public static void main(String[] args){  // 入口
        int a=1;
        System.out.println(getType(a));
        System.out.println("Hello Python !!!");
        System.out.println("Hello Wordl !!!");
        System.out.println("");
        System.out.println(100);
        System.out.println(3.1415926);

        System.out.println('Z');
        System.out.print(true);
        System.out.print(false);

        // System.out.println(null); Error
    }

    public static String getType(Object o ){
        return o.getClass().toString();
    }
}
```
![ScreenShot-00357](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00357.jpg)   
长整型: `2**64 == 18 446 744 073 709 551 616`可以表示20位数字  
float单浮点可以表示: 39位(科学计数法省空间, 范围和内存不一定相关)
double双浮点: 308位  

float：32位，数据范围在3.4e-45~1.4e38，直接赋值时必须在数字后加上f或F。   
double：64位，数据范围在4.9e-324~1.8e308，赋值时可以加d或D也可以不加。   
	   
#### 注意事项：   
* 1. 字符串不是基本类型，而是引用类型     
* 2. 浮点型可能只是一个近似值   
* 3. 数据范围与字节数不一定相关    
* 4. 浮点数当中默认类型是double。 如果一定要使用float类型，需要加上一个后缀F            
    如果是整数，默认为int类型，如果一定要使用long类型，需要加上一个后缀L。 推荐使用大写字母后缀         

#### 存储知识引导:  
位(bit):一个数字0或者一个数字1，代表一位。       
字节(Byte): 每逢8位是一个字节，这是数据存储的最小单位。        
```
1 Byte = 8 bit     
1 KB = 1024 Byte    
1 MB = 1024 KB   
1 GB = 1024 MB   
1 TB = 1024 GB   
1 PB = 1024 TB   
1 EB = 1024 PB   
1 ZB = 1024 E   
```

### 4. 常量与变量   
变量的概念:   
1. 占据着内存中的某一个存储区域       
2. 该区域有自己的名称（变量名）和类型（数据类型）     
3. 该区域的数据可以在同一类型范围内不断变化      
  
为什么要定义变量：  
用来不断的存放同一类型的常量，并可以重复使用   

使用变量注意:    
变量的作用范围, 初始化值  
定义变量的格式: t  
数据类型 变量名 = 初始化值       
注：格式是固定的，记住格式，以不变应万变。    

作用范围：定义开始到定义它的代码块结束; 
同一范围内，不允许多个个局部变量命名冲突   

实例:  
```Java
package to.today.my;

public class str_method {
    public static void main(String[] args){

        int aa = 100;
        System.out.println("This is 变量 " + aa);

        long bb = 100000;
        System.out.println(bb);
        bb += 100;
        System.out.println(bb);

        float num1 = 2.6F;
        System.out.println(num1);

        double num2 = 1.2;
        System.out.println(num2);

        char str1 = 'a';
        System.out.println(str1);

        char str2 = '道';
        System.out.println(str2);

        boolean bool1 = true;
        System.out.println(bool1);

        bool1 = false;
        System.out.println(bool1);

        // 作用域:　
        {
            int rang = 100;
            System.out.println(rang);
        }
        // System.out.println(rang); Error

        // 一次到位 
        int a = 100, b = 500, c = 999;
        System.out.println(a);
        System.out.println(b);
        System.out.println(c);
        System.out.println(a +  b + c);
    }
}
```
注意Java赋值与Python区别, `a, b, c = 1, 2, 3`不行    
Java的是: `int a = 100, b = 200, c = 300`     


本机Java安装地址: `C:\Program Files\Java\jdk-9.0.4\bin`  


