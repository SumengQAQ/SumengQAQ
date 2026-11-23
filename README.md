# SumengQAQ

大二在读，自学后端。关注领域驱动设计、分布式事务与形式化验证。

## 方向

| 方向                     | 内容                                                  |
| ------------------------ | ----------------------------------------------------- |
| 形式化验证               | TCC、Saga、Outbox、消息队列，四份 TLA+ 规约，TLC 跑通 |
| 领域驱动设计             | 聚合边界、限界上下文、UoW 与领域事件                  |
| 数据密集型应用中的一致性 | 隔离级别、MVCC、写偏斜、条件更新、重试与幂等          |

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
        AS[AppService]
        AQ[Query]
    end

    subgraph domain["领域层（不依赖框架）"]
        DS[DomainService]
        E[AggregateRoot]
        P[Protocol]
        RP[Repository ABC]
    end

    subgraph infrastructure["基础设施层"]
        SQL[SQL Repository]
        GW[网关：retry / timeout]
        UOW[UnitOfWork]
    end

    R --> AS
    R --> AQ
    AS --> DS
    AS --> RP
    AS --> UOW
    DS --> E
    E --> P
    SQL -.->|实现| RP
    GW -.->|注入| AS
```

箭头只有两个方向：上层指向下层，基础设施指向领域层定义的接口。

## 技术栈

![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![TLA+](https://img.shields.io/badge/TLA%2B-2C3E50?style=flat)

## 项目

[![backend-architecture-notes](https://github-readme-stats.vercel.app/api/pin/?username=SumengQAQ&repo=backend-architecture-notes&theme=tokyonight)](https://github.com/SumengQAQ/backend-architecture-notes)
