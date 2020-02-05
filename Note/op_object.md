对象Object   
=====
<!-- GFM-TOC -->
* [一、Object类](#一Object类)
* [二、日期时间类](#二日期时间类)
* [三、System类](#三System类)
* [四、StringBuilder类](#四StringBuilder类)
* [五、包装类](#四包装类)
<!-- GFM-TOC -->


## 一、Object类
#### 一个面向对象实例:   
```Java
package to.today.my07;
class TheCar{
    int nums = 4;
    String name = "The One";

    void run(){
        System.out.println("第er次打印: "+name+" ... "+nums);
    }
}

class CarDemo{
    public static void main(String[] args){
        TheCar q = new TheCar();
        System.out.println("第一次打印: "+q.name+" ... "+q.nums);
        show(q);  //change
    }

    public static void show(TheCar c){
        c.nums = 2;
        c.name = "The Oracle";
        c.run();
        System.out.println("第san次打印: "+c.nums+" ... "+c.nums);
    }
}
```
输出结果:   
```
第一次打印: The One ... 4
第er次打印: The Oracle ... 2
第san次打印: 2 ... 2
```
## 正 文: 
> java.lang.Object 类是Java语言中的根类，即所有类的父类。 Python中是type    
> 它中描述的所有方法子类都可以使用。 在对象实例化的时候，最终找的父类就是Object。   
* 如果一个类没有特别指定父类， 那么默认则继承自Object类。 例 如：  
```Java
public class MyClass /*extends Object*/ {
   // ...  
}
```
根据JDK源代码及Object类的API文档，Object类当中包含的方法有11个。 主要学习其中的2个:   
* `public String toString()`: 返回该对象的字符串表示。   
* `public boolean equals(Object obj)`: 指示其他某个对象是否与此对象“相等”。   

### 1. toString方法
* `public String toString()`: 返回该对象的字符串表示

toString方法返回该对象的字符串表示，其实该字符串内容就是对象的类型+@+内存地址值。   

由于toString方法返回的结果是内存地址，而在开发中，经常需要按照对象的属性得到相应的字符串表现形式，因
此也需要重写它。  
#### 覆盖重写 
```Java
public class Person{
    private String name;
    private int age;

    @Override
    public String toString() {
        return name +age;
    }
}
```
private关键字：
* 是一个权限修饰符。
* 用于修饰成员(成员变量和成员函数)
* 被私有化的成员只在本类中有效
使用原因:  
* 将成员变量私有化，对外提供对应的set, get方法对其进行访问。 提高对数据访问的安全
性。    


小贴士: 在我们直接使用输出语句输出对象名的时候, 其实通过该对象调用了其toString()方法。      

### 1. 先创建`test_oop1`文件:   
```Java
package to.today.my07;
public class test_oop1{
    private String name;
    private int age;

    public test_oop1(){
    }

    public test_oop1(String name, int age){
        this.name = name;
        this.age = age;
    }

    public String gerName(){
        return name;
    }

    public void setName(String name){
        this.name = name;
    }

    public int getAge(){
        return age;
    }

    public void setAge(int age){
        this.age = age;
    }
}
```
### 2. 创建mian启动:   
```Java
package to.today.my07;
public class tesr_main {

    public static void main(String[] args){
        System.out.println("Person默认继承Object, 使用里面的方法");

        test_oop1 p = new test_oop1("张三", 18);
        String str = p.toString();
        System.out.println("打印toString: "+str); //to.today.my07.test_oop1@282ba1e
        System.out.println("打印p的值: "+p);       //to.today.my07.test_oop1@282ba1e
    }   // p与str方法是等价的
}
```
* 直接打印地址值没有意义, 现在重写toString方法       
在`test_oop1`中重写就可以了:  打印对象的属性      
```Java
package to.today.my07;
public class test_oop1{
    private String name;
    private int age;

    public test_oop1(){
    }

    public test_oop1(String name, int age){
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString(){ //改了这里-----
        return "abc";         //改了这里-----
    }

    public String gerName(){
        return name;
    }

    public void setName(String name){
        this.name = name;
    }

    public int getAge(){
        return age;
    }

    public void setAge(int age){
        this.age = age;
    }
}
```
启动mian文件, 打印结果:  
```
Person默认继承Object, 使用里面的方法
打印toString: abc
打印p的值: abc
```
返回什么, 打印什么. 升级:  
```Java 
package to.today.my07;
public class test_oop1{
    private String name;
    private int age;

    public test_oop1(){
    }

    public test_oop1(String name, int age){
        this.name = name;
        this.age = age;
    }
//    @Override
//    public String toString(){
//        return "abc";
//    }
    @Override
    public String toString(){ //改了这里-----
        return "test_main(name="+name+", age="+age+")";
    } //改了这里-----

    public String gerName(){
        return name;
    }

    public void setName(String name){
        this.name = name;
    }

    public int getAge(){
        return age;
    }

    public void setAge(int age){
        this.age = age;
    }
}
```
打印结果:   
```
Person默认继承Object, 使用里面的方法
打印toString: test_main(name=张三, age=18)
打印p的值: test_main(name=张三, age=18)
```
以后写不用这么麻烦:
方法: alt +Insert键(注意, 笔记本要关闭数字, 然后才能用Insert)  
按了后, 选择toString即可, 自动生成如下代码:  
```Java 
 @Override
    public String toString() {
        return "test_oop1{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
```
区别是否重写方法:  
* 直接打印即可 
```Java 
package to.today.my07;

import java.util.Random;
import java.util.Scanner;

public class tesr_main {

    public static void main(String[] args){
        System.out.println("Person默认继承Object, 使用里面的方法");

        test_oop1 p = new test_oop1("张三", 18);
        String str = p.toString();
        System.out.println("打印toString: "+str); //to.today.my07.test_oop1@282ba1e
        System.out.println("打印p的值: "+p);       //to.today.my07.test_oop1@282ba1e

        Random r = new Random();
        System.out.println("打印Random: "+r); // java.util.Random@2812cbfa

        Scanner sc = new Scanner(System.in);
        System.out.println(sc);
//java.util.Scanner[delimiters=\p{javaWhitespace}+][position=0][match valid=false][need
// input=false][source closed=false][skipped=false][group separator=\,][decimal separator=
// \.][positive prefix=][negative
// prefix=\Q-\E][positive suffix=][negative suffix=][NaN string=\QNaN\E][infinity string=
// \Q∞\E]  可以看到, 重写了toString方法  
    }

}

```


### 2. equals方法
#### test_oop1代码:   
```
package to.today.my07;
import java.util.Random;

public class test_oop1{
    private String name;
    private int age;

    public test_oop1(){
    }

    public test_oop1(String name, int age){
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "test_oop1{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    public String gerName(){
        return name;
    }

    public void setName(String name){
        this.name = name;
    }

    public int getAge(){
        return age;
    }

    public void setAge(int age){
        this.age = age;
    }}
```

* `public boolean equals(Object obj)`: 指示其他某个对象是否与此对象"相等"   
```Java
package to.today.my07;
public class test_equals1 {
    public static void main(String[] args){
        System.out.println("程序入口");

        test_oop1 p1 = new test_oop1("小龙女", 22);
        test_oop1 p2 = new test_oop1("神仙姐姐", 23);

        boolean b = p1.equals(p2);
        System.out.println(b); // false
    }
}
```
返回的是false, 这是什么原因?  
此时, 研究研究equals方法, 点进去, 查看源码:  
```Java
    public boolean equals(Object obj) {
        return (this == obj);
    }
```
可以发现, 返回的是boolean值, this就表示此事的对象, obj表示传进去的对象, 返回两个对象是否一样(内存地址)   
于是, 我们稍微改下main入口处代码:   
```Java
package to.today.my07;
public class test_equals1 {
    public static void main(String[] args){
        System.out.println("程序入口");
/*
public boolean equals(Object obj) { obj: 所有类的父类, 传递任何即可
        return (this == obj);  this: 调用的方法对象, this 就是p1, obj就是p2
}*/
        test_oop1 p1 = new test_oop1("小龙女", 22);
        test_oop1 p2 = new test_oop1("神仙姐姐", 23);
        System.out.println(p1); // test_oop1{name='小龙女', age=22}
        System.out.println(p2); // test_oop1{name='神仙姐姐', age=23}

        boolean b = p1.equals(p2);
        System.out.println(b);  // false
    }
}
```
```Java


```
这段代码充分考虑了对象为空、类型一致等问题，但方法内容并不唯一。
大多数IDE都可以自动生成equals方法的代码内容。 方法同上  


## 二、日期时间类   
### 1. Date类   
`java.util.Date`类 表示特定的瞬间，精确到毫秒。   
```Java
package to.today.my07;
import java.util.Date;
 class test_date {
     public static void main(String[] args){
         System.out.println(new Date());    //Tue Feb 04 17:47:02 CST 2020
         System.out.println(new Date(0L));  //Thu Jan 01 08:00:00 CST 1970
         Date d2 = new Date(256697646686L); 
         System.out.println(d2); 			//Sun Feb 19 08:54:06 CST 1978
     }
}
```
其他过时了  
#### 成员方法:`long time = date.getTime();`
```Java
package to.today.my07;

import java.util.Date;

 class test_date {
     public static void main(String[] args){
         System.out.println("程序入口");
         getTime();
     }

     private static void getTime(){
         Date date = new Date();     // 先正常获取时间
         long time = date.getTime(); // 转换时间
         System.out.println(time);   // 1580810441276
     }
}
```    


### 2. DateFormat类   
`java.text.DateFormat`是日期/时间格式化子类的抽象类，通过这个类可以完成日期和文本之间的转换       
也就是可以在Date对象与String对象之间进行来回转换      
标识字母--含义    
> y--年    
> M--月    
> d--日    
> H--时    
> m--分    
> s--秒    
#### 第一种用法: 正向  
```Java
package to.today.my07;
import java.util.Date;
import java.text.SimpleDateFormat;
import java.text.ParseException;
import java.text.DateFormat;

public class test_calender {
    public static void main(String[] args) throws ParseException{
        DateFormat df = new SimpleDateFormat("yyyy年MM月dd日 HH时mm分ss秒");
        String str = "2020年2月5日 14时51分56秒";
        Date date_chane = df.parse(str);
        System.out.println(date_chane); //Wed Feb 05 14:51:56 CST 2020
    }
}
```
#### 第二种用法: 反向   
```Java
package to.today.my07;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.text.DateFormat;
import java.text.ParseException;

 class test_date {
     public static void main(String[] args) throws ParseException{
         DateFormat df = new SimpleDateFormat("yyyy年MM月dd日");
         String str = "2020年2月4日";
         Date date_change = df.parse(str);
         System.out.println("This is date_change: "+date_change);
                            //Tue Feb 04 00:00:00 CST 2020
}
```
### 3. Calendar类
`java.util.Calendar` 是日历类，在Date后出现，替换掉了许多Date的方法。  
该类将所有可能用到的时间信息封装为静态成员变量，方便获取。 日历类就是方便获取各个时间属性的   
使用方法:  
```Java
package to.today.my07;
import java.util.Calendar;
public class test_calender {
    public static void main(String[] args){
        System.out.println("程序入口");
        Calendar cal = Calendar.getInstance();
        // System.out.println(cal); //一堆数据
        int year = cal.get(Calendar.YEAR);
        int month = cal.get(Calendar.MONTH);
        int daily = cal.get(Calendar.DAY_OF_MONTH);
        System.out.println(year+" : "+month+" : "+daily);
        //2020 : 1 : 5
    }
}
```
#### Calendar数据, 需要什么, 就get什么即可:      
```
/*java.util.GregorianCalendar
[time=1580885583756,
areFieldsSet=true,
areAllFieldsSet=true,
lenient=true,
zone=sun.util.calendar.ZoneInfo
[id="Asia/Shanghai",
offset=28800000,
dstSavings=0,
useDaylight=false,
transitions=19,
lastRule=null],
firstDayOfWeek=1,
minimalDaysInFirstWeek=1,
ERA=1,
YEAR=2020,MONTH=1,            //YEAR--MONTH
WEEK_OF_YEAR=6,WEEK_OF_MONTH=2,
DAY_OF_MONTH=5, 		      //DAY_OF_MONTH
DAY_OF_YEAR=36,
DAY_OF_WEEK=4,
DAY_OF_WEEK_IN_MONTH=1,
AM_PM=1,HOUR=2,
HOUR_OF_DAY=14,
MINUTE=53,
SECOND=3,
MILLISECOND=756,
ZONE_OFFSET=28800000,
DST_OFFSET=0]
 */
```
#### 设置里面默认数据方法:   
```
package to.today.my07;
import java.util.Calendar;
public class test_calender {
    public static void main(String[] args){
        Calendar cal = Calendar.getInstance();
        int year = cal.get(Calendar.YEAR);
        int month = cal.get(Calendar.MONTH);
        int daily = cal.get(Calendar.DAY_OF_MONTH);
        System.out.println(year+" : "+month+" : "+daily);
        //2020 : 1 : 5
        cal.set(Calendar.YEAR, 2050);
        int year1 = cal.get(Calendar.YEAR);
        System.out.println(year1); //2050
    }
}
```
#### add方法, 对日历字段的值进行加减操作: 
```Java
package to.today.my07;
import java.util.Calendar;
public class test_calender {
    public static void main(String[] args){
        Calendar cal = Calendar.getInstance();

        cal.set(Calendar.YEAR, 2050);
        int year1 = cal.get(Calendar.YEAR);
        System.out.println(year1);  // 2050

        cal.add(Calendar.YEAR, +3);
        int year2 = cal.get(Calendar.YEAR);
        System.out.println(year2);  // 2053
    }
}
```
#### gerTime方法, 拿到Date对象:  
```
package to.today.my07;
import java.util.Calendar;
import java.util.Date;

public class test_calender {
    public static void main(String[] args){
        Calendar cal = Calendar.getInstance();
        Date date1 = cal.getTime();
        System.out.println(date1); //Wed Feb 05 16:01:31 CST 2020
    }
}
```



## 三、System类
### 1. currentTimeMillis方法   
使用方法:   
```Java
//1970年01月01日00:00点之间的毫秒差值
package to.today.my07;
import java.util.Date;
public class test_system {
    public static void main(String[] args){
        System.out.println("入口");
        System.out.println(System.currentTimeMillis()); 
        //1580889904187
    }
}
```
### 2. arraycopy方法:  将数组中指定的数据拷贝到另一个数组中   






## 四、StringBuilder类




## 五、包装类



