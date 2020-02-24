## [Ubuntu安装Java](https://www.jianshu.com/p/75f0f34b599d)

#### 一. 手动下载压缩包安装Oracle Java JDK   
1. 前往oracle Java官网下载JDK`[http://www.oracle.com/technetwork/java/javase/downloads/index.html`   
2. 创建目录：`sudo mkdir /usr/lib/jvm`    
3. 上传jdk-8u191-linux-x64.tar.gz到/usr/lib/jvm       
    注意, 使用ssh中的rz需要加`sudo rz`   

#### 二.  解压JDK到该目录   
 `sudo tar -zxvf jdk-8u191-linux-x64.tar.gz -C /usr/lib/jvm`   
   
1. 修改环境变量：   
     `sudo vi ~/.bashrc`   

- 在文件末尾追加以下内容：   
> ```bash      
> #set oracle jdk environment   
> export JAVA_HOME=/usr/lib/jvm/jdk-11.0.6  ## 这里要注意目录要换成自己解压的jdk 目录   
> export JRE_HOME=${JAVA_HOME}/jre   
> export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib   
> export PATH=${JAVA_HOME}/bin:$PATH   
> ```   
立马生效:  `source ~/.bashrc`   


#### 三. 系统注册此jdk(安装未注册成功)   
 `sudo update-alternatives –install /usr/bin/java java /usr/lib/jvm/jdk1.8.0_191/bin/java 300`   


#### 四. 查看java版本，看看是否安装成功：   
 `java -version`   
