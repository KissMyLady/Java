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

