方法入门
===

> 我们在学习运算符的时候，都为每个运算符单独的创建一个新的类和main方法，我们会发现这样编写代码非常的繁琐，而且重复的代码过多。   

#### 能否避免这些重复的代码呢?        

就需要使用方法来实现    

### 方法： 就是将一个功能抽取出来，把代码单独定义在一个区域内(大括号内)，形成一个单独的功能。  
> 当我们需要这个功能的时候，就可以去调用。    
> 这样即实现了代码的复用性，也解决了代码冗余的现象。     


格式模板: 
```
修饰符 返回值类型 方法名 (参数列表) {
     代码...        
    return ;     
}
```
定义格式解释:  
* 修 饰: 目前固定写法  public static   
* 返回值类型: 目前固定写法 void , 其他返回值类型在后面的课程讲解。   
* 方法名: 为我们定义的方法起名, 满足标识符的规范，用来调用方法。  
* 参数列表: 目前无参数, 带有参数的方法在后面的课程讲解。  
* return: 方法结束。 因为返回值类型是void(虚空)，方法大括号内的return可以不写。   
```Java
package to.today.to.todat.my03;

public class method {
    public static void main(String[] args){
        System.out.println("This is main");
        method();
    }

    public static void method(){
        System.out.println("自己创建的方法, 需要main函数调用run");
    }
}
```
很明显的发现, java需要一个mian入口, 在下面写方法, 格式与上一样`public static void method(){do something}`

写好后, 在main函数里面写入函数名即可, 应该还可以这样:   
```Java
package to.today.to.todat.my03;

public class method {
    public static void method(){
        System.out.println("自己创建的方法, 需要main函数调用run");
    }

    public static void main(String[] args){
        System.out.println("This is main");
        method();
    }
}
```
先定义方法`method`,  在写好方法后, 再调用, 即: `先买票, 后上车`的思路     








