【Collection、泛型】   
====

<!-- GFM-TOC -->
* [一、Collection集合](#一Collection集合)
* [二、Iterator迭代器](#二Iterator迭代器)
* [三、泛型](#三泛型)
* [四、集合综合案例](#四集合综合案例)
<!-- GFM-TOC -->

# 一、Collection集合
### 1. 集合概述: [集合]()是java中提供的一种容器，可以用来存储多个数据。
集合和数组既然都是容器，啥区？ 
* 1. 数组`[]`的长度是固定的。   
* 2. 集合的长度是可变的。     

数组中存储的是同一类型的元素，可以存储基本数据类型值。 
#### 集合存储的都是对象。而且对象的类型可以不一致。 在开发中一般当对象多的时候，使用集合进行存储。   

### 2. 集合框架   
JAVASE提供了满足各种需求的API，在使用这些API前，先了解其继承与接口操作架构，才能了解何时采用哪个类，以及类之间如何彼此合作，从而达到灵活应用。   

集合按照其`存储结构`可以分为两大类，分别是单列集合`java.util.Collection`和双列集合`java.util.Map`   
主要学习 Collection 集合，Map集合。     
* Collection单列集合类的根接口, 用于存储一系列符合某种规则的元素, 它有两个重要的子接口，分别是java.util.List 和 java.util.Set   
** 其中, List 的特点是元素有序、元素可重复。 Set 的特点是元素无序，而且不可重复(类似于字典)。     
List 接口的主要实现类有 java.util.ArrayList 和 java.util.LinkedList, Set 接口的主要实现类有 java.util.HashSet 和 java.util.TreeSet   

从上面的描述可以看出JDK中提供了丰富的集合类库, 为了便于初学者进行系统地学习,  接下来通过一张图来描述整个集合类的继承体系。        
![ScreenShot-00381](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00381.jpg)       
橙色写的都是接口类型，而蓝色写的都是具体的实现类。   
* 集合本身是一个工具，它存放在java.util包中。 在Collection接口定义着单列集合框架中最最共性的内容    

### 3. Collection 常用功能
#### Collection是所有`单列集合的父接口`，因此在Collection中定义了单列集合(List和Set)通用的一些方法，这些方法可用于操作所有的单列集合。   
方法如下：      
* public boolean add(E e): 添加     
* public void clear(): 清空     
* public boolean remove(E e): 指定删除        
* public boolean contains(E e): 判断是否包含     
* public boolean isEmpty(): 判断是否为空     
* public int size(): 个数     
* public Object[] toArray(): 把集合中的元素，存储到数组中     
#### 实例:  
```Java
package to.today.my08;
import java.util.ArrayList;
import java.util.Collection; 
public class text_collection {
    public static void main(String[] args){
        System.out.println("入口");
        Run();
    }
    private static void Run(){
        Collection<String> coll = new ArrayList<String>();

        coll.add("乔峰");
        coll.add("萧峰");
        coll.add("神仙姐姐");
        coll.add("扫地僧");
        System.out.println(coll);

        System.out.println(coll.contains("虚竹")); //false
        System.out.println(coll.remove("段誉"));   //false
        System.out.println(coll.size());  //4

        Object[] arry = coll.toArray();
        for (int i=0;i<arry.length;i++){
            System.out.println(arry[i]);
        }
        coll.clear();
        System.out.println(coll.isEmpty()); //true
    }
}
```

# 二、Iterator迭代器
在程序开发中，经常需要遍历集合中的所有元素。   
针对这种需求，JDK专门提供了一个接口`java.util.Iterator`     
Iterator 接口也是Java集合中的一员，但它与 Collection 、 Map 接口有所不同，Collection 接口与 Map 接口主要用于存储元素，而 Iterator 主要用于迭代访问（即遍历） Collection 中的元素，因此 Iterator 对象也被称为迭代器。[Python中的迭代器](https://github.com/KissMyLady/Python/blob/master/Nont/py_iterable.md)   


想要遍历Collection集合，那么就要获取该集合迭代器完成迭代操作，下面介绍一下获取迭代器的方法:    
* `public Iterator iterator()`: 获取集合对应的迭代器，用来遍历集合中的元素的。

#### 迭代:  即Collection集合元素的通用获取方式。在取元素之前先要判断集合中有没有元素，如果有，就把这个元素取出来，继续在判断，如果还有就再取出出来。 一直把集合中的所有元素全部取出。   

### 1. Iterator接口的常用方法如下：
* `public E next()`: 返回迭代的下一个元素   
* `public boolean hasNext()`: 如果仍有元素可以迭代，则返回true。   
实 例:   
```Java
package to.today.my08;
import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;
public class test_iterator {
    public static void main(String[] args){
        Iterator();
    }
    private static void Iterator(){
        Collection<String> coll = new ArrayList<String>();
        coll.add("逻辑");
        coll.add("维德");
        coll.add("智子");
        coll.add("程心");
        Iterator<String> it = coll.iterator();
        while (it.hasNext()){
            String s = it.next();
            System.out.println(s);
        }
    }
}
```
tips:：在进行集合元素取出时，如果集合中已经没有元素了，还继续使用迭代器的next方法，将会发生
`java.util.NoSuchElementException`没有集合元素的错误。  


### 2. 迭代器的实现原理   
#### 当遍历集合时，首先通过调用t集合的iterator()方法获得迭代器对象，然后使用hashNext()方法判断集合中是否存在下一个元素，如果存在，则调用next()方法将元素取出，否则说明已到达了集合末尾，停止遍历元素。     

Iterator迭代器对象在遍历集合时，内部采用指针的方式来跟踪集合中的元素     
  
> 在调用Iterator的next方法之前，迭代器的索引位于第一个元素之前，不指向任何元素    
> 当第一次调用迭代器的next方法后，迭代器的索引会向后移动一位，指向第一个元素并将该元素返回    
> 当再次调用next方法时，迭代器的索引会指向第二个元素并将该元素返回      
> 依此类推，直到hasNext方法返回false，表示到达了集合的末尾，终止对元素的遍历      

### 3. 增强For   
增强for循环(也称for each循环)是JDK1.5以后出来的一个高级for循环，专门用来遍历数组和集合的。   
它的内部原理其实是个Iterator迭代器，所以在遍历的过程中，不能对集合中的元素进行增删操作    
#### [for循环实例](https://github.com/KissMyLady/Java/blob/master/Note/b_base_grammar.md#%E5%9B%9BFor%E5%BE%AA%E7%8E%AF)   



# 三、泛型
### 1. 泛型概述: 
学习集合时，我们都知道集合中是可以存放任意对象的，只要把对象存储集合后，那么这时他们都会被提升成Object类型。

当我们在取出每一个对象，并且进行相应的操作，这时必须采用类型转换    
观察这段代码:   
```Java
public class GenericDemo {
	public static void main(String[] args){    
		Collection coll = new ArrayList();        
		coll.add("abc");        
		coll.add("itcast");        
		coll.add(5); //由于集合没有做任何限定，任何类型都可以给其中存放       
		 
		Iterator it = coll.iterator();        
		while(it.hasNext()){        
			//需要打印每个字符串的长度,就要把迭代出来的对象转成String类型            
			String str = (String) it.next();            
			System.out.println(str.length());            
		}                  
	}   
}
```
程序在运行时发生了问题`java.lang.ClassCastException`。 为什么会发生类型转换异常呢？
 
分析下：由于集合中什么类型的元素都可以存储。 导致取出时强转引发运行时 ClassCastException。 

怎么来解决这个问题呢？
Collection虽然可以存储各种对象，但实际上通常Collection只存储同一类型对象。  

例如都是存储字符串对象。 因此在JDK5之后，新增了泛型(Generic)语法，让你在设计API时可以指定类或方法支持泛型，这样我们使用API的时候也变得更为简洁，并得到了编译时期的语法检查。  

#### 泛型: 可以在类或方法中预支地使用未知的类型。   
* tips: 一般在创建对象时，将未知的类型确定具体的类型。 当没有指定泛型时，默认类型为Object类型。  
### 3. 使用泛型的好处
* 将运行时期的ClassCastException, 转移到了编译时期变成了编译失败。  
* 避免了类型强转的麻烦   



# 四、集合综合案例



