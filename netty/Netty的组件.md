


## **Netty的组件和设计**

**Channel 接口**

在基于Java的网络编程中，其基本的构造是class socket。Netty的Channel接口所提供的api，大大的降低了直接使用Socket类的复杂性。


----------


 **EventLoop 接口** 

EventLoop 定义了 Netty 的核心抽象，用于处理连接的生命周期中所发生的事件。
+ 一个EventLoopGroup包含一个或者多个EventLoop；
+ 一个EventLoop在它的生命周期内只和一个Thread绑定； 
- 所有由EventLoop处理的 I/O 事件都将在它专有的Thread上被处理； 
- 一个Channel在它的生命周期内只注册于一个EventLoop； 
- 一个EventLoop可能会被分配给一个或多个Channel。

----------

**ChannelFuture 接口**

Netty 中所有的 I/O 操作都是异步的。因为一个操作可能不会 立即返回，所以我们需要一种用于在之后的某个时间点确定其结果的方法。
为此，Netty 提供了 ChannelFuture接口，其addListener()方法注册了一个ChannelFutureListener，
以 便在某个操作完成时（无论是否成功）得到通知。  

---------

**ChannelHandler 接口**

充当了所有 处理入站和出站数据的应用程序逻辑的容器。

---

**ChannelPipeline 接口**

ChannelPipeline 提供了 ChannelHandler 链的容器，并定义了用于在该链上传播入站 和出站事件流的 API。
当 Channel被创建时，它会被自动地分配到它专属的ChannelPipeline。 

ChannelPipeline中存放的是ChannelHandler链，一条数据可以经过多个ChannelHandler进行处理，类似拦截器。

---

**引导**

- Bootstrap

	客户端配置

- ServerBootstrap

	服务端配置

引导一个客户端只需要一个 EventLoopGroup，但是一个 ServerBootstrap则需要两个（也可以是同一个实例）。

因为服务器需要两组不同的 Channel。第一组将只包含一个 ServerChannel，代表服务 器自身的已绑定到某个本地端口的正在监听的套接字。
而第二组将包含所有已创建的用来处理传 入客户端连接（对于每个服务器已经接受的连接都有一个）的 Channel。



