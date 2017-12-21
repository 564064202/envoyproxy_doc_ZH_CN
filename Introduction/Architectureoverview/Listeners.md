### 监听器

Envoy配置支持单个进程中的任意数量的监听器。通常我们建议每台机器运行一个Envoy，而不关心监听器数量。这样可以使操作更简单，统计也更简单。目前Envoy只支持监听TCP。

每个监听器都独立配置一定数量的（L3 / L4）网络过滤器。当监听器接收到新连接时，实例化相应过滤器，并开始处理后续事务。通用监听器用于执行不同代理任务（例如，速率限制，TLS客户机认证，HTTP连接管理，MongoDB嗅探，原始TCP代理等）。

监听器也可以通过监听器发现服务（LDS）动态获取。

[相关配置](../../Configurationreference/Listeners.md)

### 返回
- [架构介绍](../Architectureoverview.md)
- [简介](../../Introduction.md)
- [首页目录](../../README.md)
