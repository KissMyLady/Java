## 网络编程
网络编程就是 `socket编程 `     
###### 端口: 有效端口：`0~65535`，其中`0~1024`系统使用或保留端口       

#### UDP--面向无连接
•  将数据及源和目的封装成数据包中，不需要建立连接     
•  每个数据报的大小在限制在`64k`内     
•  因无连接，是不可靠协议     
•  不需要建立连接，速度快     
     
#### TCP--面向对象连接     
•  建立连接，形成传输数据的通道     
•  在连接中进行大数据量传输     
•  通过三次握手完成连接，是可靠协议     
•  必须建立连接，效率会稍低     

##### UDP发送方:  
```java
package my03;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;
import java.nio.channels.DatagramChannel;

public class StringDemo{
    public static void main(String[] args) throws Exception{
        DatagramSocket ds = new DatagramSocket();
        byte[] buf = "This is date".getBytes();
        DatagramPacket dp = 
            new DatagramPacket(buf, 
                         buf.length, 
                         InetAddress.getByName("192.168.0.1"), 8080);

        ds.send(dp);
        ds.close();
}}
```
##### UDP接收方:  
```python
package my03;

import java.net.InetAddress;
import java.net.DatagramSocket;
import java.net.DatagramPacket;

public class recv_socket {
    public static void main(String[] args) throws Exception{
        DatagramSocket ds = new DatagramSocket(8080);
        byte[] by = new byte[1024];
        DatagramPacket dp = new DatagramPacket(by, by.length);
        ds.receive(dp);
        String ip = dp.getAddress().getHostAddress();
        String data = new String(dp.getData(), 0, dp.getLength());
        int port = dp.getPort();
        System.out.println("Ip地址s :"+ip +" 数据接收的是 :"+ data + "--" +" 端口号是: "+port);
        ds.close();
}}
```
## 效果图:       
![ScreenShot-00465](https://github.com/KissMyLady/Java/blob/master/Img/ScreenShot-00465.jpg) 
