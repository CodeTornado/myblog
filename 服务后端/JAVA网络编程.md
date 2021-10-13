# 网络编程

##	网络协议

###	TCP(传输控制协议)方式 

#### 概念

是一种面向连接的保证可靠传输的协议。通过TCP协议传输,得到的是一个顺序的无差错的数据流。发送方和接收方的成对的两个socket之间必须建立连接,以便在TCP协议的基础上进行通信,当一个socket (通常都是server socket)等待建立连接时,另一个socket可以要求进行连接,一旦这两个socket雌接起来,它们就可以进行双向数据传输,双方都可以进行发送或接收操作

#### 三次握手

1. a你瞅啥
2. b瞅你咋地
3. a来干一架

#### 四次挥手

1. a我们分手吧
2. b你真的要离开我了吗
3. b你真的真的要离开我了吗
4. a是的



### 特点

1. 面向连接的协议,在socket之间进行数据传输之前必然要建立连接,所以在TCP中需要连接时间
2. TCP传输数据大小限制,一旦连接建立起来,双方的socket就可以按统一的格式传输大的数据。
3. TCP是一个可靠的协议,它确保接收方完全正确地获取发送方所发送的全部数据。

###		UDP(用户数据报协议)方式

#### 概念

是一种无连接的协议,每个数据报都是一个独立的信息,包括完整的源地址或目的地址,它在网络上以任何可能的路径传往目的地,因此能否到达目的地,到达目的地的时间以及内容的正确性都是不能被保证的。

#### 特点

1. 每个数据报中都给出了完整的地址信息,因此无需要建立发送方和接收方的连接。
2. UDP传输数据时是有大小限制的,每个被传输的数据报必须限定在64KB之内。
3. UDP是一个不可靠的协议,发送方所发送的数据报并不一定以相同的次序到达接收方

##	网络编程步骤

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210912121556.png" alt="image-20210912121556844" style="zoom:50%;" />

## 	java网络编程

###	InetAddress类

IP地址类，封装了对网络IP的操作

###	ServerSocket类

服务端监听socket类

```java
//服务端打开对用端口并获取监听对象
public ServerSocket(int port)；

//监听并获取连接对象
public Socket accept()
  
//关闭服务端监听
public void close()
```

### Socket类

网络连接套接字，实现数据传输的主要操作类

```java
//创建连接对象，连接服务器
public Socket(String host, int port)；//host为服务器地址，port为服务器监听端口
 
//获取输出流对象（输出信息）
public OutputStream getOutputStream()
 
//获取输入流对象（接收信息）
public InputStream getInputStream()
 
//关闭socket
public synchronized void close()
```



​	

### 示例

#### TCP

##### 服务端

```java
try {
       //服务端打开端口8888
       ServerSocket ss = new ServerSocket(8888);
 
      //在8888端口上监听，看是否有连接请求过来
      logger.info("监听在端口号:8888");
      Socket s = ss.accept();
 
      logger.info("有连接过来" + s);
 
      //打开输入流
      InputStream is = s.getInputStream();
 
      if (is != null) {
          logger.info("接收到信息：");
          //读取客户端发送的数据
          int msg = is.read();
          //打印出来
          logger.info(msg + "");
      }
      is.close();
 
      s.close();
      ss.close();
} catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
}
```



##### 客户端

```java
try {
        logger.info("发起连接。。。");
        //连接到本机的8888端口
        Socket s = new Socket("127.0.0.1", 8888);
        logger.info("连接成功");
 
        logger.info("发送细信息：110");
        // 打开输出流
        OutputStream os = s.getOutputStream();
 
        // 发送数字110到服务端
        os.write(110);
 
        logger.info("发送成功");
        os.close();
        s.close();
} catch (UnknownHostException e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
} catch (IOException e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
}
```



##### 运行结果

