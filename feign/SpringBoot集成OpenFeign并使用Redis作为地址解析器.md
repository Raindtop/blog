​	最开始项目是使用B/S模式进行开发的多模块项目，并且没有使用SpringCloud。所以使用MQ作为项目间的通信方式，后来由于客户注重数据安全，所以不太愿意使用B/S模式。他们更倾向于C/S模式，这就导致每次部署的工作量增加。为了解决这个问题，我决定使用OpenFeign+Redis的方式对MQ进行替换。

​	功能介绍：

​		openFeign：服务间互相调用组建

​		Redis：简易的服务注册与发现



1. 开发注解，实现FeignClient的注册与发现





> openFeign 执行流程解析 https://www.cnblogs.com/wuzhenzhao/p/13680807.html

