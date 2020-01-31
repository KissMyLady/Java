语句控制  
====
<!-- GFM-TOC -->
* [一、If-else语句使用](#一If-else语句使用)
* [二、三元运算与else-if语句](#二三元运算与else-if语句)
* [三、Switch语句](#三Switch语句)
* [四、For循环](#四For循环)
* [五、While语句](#五While语句)
* [六、Do-while语句](#六Do-while语句)
<!-- GFM-TOC -->



### 一、If-else语句使用
```Java
package to.today.my04;

public class test2 {
    public static void main(String[] args){
        int source = 100;

        if (source >=90 && source==100){
            System.out.println("你他娘的真是个人才");
        }
        else if (source >= 80){
            System.out.println("吃干饭的?");
        }
        else if (source >= 70){
            System.out.println("生死由命, 富贵在天");
        }
        else if (source >= 70){
            System.out.println("饭桶");
        }
        else if (source >= 60){
            System.out.println("继续板砖吧");
        }
        else if (source <= 59){
            System.out.println("有巨大的成长空间, 加油");
        }
        else {
            System.out.println("神知道要对你说什么话, 处理边界条件");
        }
    }
}

```
### 二、三元运算与else-if语句
```Java
package to.today.my04;

public class max {
    public static void main(String[] args){
        int a = 100;
        int b = 5;

        int max = a < b ? 999: 666;
        System.out.println(max);

        if (a >= b){
            max = a;
            System.out.println(a);
        }
        else {
            max = a;
            System.out.print(b);
        }
        System.out.println(max);
    }
}
```
### 三、Switch语句 
```Java
package to.today.my04;

public class switch1 {
    public static void main(String[] args){
        int num = 7;
        switch (num){
            case 1:
                System.out.println("星期一");
                break;
            case 2:
                System.out.println("星期二");
                break;
            case 3:
                System.out.println("星期三");
                break;
            case 4:
                System.out.println("星期四");
                break;
            case 5:
                System.out.println("星期五");
                break;
            default:
                System.out.println("休息日");
                break;
        }
    }
}
```
#### switch语句使用的注意事项：
* 1. 多个case后面的数值不可以重复。   

* 2. switch后面小括号当中只能是下列数据类型：   
基本数据类型: byte/short/char/int
引用数据类型: String字符串、enum枚举

* 3. switch语句格式可以很灵活：前后顺序可以颠倒，而且break语句还可以省略。   
“匹配哪一个case就从哪一个位置向下执行，直到遇到了break或者整体结束为止。”    

### 四、For循环
```Java
package to.today.my04;

public class for_end {
    public static void main(String[] args){
        for (int i = 1; i <=100; i++){
            System.out.println("今天很安静, 没有发生事情"+i);
        }
        System.out.println("最近都很安静");
    }
}
```

### 五、While语句  
```Java
package to.today.my04;

public class test_while {
    public static void main(String[] args){
        for (int i =1; i<=10; i++){
            System.out.println("Do something"+i);
        }
        int b = 1;
        while (b<10){
            b += 1;
            // b++;
            System.out.println("现在b的值是: "+b);
        }
        System.out.println("结束程序");


        byte cc = 1;
        cc ++;
        System.out.println(cc);
        cc += 1;
        System.out.println(cc);
    }
}
```

### 六、Do-while语句
```Java
package to.today.my04;

public class test_do_while {
    public static void main(String[] args){
        System.out.println("开始程序");

        int nums = 1;
        while (nums <= 10){
            System.out.println("此时的nums是: "+nums);
            nums++;
        }

        int mylady = 1;
        do {
            System.out.println("如果重来你会不会爱我: "+mylady);
            mylady++;
        }
        while (mylady<=10);
    }
}
```
1. 如果条件判断从来没有满足过，那么for循环和while循环将会执行0次，但是Do-while循环会执行至少一次。   
2. for循环的变量在小括号当中定义，只有循环内部才可以使用。   
3. while循环和do-while循环初始化语句本来就在外面，所以出来循环之后还可以继续使用。     

```Java
package to.today.my04;
 
public class test_do_diffirrent {
    public static void main(String[] args){
        System.out.println("程序入口");

        for (int b =1; b<10; b++){
            System.out.println(b);
        }
        // System.out.println(b);
        int dd = 1;
        do {
            System.out.println(dd);
            dd++;
        }while (dd<=5);

        System.out.println("这是do-while外边, 现在输出dd: "+dd);
    }
}
```
这里的最后一个输出了6, 在do-while语句下, 变量可以成为外面的全局变量      

#### continue与break与Python用法相同, 放在语句下即可  


### While ture  
注意Java中的ture是小写   
```Java
package to.today.my04;

public class test_while_true {
    public static void main(String[] args){
        System.out.println("程序入口");

        while (true){
            System.out.println("死循环");
        }
    }
}
```



