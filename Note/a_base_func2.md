函数规则2 
====
<!-- GFM-TOC -->
* [一、函数规则](#一函数规则)
* [二、组合函数](#二组合函数)
* [三、Java实现乘法表](#三Java实现乘法表)
<!-- GFM-TOC -->


## 一、函数规则    
```Java
package to.today.my05;

public class test_list {
    public static void main(String[] args){
    	System.out.println("程序入口");
    	getNum(5)
    }
    public static void getNum(int num){
    	System.out.println(num*3 +5);
    	return;
    }
}
```
####　第二种方式: 类启动  
```Java
package to.today.my05;

class GetFunction
{
    public static void main(String[] args){
        System.out.println("程序入口");
        getNum(5);
    }
    public static void getNum(int num){
        System.out.println(num *3 +5);
        return;
	}
}
```

## 二、组合函数
```Java
package to.today.my05;

class test_func3 {
    public static void main(String[] args){
        System.out.println("程序入口处");

        int x = getSum(4, 5);
        int y = getSum(10, 11);
        System.out.println(getMax(x, y));
    }

    public static int getSum(int a, int b){
        return a +b;
    }

    public static boolean juje(int b, int l){
        return b == l;
    }

    public static int getMax(int a, int b){
        return (a>b)?a:b;
    }
}
```


## 三、Java实现乘法表 
```Java
package to.today.my05;

class test_func5 {
    public static void main(String[] args){
        System.out.println("程序入口");
        print99();
    }

    public static void print99(){
        for (int a=1; a<10; a++){   // for i in range(9)
            for (int b=1; b<=a; b++){
                System.out.print(a+"*"+b+ "="+ a*b+"\t");
            }
            System.out.println();
        }
    }

}
```
注意, 这里的打印用的`print`, 而不是`println`    
#### 区 别:    
print打印出来的内容是不能够自动换行的，而println可以   
相比于Python, Python可只用调用一个函数`print()`, 在里面添加参数`end=""`来控制换行与否      

#### 看到这里的代码, 我才知道原来Java不是一个特立独行的语言, 打印方式还是很多元化, 原来`println`不是为了花狸狐哨而创建的      



