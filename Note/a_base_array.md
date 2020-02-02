数组Array   
=====
<!-- GFM-TOC -->
* [一、数组定义和访问](#一数组定义和访问)
* [二、数组原理内存图](#二数组原理内存图)
* [三、数组的常见操作](#三数组的常见操作)
* [四、数组的常见操作](#四数组的常见操作)
<!-- GFM-TOC -->

## 一、数组定义和访问
### 1. 需 求:     
现在需要统计某公司员工的工资情况，例如计算平均工资、找到最高工资等。
假设该公司有50名员工，用前面所学的知识，程序首先需要声明50个变量来分别记住每位员工的工资，   
然后在进行操作，这样做会显得很麻烦，而且错误率也会很高。   
因此我们可以使用容器进行操作。 #### 将所有的数据全部存储到一个容器中，统一操作(很像list)       

#### 2. 容 器: 将多个数据存储到一起，每个数据称为元素。 
* 生活中的容器: 水杯，衣柜，教室   

#### 3. 数组: 数组就是存储`数据长度固定`的容器，保证多个数据的`数据类型一致`。     

### 4. 定义一个数组的三种方式      
第一种方法: 定义可以存储3个整数的数组容器    
```Java
int[] arr = new int[3];
```
第二种方法: 定义存储12345整数的数组容器       
```Java
int[] arr = new int[]{1,2,3,4,5};
```
第三种方法: 定义存储`12345`整数的数组容器      
```Java
int[] ajj = {1,2,3,4,5};
```
### 5. 友好访问  
#### 1. 长度访问:  
```Java
int[] ayy = new int [3];
System.out.println("This is length: "+ayy.length);  //This is length: 3
```
#### 2. 访问数组中元素:   
```Java
package to.today.my06;

class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = new int[]{1, 2, 3, 4};
        ayy[0] = 100;
        System.out.println(ayy[0]);  // 100
    }
}
```    
#### 3. 索引访问:   
```Java
package to.today.my06;

class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = new int[]{1, 2, 3, 4};
        System.out.println(ayy);

        ayy[0] = 100;
        System.out.println(ayy[0]);

        int b = ayy[2];
        System.out.println(b);  //3
    }
}
```
## 二、数组原理内存图   
#### 1. 内存概述
> 内存是计算机中的重要原件，临时存储区域，作用是运行程序。     
> 我们编写的程序是存放在硬盘中的，在硬盘中的程序是不会运行的，必须放进内存中才能运行，运行完毕后会清空内存   
Java虚拟机要运行程序，必须要对内存进行空间的分配和管理。   

### 2. Java虚拟机的内存划分   
为了提高运算效率，就对空间进行了不同区域的划分，因为每一片区域都有特定的处理数据方式和内存管理方式   
* JVM 的内存划分   
| 区域名称  | 作用  |    
| :---: | --- |      
| 寄存器 | 给CPU使用，和我们开发无关 |    
| 本地方法栈 | JVM在使用操作系统功能的时候使用，和我们开发无关 |    
| 方法区 | 存储可以运行的class文件 |      
| 堆内存 | 存储对象或者数组，new来创建的，都存储在堆内存 |    
| 方法栈 | 方法运行时使用的内存，比如main方法运行，进入方法栈中执行 |    

### 3. 数组在内存中的存储  
#### 一、一个数组内存图   
```Java
package to.today.my06;

class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = new int[]{1, 2, 3, 4};
        System.out.println(ayy);  //[I@50cbc42f
    }
}
```
这一坨是什么呢?  #### 是数组在内存中的地址。   
new出来的内容，都是在堆内存中存储的，而方法中的变量arr保存的是数组的地址     
#### 打印`arr[0]`, 就会输出arr保存的内存地址中数组中0索引上的元素   
![ScreenShot-00371](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00371.jpg)  

#### 二、两个数组内存图   
```Java
package to.today.my06;

class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = new int[2];
        int[] ajj = new int[3];

        System.out.println(ayy);  //[I@50cbc42f
        System.out.println(ajj);  //[I@75412c2f
    }
}
```
![ScreenShot-00372](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00372.jpg)  

  
#### 三、两个变量指向一个数组   
```Java
package to.today.my06;

class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = new int[2];
        int[] ajj = new int[3];

        System.out.println(ayy);  //[I@75412c2f
        System.out.println(ajj);  //[I@282ba1e

        int[] app = new int[4];
        app[0] = 0;
        app[1] = 1;
        app[2] = 2;
        app[3] = 3;

        System.out.println(app[0]);  //0
        System.out.println(app[1]);  //1
        System.out.println(app[2]);  //2
        System.out.println(app[3]);  //3

        int[] appp = app;
        appp[0] = 6666;
        System.out.println(app[0]);  // 6666
        System.out.println(appp[0]); // 6666

    }
}
```
![ScreenShot-00373](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00373.jpg)   
可以理解为地址引用   


## 三、数组的常规操作   
### 1. 数组越界异常   
```Java
package to.today.my06;

class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = new int[5];

        System.out.println(ayy[5]);
    }
}
```
错误提示:   
```
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 5
	at to.today.my06.test_arry2.main(test_arry1.java:8)
```

### 2. 数组空指针异常   
```Java
package to.today.my06;
class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = new int[5];

        ayy = null;
        System.out.println(ayy);    // null
        System.out.println(ayy[0]);
    }
}
```
错误提示:    
```
Exception in thread "main" java.lang.NullPointerException
	at to.today.my06.test_arry2.main(test_arry1.java:10)
```
空指针异常在内存图中的表现:   
![ScreenShot-00374](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00374.jpg)   

### 3. 数组遍历   
数组遍历: 数组中的每个元素分别获取出来，就是遍历    
无脑遍历法:   
```Java
package to.today.my06;
class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = {1,2,3,4,5};
        System.out.println(ayy[0]);  //1
        System.out.println(ayy[1]);  //2
        System.out.println(ayy[2]);  //3
        System.out.println(ayy[3]);  //4
        System.out.println(ayy[4]);  //5
    }
}
```
### 升级版方法:  
```
package to.today.my06;
class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = {1,2,3,4,5};
        System.out.println(ayy[0]);  //1
        System.out.println(ayy[1]);  //2
        System.out.println(ayy[2]);  //3
        System.out.println(ayy[3]);  //4
        System.out.println(ayy[4]);  //5

        System.out.println("=========");  //5

        for (int a=0; a< ayy.length; a++){
            System.out.println(ayy[a]);
        }
    }
}
```
### 4. 数组获取最大值元素
![ScreenShot-00376]()   
```Java
package to.today.my06;
class test_arry2 {
    public static void main(String[] args){
        int[] ayy = {-5, 15, 2000, 500, 10000, 100, 4000};

        int max = ayy[0];

        for (int i=0; i<ayy.length;i++){
            if (ayy[i] > max){
                max = ayy[i];
            }
        }
        System.out.println(max);
    }
}
```

### 5. 数组反转  
```Java
package to.today.my06;
class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = new int[]{50, 80, 90, 100, 200, 400};

        for (int min=0, max=ayy.length-1; min<=max; min++, max--){
            int temp = ayy[min];  //桥
            ayy[min] = ayy[max];
            ayy[max] = temp;
        }

        for (int i=0; i<ayy.length; i++){
            System.out.println(ayy[i]);
        }

    }
}
```




## 四、数组的常见操作   
* 1. 数组作为方法参数传递，传递的参数是数组内存的地址    
```Java
package to.today.my06;
class test_arry2 {
    public static void main(String[] args) {
        int[] ayy = new int[]{1,2,3,4,5};
        getArray(ayy);
    }

    public static void getArray(int[] array) {
        for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);
        }
    }
}
```
* 2. 数组作为方法返回值
```Java
package to.today.my06;
class test_arry2 {
    public static void main(String[] args){
        int[] agg = getArray();
        for (int i=0; i<agg.length; i++){
            System.out.println(agg[i]);
        }

    }
    public static int[] getArray(){
        int[] arry =  {1,2,3,4,5,6};
        return arry;
    }
}
```

* 3. 方法的参数类型区别
```Java
package to.today.my06;
class test_arry2 {
    public static void main(String[] args) {
        int a = 5, b = 99;
        System.out.println(a);  //5
        System.out.println(b);  //99
        change(a, b);  //
        System.out.println(a);  //5
        System.out.println(b);  //99
    }

    public static void change(int a, int b){
        a = a + b;
        b = b + a;
        System.out.println(a);   // 5+99 = 104
        System.out.println(b);   // 99 +104 = 203
    }
}
```
这 种:  
```Java
package to.today.my06;
class test_arry2 {
    public static void main(String[] args) {
        int a = 5, b = 99;
        System.out.println(a);  //5
        System.out.println(b);  //99
        change(a, b);  //
        System.out.println(a);  //5
        System.out.println(b);  //99
    }

    public static void change(int a, int b){
        a = a + b;
        b = b + a;
        System.out.println(a);   // 5+99 = 104
        System.out.println(b);   // 99 +104 = 203

    }
}
```
