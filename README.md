# 你好，我是 SumengQAQ

大二在读，非科班自学后端。方向是 Go / Python 服务端，最近在啃领域驱动设计、分布式事务和 TLA+。

## 在做什么

| 方向         | 内容                                                     |
| ------------ | -------------------------------------------------------- |
| 领域驱动设计 | 聚合边界怎么切、限界上下文怎么分、防腐层什么时候真的需要 |
| 分布式事务   | TCC、Saga、Outbox，三个模式各写了一份 TLA+ 规约          |
| 形式化验证   | 用 TLC 跑模型检查，找并发下的空回滚、悬挂、写偏斜        |

## 一个自己设计的状态机

消息组在中间件里的生命周期，用 TLA+ 验证过：

```mermaid
stateDiagram-v2
    [*] --> 待收集
    待收集 --> 处理中: 收集完毕，分发
    处理中 --> 成功: 消费成功
    处理中 --> 失败: 失败 / 超时
    处理中 --> 死信: 重试超限
    失败 --> 处理中: 重新调度
    成功 --> [*]
    死信 --> [*]
```

## 技术栈

![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![TLA+](https://img.shields.io/badge/TLA%2B-2C3E50?style=flat)

## 项目

[![backend-architecture-notes](https://github-readme-stats.vercel.app/api/pin/?username=SumengQAQ&repo=backend-architecture-notes&theme=tokyonight)](https://github.com/SumengQAQ/backend-architecture-notes)

## 统计

![stats](https://github-readme-stats.vercel.app/api?username=SumengQAQ&show_icons=true&theme=tokyonight&hide_title=true)
