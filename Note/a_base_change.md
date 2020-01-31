基本数据类型转换之向上转型和向
==========

## 1. 自动转换
自动转换: 将取值范围小的类型 `自动提升`为 取值范围大的类型   
例 子: 
```Java
package to.today.my02;

public class change_int {
    public static void main(String[] args){
        int a = 100;
        byte b = 2;

        int c = a + b;
        // byte x = a + b;  Error
        System.out.println(c);
    }
}
```
同样道理，当一个 int 类型变量和一个 double 变量运算时， int 类型将会自动提升为 double 类型进行运算    
```Java
package to.today.my02;

public class change_int {
    public static void main(String[] args){
        int a = 100;
        double b = 2;

        double c = a + b;
        System.out.println(c);
    }
}
```
## 2. 转换规则: 
* 容量小的类型可自动转换为容量大的数据类型；
#### byte,short,char → int → long → float → double
* byte，short，char之间不会相互转换，他们在计算时首先会转换为int类型。
#### boolean 类型是不可以转换为其他基本数据类型。

## 3. 强制转换   
```Java
package to.today.my02;

public class change_int {
    public static void main(String[] args){
        int xx = (int)5.5;
        System.out.println(xx);

        short ss = 1;
        // ss = ss + 1;
        ss = (short)(ss + 1);
        System.out.println(ss);
    }
}
```
### 注意: 
* 浮点转成整数，直接取消小数点，可能造成数据损失精度。   
* int 强制转成 short 砍掉2个字节，可能造成数据丢失。   
```Java
package to.today.my02;

public class change_int {
    public static void main(String[] args){
        short abc = 32767;  // 定义范围内最大值
        ss = (short)(abc + 10); // 运算后，强制转换，砍掉2个字节后会出现不确定的结果
        System.out.println(ss);
    }
}
```
输出:  
`-32759`

总 结: 类型转化
小转大, 自动 自动类型转换(隐式类型转换)  
大转小, 强转 强制类型转换(显式类型转换) 
