# Supported tags and respective `Dockerfile` links



- [`latest`](https://github.com/seltonGitHub/psqueue/blob/master/1.0/Dockerfile)

# Quick reference



- **Where to file issues**:

  https://github.com/seltonGitHub/psqueue/issues

- **Supported OS**:

  centos

# What is Psqueue?

支持任意个队列,每个队列任意多个消费者的基于 HTTP GET/POST 协议的轻量级开源简单消息队列服务!协议用纯java实现.可以达到每秒并发40000-50000个请求.

队列（Queue）又称先进先出表（First In First Out），即先进入队列的元素，先从队列中取出。加入元素的一头叫“队头”，取出元素的一头叫“队尾”。利用消息队列可以很好地异步处理数据传送和存储，当你频繁地向数据库中插入数据、频繁地向搜索引擎提交数据，就可采取消息队列来异步插入。另外，还可以将较慢的处理逻辑、有并发数量限制的处理逻辑，通过消息队列放在后台处理，例如FLV视频转换、发送手机短信、发送电子邮件等。

#### PSQueueServer 具有以下特征：

+ [x] 非常简单，基于 HTTP GET/POST 协议。PHP、Java、Perl、Shell、Python、Ruby等支持HTTP协议的编程语言均可调用。
+ [x] 完善的JMX管理接口,所有方法全部可以由JMX来管理.为了安全管理方法需要口令!
+ [x] 每个队列支持任意多消费者。
+ [x] 非常快速，入队列、出队列速度超过40000次/秒。
+ [x] 高并发，支持5K以上的并发连接。
+ [x] 支持多队列。
+ [x] 队列个数无限制,只要系统的磁盘空间够用(缺省单个队列占用磁盘空间是2G)。
+ [x] 低内存消耗，海量数据存储，存储几十GB的数据只需不到200MB的物理内存缓冲区。
+ [x] 可以实时查看指定队列状态（未读队列数量）。
+ [x] 可以查看指定队列,指定消费者的内容，包括未出、已出的队列内容。
+ [x] 查看队列内容时，支持多字符集编码。
+ [x] 创新设计:消费者可以故意倒回到老的偏移量再次消费数据。这违反了队列的常见约定，但被证明是许多消费者的基本特征。
  
### 注意:
>  当向队列`add`添加数据而且当队列的`size`超出队列的`capacity`时,是不会报队列满的错误的!  
>  系统会定时清理(缺省30分钟),把队列的size调整到跟`capacity`一致,这时超出`capacity`的队列尾部的数据会被清理掉!!!  



# How to use this image



## start a redis instance



```shell
$ docker run --name some-psqueue -dt -p  selton/psqueue
$ docker exec -it some-psqueue bash
$ ./opt/psqueue/bin/psqueue.sh start
```

> 由于没有加入启动脚本,所以还需要创建好容器之后,进入容器内部启动psqueue服务