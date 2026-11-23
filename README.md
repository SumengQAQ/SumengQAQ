# SumengQAQ

大二在读，自学后端。关注领域驱动设计、分布式事务与形式化验证。

## 方向

| 方向           | 内容                                                               |
| -------------- | ------------------------------------------------------------------ |
| 形式化验证     | 动作的时序逻辑、TLA+、超组合、对称性约简、反例轨迹、分布式事务规约 |
| 领域驱动设计   | 事件风暴、聚合边界、限界上下文、工作单元、实体、值对象、聚合根     |
| 数据密集型应用 | 脏写、写偏斜、隔离级别、幂等、分布式共识                           |

## 消息组状态机

```mermaid
stateDiagram-v2
    direction LR
    [*] --> Pending: 写入
    Pending --> Processing: 收齐，分发
    Processing --> Success: 成功
    Processing --> Failed: 失败 / 超时
    Processing --> Dead: 重试超限
    Failed --> Processing: 重新分发
    Success --> [*]
    Dead --> [*]
```

## 分层

```mermaid
---
config:
  flowchart:
    curve: basis
---
flowchart TB
    subgraph iface["接口层"]
        R[Router]
    end

    subgraph application["应用层"]
        C[CommandService]
        Q[QueryService]
    end

    subgraph domain["领域层"]
        AR[AggregateRoot]
        DS[DomainService]
        EV[DomainEvent]
    end

    subgraph infrastructure["基础设施层"]
        REPO[Repository]
        UOW[UnitOfWork]
        MQ[MessageQueue]
        RM[("ReadModel")]
        OLAP[("OLAP")]
    end

    R --> C
    R --> Q
    C --> AR
    C --> DS
    C --> REPO
    C --> UOW
    AR --> EV
    EV --> MQ
    MQ -.->|异步投影| RM
    Q --> RM
    Q --> OLAP
```

## 技术栈

![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![TLA+](https://img.shields.io/badge/TLA%2B-2C3E50?style=flat)

## 项目

[![backend-architecture-notes](https://github-readme-stats.vercel.app/api/pin/?username=SumengQAQ&repo=backend-architecture-notes&theme=tokyonight)](https://github.com/SumengQAQ/backend-architecture-notes)
