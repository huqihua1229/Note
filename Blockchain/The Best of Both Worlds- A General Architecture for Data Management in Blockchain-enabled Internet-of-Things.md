# The Best of Both Worlds: A General Architecture for Data Management in Blockchain-enabled Internet-of-Things

****

传统中心话管理的缺点

* IoT 设备众多的情况下存储压力、可扩展性差

* 敏感数据易被泄露、篡改

* 存在单点故障问题，可靠性难以保障

* 权力集中，供应商与用户之间不平衡

****

具有区块链功能的物联网设备作为连接区块链网络的传统物联网设备的联合代理执行

当执行数据访问操作的时候，物联网设备之间可能存在资源限制和竞争，直观导致了瓶颈问题

物联网的动态性（高移动性）、区块链的不确定性（区块链攻击）导致不可预测的网络环境

> a case study of a learning-assisted data transmission method for intelligent data  management

****

该文提出的方法在**资源受限**的情况下实现了**低成本**、**高效率**的数据传输，不需要系统的完整信息。

****

随着当今物联网系统的大规模部署，大量数据感知和交换记录将以分布式模式连续产生

物联网系统可以利用区块链技术来存储、访问和保护历史交易数据，以便进一步利用数据

区块链在作为通用分布式账本集成到物联网系统中时，仍存在部署问题：

* 区块链需要为各类物联网设备提供差异化的数据管理服务
  
  典型的物联网设备的计算资源受限、无线传感器的内存和电池电量受限
  
  在物联网系统的每个设备中简单地部署区块链功能是不切实际地
  
  > 作为一个简单地解决方案，只有一部分地物联网设备可以选择部署区块链，此时物联网系统地架构设计应战略性地组织区块链和非区块链子网络

* 现代物联网系统不仅由传感器、网关和路由器等传统物联网设备组成，而且还与边缘计算和云计算等其他网络技术集成，这可能会增加物联网系统的能力
  
  区块链作为账本的架构和部署需要考虑这些新兴的物联网技术
  
  > 例如，资源有限的物联网设备可以将区块链共识任务卸载到可用的边缘/云服务器上进行计算。
  > 
  > 在这种情况下，需要考虑边缘/云服务的可用性、边缘/云环境的随机性以及区块链安全的影响等方面的一些问题。

## 通用框架介绍

> 没看懂这段话啥意思
> 
> As different device owners can contribute to the  IoT system in practical scenarios, both private and  public blockchain networks can co-exist for internal (within the devices by the same owner) and  global data management, respectively

两种集成方式

* 紧密集成
  
  每个 IoT 设备都是区块链节点

* 松散集成
  
  底层资源受限的物联网设备只产生和交付交易数据到区块链网络，以便通过区块链网络的物联网边缘设备进一步处理
  
  松散集成的主要缺点是系统中的物联网设备只能通过边缘设备访问和使用区块链账本，这会导致潜在的单节点故障或边缘设备的资源瓶颈

> 松散集成的方式在当前情况下更有前景，因为对现有物联网结构的修改较小

> ?  public and  private blockchains co-exist
> 
> 还有公有和私有区块链同时存在的区块链

****

基于区块链的物联网方案应用场景

* 数据分享和数据访问控制

* 数据审计

* 智能合约

****

区块链应用于物联网的挑战

* 物联网基础设施具有动态性
  
  系统性能受到物联网设备移动性引起的动态和随机性的不利影响

* 系统信息不完整
  
  区块链网络监管者在决策时无法获得整个系统的完整信息

* 支持区块链的物联网架构的瓶颈
  
  物联网边缘设备的计算和通信资源（例如内存、存储和带宽）很容易耗尽

因此，考虑**系统动态**、**不完整信息**以及**物联网设备和区块链网络之间的控制和传输的数据管理**是开发支持区块链的物联网系统的关键未来方向

****

使用了深度强化学习来辅助决策进行频段选择