```java
----Server.java
 
[main] INFO SocketConnect.Server - 监听在端口号:8888
[main] INFO SocketConnect.Server - 有连接过来Socket[addr=/127.0.0.1,port=5454,localport=8888]
[main] INFO SocketConnect.Server - 接收到信息：
[main] INFO SocketConnect.Server - 110
 
 
----Client.java
 
[main] INFO SocketConnect.Client - 发起连接。。。
[main] INFO SocketConnect.Client - 连接成功
[main] INFO SocketConnect.Client - 发送细信息：110
[main] INFO SocketConnect.Client - 发送成功

```



#### UDP

##### 发送端

```java
try {
            ServerSocket ss = new ServerSocket(8888);
            logger.info("监听8888.。。。");
 
            Socket socket = ss.accept();
 
            logger.info("有连接过来" + socket);
 
            InputStream is = socket.getInputStream();
 
            OutputStream os = socket.getOutputStream();
 
            //把输入输出流封装在DataInputStream
            DataInputStream dis = new DataInputStream(is);
 
            DataOutputStream dos = new DataOutputStream(os);
 
            String message = "start";
 
            logger.info("交流开始。。。");
            while (!message.equals("end")) {
                System.out.print("接收到信息：");
 
                //使用readUTF读取字符串
                message = dis.readUTF();
 
                System.out.println(message);
 
                //使用Scanner读取控制台的输入，并发送到服务器
                System.out.print("发送信息：");
                Scanner sc = new Scanner(System.in);
 
                message = sc.next();
 
                dos.writeUTF(message);
            }
 
            logger.info("交流结束");
 
            dis.close();
            is.close();
            socket.close();
            ss.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
```



##### 接收端

```java
try {
     Socket s = new Socket("127.0.0.1", 8888);
 
     OutputStream os = s.getOutputStream();
 
     //获取输出流并封装到DataOutputStream中
     DataOutputStream dos = new DataOutputStream(os);
    
     //获取输入流并封装到DataInputStream中
     InputStream is = s.getInputStream();
     DataInputStream dis = new DataInputStream(is);
     
     String message = "";
 
     while(true){
        //使用Scanner读取控制台的输入，并发送到服务器
        System.out.print("发送信息：");
        Scanner sc = new Scanner(System.in);
        message= sc.next();
        dos.writeUTF(message);
           
        //输入的时“end”字符串时，结束交流
        if(NetWorkConst.END.equals(message)){
            logger.info("交流结束");
            break;
        }
 
        message = dis.readUTF();
        logger.info("收到服务端信息:"+message);
        if(NetWorkConst.END.equals(message)){
            break;
        }
     }
 
     dos.close();
     s.close();
} catch (UnknownHostException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
} catch (IOException e) {
     // TODO Auto-generated catch block
     e.printStackTrace();
}
```



##### 运行结果

```java
-----Server.java
 
[main] INFO SocketConnect.Server - 监听8888.。。。
[main] INFO SocketConnect.Server - 有连接过来Socket[addr=/127.0.0.1,port=7260,localport=8888]
[main] INFO SocketConnect.Server - 交流开始。。。
接收到信息：123
发送信息：我是服务器端
接收到信息：我是客户端
发送信息：end
[main] INFO SocketConnect.Server - 交流结束
 
 
-----Client.java
 
发送信息：123
[main] INFO SocketConnect.Client - 收到服务端信息:我是服务器端
发送信息：我是客户端
[main] INFO SocketConnect.Client - 收到服务端信息:end
```



##	总结

1. 网络传输方式主要有两种，TCP传输方式安全可靠，传输双方需要建立虚拟连接，存在连接时延。UDP方式通过各种渠道传输数据，是个不可靠传输协议，且无法判断数据到达的正确性和时间。所以一般使用TCP传输方式或者两者结合使用
2. java网络编程依赖于java.net包实现，其中的InetAddress封装了一些关于IP的操作方法
3. 网络编程离不开客户端和服务端，java的C/S模式网络编程开发，使用套接字对象socket作为设备间的逻辑连接端点，实行传输。服务器端主要有以下步骤：创建服务器端口监听socket-获取连接socket-交换信息-结束交换，关闭socket及相关资源；客户端主要有以下步骤：创建对应地址端口的socket对象，请求连接-交换信息-结束交换，关闭socket及相关资源