静态代码块
===
要求: 基本了解就行 

格式: 
```Java
static {
	静态代码块中的执行语句
}

class StaticCode{
	static {
		System.our.println("A");
	}
}
```
特点: 随着类的加载而执行, 只执行一次   
用于: 初始化

## 类初始化只执行一次实 例:  
```Java
package to.today.my06;
class test_bobo {
    static {
        System.out.println("a");
    }
}

class StaticCodeDemo{
    static {
        System.out.println("b");
    }

    public static void main(String[] args){
        new test_bobo();
        new test_bobo();
        System.out.println("over");
    }

    static {
        System.out.println("c");
    }
}
// b c a over
```
`new test_bobo();`为什么只执行一次:  
> 1. 加载进内存     
> 2. 执 行      
> 3. 不执行, 因为类已经在内存了, 不会被加载了        


# 静态初始化过程 
### 构造代码块`{}`优先级高于构造函数`PersonP{}`    
Person代码块:  
```Java
package my02;
class Person
{
    private String name; 
  //private String name = "haha";
    private int age;
    private static String county ="cn";

    Person(String name, int age)
    {
        this.name = name;
        this.age = age;
    }
    {
        System.out.println(name+"...."+age);
    }

    public void setName(String name)
    {
        this.name = name;
    }
    public void setAge(int age)
    {
        this.age = age;
    }

    public void speak()
    {
        System.out.println(this.name+"..."+this.age);
    }

    public static void showCounty()
    {
        System.out.println("county= "+county);
    }
}
```
Main代码块:    
```Java
package my02;
public class test_person {
    public static void main(String[] args){
        System.out.println("Enter");
        Person p1 = new Person("貂蝉", 18);
    }
}
```
## 全过程:  
1. 先找到Person.class文件加载到内存;   
2. 执行static, 没有继续    
3. 开辟内存空间   
4. 在堆内存中建立对象的特有属性, 并默认初始化   
5. 对 属性进行显示初始化   
6. 构造代码块  
7. 构造函数初始化  
8. 内存地址赋值给栈内存中的P  


