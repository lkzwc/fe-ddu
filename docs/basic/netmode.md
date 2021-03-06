---
title: 网络模型
slug: /netmode
---

网络实际模型：物理层、数据链路层、网络层、传输层、应用层！
![image](https://user-images.githubusercontent.com/84896877/168201127-efe68fbb-de43-453e-8f8c-d9de8e965873.png)

| 数据层     | 协议                      | 功能                                         |
| ---------- | ------------------------- | -------------------------------------------- |
| 物理层     | --                        | 抹平上层的差异性，将数据处理为比特流透明传输 |
| 数据链路层 | --                        | 校验提供可靠的物理传输介质                   |
| 网络层     | tcp 、udp quic            | 寻址、组包                                   |
| 传输层     | ip \icmp\arp              | 定义传输的协议端口                           |
| 应用层     | http \talnet\ftp\stp\smtp | 建立会话                                     |

> QUIC

- 基于 UDP 的多路传输（单连接下）；
- 极低的等待时延（相比于 TCP 的三次握手）
- 快速迭代更新；
- 开源于 Chromium 项目中。

TCP 由于基于操作系统内核实现，发展速度极慢，现有的 TCP Fast Open 实现等等虽然早已存在于标准中但是实际应用情况及其落后，即便除非所有机器的操作系统都更新到最新，否则考虑到兼容性不太可能大范围采用新技术。QUIC 直接基于[客户端]实现，而非基于系统内核（这点有点像最新的.Net Core），可以进行快速迭代更新，不需要操作系统内核层面的更改。

> 数据流转：

- 应用层产生数据->发送到传输层
- 加入 TCP 头部信息->形成数据段
- 传输到网络层
- 加入 IP 信息 形成数据包
- 加入 mac 地址信息(arp)，形成数据帧
- 传输到物理层
- 转化为电信号->通过网卡、网线发送到交换机->网络传输
