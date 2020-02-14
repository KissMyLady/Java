扩展知识--单例设计模式 
======
### 引导知识理解: 
1. 设计模式: 早期见诸领域, 盖楼, 有规律可循, 常用的规律总结出来, 备案资料.
2. 软件设计中, 找到很多模式(解决问题有效的方法) GOF四人帮, 有很多书, '设计模式'
3. 设计模式, 偏纯思想, 在不断劳动过程中, 总结出来的规律, 语言通用
4. 有一个比较复杂的业务需求, 在实际中运用的 

### 生活中的模式:  
老师建议: 总结学习方法, 总结Java学习方法, 特有效果, 你有用, 别人也有用, 这就是学习Java的设计模式   
1. 吃饭模式(有两根棍子就可以), 西方(刀叉)  
> 勺, 叉只是表现形式的一种,, 没有一样可以吃  
#### 设计模式: 解决某一问题最行之有效的方法, Java有24种, 单例是1种  
* 单例:  解决一个类在内存中只存在一个对象   

## 单 例   
我建立好了给你用, 你不能建立, 这样就保证了单一 
#### 保证对象唯一
1. 为避免过多建立对象, 先禁止其他程序建立该对象
2. 还为了让 其他程序可以访问到该类对象, 只好在本类中, 自定义一个对象
3. 为了方便访问, 可以提供访问方式

1. 私有化
2. 创建本类对象
3. 提供方法可以获取到该对象

```Java 
package my03;
class Single{
    private Single(){
        System.out.println("There is do something");
    }
    private static Single s1 = new Single();

    public static Single getInstance(){
        return s1;
    }
}

public class one_demo {
    public static void main(String[] args){
        Single ss = Single.getInstance();
        System.out.println(ss);//my03.Single@75412c2f
    }
}
```
## [Java实现单例的5种方式](https://blog.csdn.net/u014672511/article/details/79774847)  
如何实现单例模式
### 1. 饿汉模式
立即加载，一般情况下再调用getInstancef方法之前就已经产生了实例，也就是在类加载的时候已经产生了。   
这种模式的缺点很明显，就是占用资源，当单例类很大的时候，其实我们是想使用的时候再产生实例。   
因此这种方式适合占用资源少，在初始化的时候就会被用到的类。   
```Java
package my03;
class Singles {
    private static Singles s = new Singles();
    private Singles(){}
    public static Singles getInstance() {
        return s;
    }
}

public class single {
    public static void main(String[] args){
        System.out.println("Enter");
        System.out.println(Singles.getInstance());
    }
}

```

### 2. 懒汉模式











