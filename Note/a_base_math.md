5类运算方法
====

## 1. 算数运算符
![ScreenShot-00359](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00359.jpg)  

### Java中，整数使用以上运算符，无论怎么计算，也不会得到小数。
```Java
package to.today.my02;

public class math {
    public static void main(String[] args){
        int a = 10;
        int b = 3;
        System.out.println(a/b); // 3
    }
}

```
`++`运算，变量自己增长1。 反之，`--`运算，变量自己减少1，用法与`++`一致。   

独立运算：
变量在独立运算时， 前`++`和 后`++`没有区别     

混合运算：   
和其他变量放在一起， 前`++`和 后`++`就产生了不同。       
变量 前`++`: 变量a自己加1，将加1后的结果赋值给b，也就是说a先计算。a和b的结果都是2。   

### 第一种混合运算:　
```Java
package to.today.my02;

public class math {
    public static void main(String[] args){
        int aa = 1;
        int bb = ++aa;
        System.out.println(aa);  // 2
        System.out.println(bb);  // 2
    }
}
```
### 第二种混合运算:  
```Java
package to.today.my02;

public class math {
    public static void main(String[] args){
        int aaa = 1;
        int bbb = aaa++;
        System.out.println(aaa); // 2
        System.out.println(bbb); // 1
    }
}
```
* 变量a先把自己的值1，赋值给变量b，此时变量b的值就是1，变量a自己再加1       
  
### `+`符号在字符串中的操作：  
`+`符号在遇到字符串的时候，表示连接、拼接的含义。   
"a"+"b" 的结果是“ab”，连接含义    
```Java
package to.today.my02;
public class math {
    public static void main(String[] args){
        System.out.println("5+5="+5+5);  // 5+5=55
    }
}
```


## 2. 赋值运算符
![ScreenShot-00360](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00360.jpg)  


## 3. 比较运算符    
![ScreenShot-00361](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00361.jpg)  
比较运算符，是两个数据之间进行比较的运算，运算结果都是布尔值 true 或者 false   
```Java
public static void main(String[] args) {
    System.out.println(1==1); // true
    System.out.println(1<2);  // true
    System.out.println(3>4);  // false
    System.out.println(3<=4); // true
    System.out.println(3>=4); // false
    System.out.println(3!=4); // true
}
```


## 4. 逻辑运算符   
![ScreenShot-00362](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00362.jpg)  
逻辑运算符，是用来连接两个布尔类型结果的运算符，运算结果都是布尔值 true 或者 false   
```Java
public static void main(String[] args)  {
    System.out.println(true  && true);  //true
    System.out.println(true  && false); //false
    System.out.println(false && true);  //false，右边不计算
 
    System.out.println(false || false); //falase
    System.out.println(false || true);  //true
    System.out.println(true  || false); //true，右边不计算
 
    System.out.println(!false); //true
}
```

## 5. 三元运算符   
```Java
package to.today.my02;
	public class three_basic {
    public static void main(String[] args){
        int a =(1==2 ? 100 : 200);
        System.out.println(a);

        int b =(1==1 ? 100 : 200);
        System.out.println(b);
    }
}


