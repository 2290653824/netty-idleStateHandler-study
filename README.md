## 为什么有这个仓库
1. 在学习项目的时候，用到netty中的心跳机制，有个很重要的组件叫做IdleStateHandler,想要进行学习，固有此仓库


## 项目结构

com.zj.netty.client下是客户端相关的类
com.zj.netty.server下是服务端相关的类

## 怎么使用
1. 先server服务端
2. 再启动client客户端
3. 之后会发现client因为IdleStateHandler的写事件会在一定周期内发送给server端心跳
4. server端因为定期收到了来自client的信息，有读事件，所以不会触发userEventTrigger

那么怎么样才会触发server的userEventTrigger呢？首先需要client停止向server发送信息即可。只需要我们以debug模式启动，然后在client端发送数据之前打上断点，server端收不到来自client的数据，自然会触发readIdle事件，然后进而触发userEventTrigger

## 参考
可以看我的博客[netty中的心跳处理]()

## 后续
- [ ] 一般项目中怎么使用这个心跳机制。