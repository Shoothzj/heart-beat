在现在,我们经常使用到的心跳例子就是k8s的liveness和readiness
常见的配置文件:



我们可以开发出一个通用的,能支持多种协议的远端服务器状态探测代码,常见的心跳探测有:
- ping命令检测
- COAP(S)请求探测
- HTTP(S)请求探测
- 基于HTTP协议实现的私有协议(如SOAP协议等)
- 基于TCP长链接的心跳探测(如SMPP, MQTT)

我们首先可以把心跳拆分为长链接和短连接

短连接一定要有超时时间,不然会耗尽系统的资源.
用线程池的方式控制系统的资源占用ScheduledExecutorService

短链接常见协议:
- ICMP的ping协议
