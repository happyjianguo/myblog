---
title: "2 软件过程"
authors: [kiki]
tags: [sa, engineer]
categories: [blog]
draft: false
---

- [2.1 软件过程模型](#21-%e8%bd%af%e4%bb%b6%e8%bf%87%e7%a8%8b%e6%a8%a1%e5%9e%8b)
- [2.2 过程活动](#22-%e8%bf%87%e7%a8%8b%e6%b4%bb%e5%8a%a8)
- [2.3 应对变更](#23-%e5%ba%94%e5%af%b9%e5%8f%98%e6%9b%b4)
- [2.4 Rational 统一过程](#24-rational-%e7%bb%9f%e4%b8%80%e8%bf%87%e7%a8%8b)

- 软件过程分类
  - 计划驱动：提前计划好所有的过程活动，庵后按计划去考核过程的执行
  - 敏捷过程：计划是增量式的，而且很容易根据不断变化的客户需求变更过程
- 过程标准化的重要性：减少在一个机构中多样的软件过程的出现，可以改善沟通、缩短培训时间、使自动化的过程支持更经济

## 2.1 软件过程模型

- 常用的过程模型(也叫过程泛型)

名称 | 描述 | 适用场景 | 优点 | 不足
--- | --- | --- | --- | ---
瀑布模型 | 计划驱动，开始工作之前，必须对所有过程活动制定计划并给出进度安排 | 完全了解需求，且系统开发过程中不太可能发生重大改变 | 每个阶段生成文档，过程可见，易于根据项目计划监控项目进度 | 不易响应用户的需求变更
增量式开发| 敏捷方法，系统每个增量或版本包括用户需要的一部分功能 | 商务、电子商务和个人系统 | 降低了适应用户需求变更的成本，易得到用户反馈，更快地交付和部署 | 过程不可见，新的增量导致系统结构被破坏
面向复用的软件过程 | 根据需求复用现存软件进行开发 | 已存在大量可复用的软件组件，以及组合组件的集成框架 | 减少需要开发的软件数量，降低开发成本和风险，可快速交付 | 需求妥协，可能不符合用户真正的需求，且组件新版本不受机构控制

## 2.2 过程活动

- 包括 4 个基本活动
  - 软件描述：必须定义软件的功能以及软件操作上的约束。其中的关键阶段是[需求工程](./4-requirement-engineering.md)
  - 软件设计和实现：对实现软件的结构、系统的数据、系统组件间的接口以及所用算法的描述
  - 软件有效性验证：软件必须得到有效性验证，即确保软件是客户所想要的
  - 软件进化：软件必须进化以满足不断变化的客户需要

## 2.3 应对变更

- 返工：变更增加了软件开发的成本，通常意味着已完成的工作要重做
- 降低返工成本的方法
  - 变更避免：在重大返工发生之前预测变更。比如开发原型，客户试用原型，重新定义需求
  - 变更容忍：通常需要增量开发，提出的变更可能是在还没有开发的增量上实现，或者修改单个增量来适应变更
- 应对变更系统需求的方法：
  - 系统原型：快速开发一个系统版本或系统的一部分，以检验客户需求和某些设计决定的可行性。支持变更避免
    - 原型：一个软件系统的最初版本，用于验证概念、试用设计选型、发现更多的问题和可能的解决方案
  - 增量交付：系统增量地交付给客户，给用户评审和试用。支持变更避免和变更容忍

## 2.4 Rational 统一过程

- 6 个基本且最好的实践
  - 1 迭代地开发软件：根据客户的轻重缓急来规划系统的增量，在开发过程中先开发和交付最高优先权的系统特性
  - 2 对需求的管理：明确地记录客户的需求并跟踪这些需求的变更。在接受之前分析系统变更带来的影响
  - 3 使用基于组件的体系结构：将系统体系结构组织成组件的形态
  - 4 可视化地建模软件：使用图形 UML 模型表现软件的静态和动态视图
  - 5 检验软件质量：保证软件满足了机构质量标准
  - 6 控制对软件的变更：使用变更管理系统、配置管理程序和工具来管理软件的变更