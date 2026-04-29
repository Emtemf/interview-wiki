# Wiki Schema

## Domain
后端工程师面试知识库 —— LeetCode算法、MySQL、Redis、消息队列、系统设计、项目经验

## Conventions
- 文件名：小写、连字符、无空格（如 `mysql-index-optimization.md`）
- 每个wiki页面以YAML frontmatter开头（见下方模板）
- 使用 `[[wikilinks]]` 链接页面（每页至少2个外链）
- 更新页面时，务必更新 `updated` 日期
- 新页面必须添加到 `index.md` 对应分区
- 每次操作都要追加到 `log.md`
- **来源标记**：综合3+来源的页面，在段落末尾标注来源 `^[raw/articles/source.md]`

## Frontmatter
```yaml
---
title: 页面标题
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | problem
tags: [从下方分类选取]
sources: [raw/articles/source-name.md]
# 可选质量标记：
confidence: high | medium | low    # 知识点掌握程度
frequency: high | medium | low     # 面试高频程度
---
```

## Tag Taxonomy

### 算法 (LeetCode)
- `two-pointers` - 双指针
- `sliding-window` - 滑动窗口
- `binary-search` - 二分查找
- `dfs` - 深度优先搜索
- `bfs` - 广度优先搜索
- `dp` - 动态规划
- `greedy` - 贪心算法
- `backtracking` - 回溯
- `tree` - 树
- `graph` - 图
- `heap` - 堆
- `hash` - 哈希表
- `linked-list` - 链表
- `array` - 数组
- `string` - 字符串

### 数据库 (MySQL)
- `mysql-index` - 索引
- `mysql-transaction` - 事务
- `mysql-lock` - 锁机制
- `mysql-replication` - 主从复制
- `mysql-cluster` - 集群
- `mysql-optimization` - 性能优化
- `sql-syntax` - SQL语法

### 缓存 (Redis)
- `redis-data-structure` - 数据结构
- `redis-persistence` - 持久化
- `redis-cluster` - 集群/哨兵
- `redis-cache` - 缓存策略
- `redis-lock` - 分布式锁

### 消息队列
- `mq-kafka` - Kafka
- `mq-rabbitmq` - RabbitMQ
- `mq-rocketmq` - RocketMQ
- `mq-pattern` - 消息模式（发布订阅、死信队列等）

### 系统设计
- `system-design` - 系统设计
- `distributed` - 分布式系统
- `microservice` - 微服务
- `high-concurrency` - 高并发
- `high-availability` - 高可用

### 项目经验
- `project` - 项目经验
- `architecture` - 架构设计
- `troubleshooting` - 问题排查
- `optimization` - 优化实践

### 元标签
- `comparison` - 对比分析
- `faq` - 常见问题
- `pitfall` - 易错点

## Page Thresholds
- **创建页面**：一个知识点在2+来源中出现，或是一个来源的核心内容
- **不创建页面**：偶然提及、与后端无关的内容
- **拆分页面**：超过200行时拆分为子主题

## Entity Pages
一个实体一个页面：
- 是什么 / 核心概念
- 关键知识点
- 相关实体链接
- 来源引用

## Concept Pages
一个知识点一个页面：
- 定义 / 解释
- 当前理解程度
- 常见面试问题
- 相关概念链接

## Comparison Pages
对比分析：
- 对比什么、为什么对比
- 对比维度（表格形式）
- 结论 / 选择建议
- 来源

## Problem Pages (LeetCode)
算法题目页面：
- 题目描述 / 链接
- 解题思路
- 代码模板
- 相关题目 [[wikilinks]]
- 变体 / 易错点

## Update Policy
当新信息与现有内容冲突时：
1. 查看日期 —— 新来源一般覆盖旧来源
2. 如果确实矛盾，标注两个观点及日期和来源
3. 在frontmatter标记：`contradictions: [page-name]`
4. 标记为待复习