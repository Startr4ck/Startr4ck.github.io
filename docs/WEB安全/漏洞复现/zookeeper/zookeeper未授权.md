## zookeeper 

zookeeper是分布式应用程序协调服务，为分布式应用提供一致性服务的软件。提供的功能包括 配置维护 域名服务 分布式同步 组服务等。 

zookeeper是分布式协调服务，可以**自分布式系统当中共享配置，协调锁资源，提供命名服务**。

zookeeper的场景是 读多写少  ，其中存储的数据是 组件的配置文件，存储于Znode当中，每一个Znode当中存在  
 
data 数据  数据当中存储的是该组件的配置信息 
acl 访问表
stat 状态
child 子节点 



Zookeeper防止自己被挂所以自己使用了一主动从的结构。更新数据的时候首先更新主节点，然后同步从节点。读取数据的时候直接读取任意从节点。 



意思是能够通过zookeeper管理到其他的分布式组件 ？ 

一句话概括 

业务一般将组件的配置信息存储在zookeeper当中，各个组件通过访问zookeeper当中的节点获取配置从而被管理。 



### 造成危害

能够通过未授权获取到大量的系统的敏感信息，系统名称，java环境

配置信息等。一也可以对这些配置文件进行删除修改对组件的可用性造成影响。





### 如何寻找   

简单的测试步骤，寻找开启的2182端口。

往2182端口当中发送数据 ，看看回显 



![20211101001042](https://picsfor.oss-cn-shenzhen.aliyuncs.com/blogs/imgs/20211101001042.png)

### 如何修复

1、zookeeper服务器开启ACL进行访问 

2、设置防火墙限制IP访问 



### 总结 

zookeeper是管理大量组件的组件。服务器组件从zookeeper的节点当中获取配置数据

