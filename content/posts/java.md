---
title: "java"
date: 2025-01-24T11:00:00+08:00
draft: false
categories: ["Note","java"]
tags: ["Note","java","java"]
summary: java教程
---

# 简介

> 把大象装进冰箱需要几步？答：三步，把冰箱门打开，大象塞进去，关上冰箱门。
>
> 声明/实例化->配置->使用

spring,spring boot,spring cloud 这三个框架一起提供了一个强大的生态系统，适用于构建现代的 Java 应用，特别是以可扩展性、云原生特性和开发简便性为重点。

**Spring** 是基础，它提供了核心框架。

- 核心特性：依赖注入（DI）、面向切面编程（AOP）、事务管理等，帮助开发者构建各种 Java 应用。
- 用于构建任何规模的应用，重点是灵活性和模块化。

**Spring Boot** 基于 Spring 框架，提供了一种快速开发的方式。

- 它**简化了 Spring 的配置**，提供了开箱即用的功能和约定优于配置（Convention over Configuration）的理念。
- 重点是快速搭建、减少样板代码、内嵌服务器（如 Tomcat）以及易于测试和部署。
- 本质上，Spring Boot 是对 Spring 的增强，**使开发微服务变得简单。**

**Spring Cloud** 构建在 Spring Boot 和 Spring 之上，专注于微服务架构。

- 提供工具和库，用于解决微服务系统的常见问题，如服务注册与发现、分布式配置、负载均衡、断路器、分布式消息等。
- Spring Cloud 的模块需要依赖 Spring Boot 来运行，并继承 Spring 的核心特性。

# Getting started

## Install eclipse

https://www.eclipse.org/downloads/packages/

https://www.eclipse.org/downloads/

## Install IntelliJ IDEA

> IDEA IntelliJ IDEA Ultimate  2024 1.x 版本  ideaIU-2024.1.7
> https://www.jetbrains.com/idea/download/other.html
>
> 失效就卸载重装下

注册码激活(推荐): https://ipfs.io/ipfs/bafybeih65no5dklpqfe346wyeiak6wzemv5d7z2ya7nssdgwdz4xrmdu6i/

下载 [jetbra.zip](https://ipfs.io/ipfs/bafybeih65no5dklpqfe346wyeiak6wzemv5d7z2ya7nssdgwdz4xrmdu6i/files/jetbra-8f6785eac5e6e7e8b20e6174dd28bb19d8da7550.zip)文件,放好位置,点击`scripts`脚本,自动配置 vmoptions

使用页面 https://jetbra.in/5d84466e31722979266057664941a71893322460 上的密钥

```bash
操作指南：
1. 将 -javaagent:/path/to/ja-netfilter.jar=jetbrains 添加到您的 vmoptions（手动或自动）
2. 在“许可证”窗口中注销 jb 帐户
3. 使用页面 https://jetbra.in/5d84466e31722979266057664941a71893322460 上的密钥
4. 插件“mymap”自 2022.1 版起已弃用
5. 不必在意激活时间，它是一个后备许可证，不会过期

享受它~

JBR17：
将这 2 行添加到您的 vmoptions 文件：（手动，没有任何空格字符）
--add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
--add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED

新功能：
自动配置 vmoptions：
macOS 或 Linux：执行“scripts/install.sh”
Windows：双击执行“scripts\install-current-user.vbs”（针对当前用户）
“scripts\install-all-users.vbs”（针对所有用户）
```

## Java主流版本

> 在国内，互联网公司的 Java 开发大多结合 Spring 系列框架（如 Spring Boot），而框架的兼容性也会影响 Java 版本的选择。
>
> Docker 和 Kubernetes 等容器化技术的发展，也推动了对性能优化和运行时稳定性的更高要求，新版本逐渐受到欢迎。
>
> 中大型企业更倾向于使用长期支持（LTS）版本，以减少频繁升级的成本和风险。

| **Java 版本** | **适用场景**                                   | **状态**           |
| ------------- | ---------------------------------------------- | ------------------ |
| **Java 8**    | 老旧系统，基于早期版本的 Spring 工具链         | 不建议新项目使用   |
| **Java 11**   | 主流项目，稳定支持 LTS 和 Spring Boot 2.x 系列 | 推荐大部分项目使用 |
| **Java 17**   | 新项目，未来长期支持，与最新框架完全兼容       | 强烈推荐使用       |

如果是 Spring Boot 3.x 或 Spring Cloud 2022.x 开始的新项目，**Java 17 是最佳选择**。

- Java 8 (LTS)
  - 最为广泛使用，尤其是在成熟项目和传统业务系统中。
  - 稳定性高，许多企业选择 Java 8 作为生产环境的默认版本。
  - 丰富的工具和第三方库生态支持。
- Java 11 (LTS)
  - 在 Java 8 之后，许多新项目或需要升级的项目会选择 Java 11。
  - 提供了更好的性能优化，同时是一个长期支持版本（LTS）。
- Java 17 (LTS)
  - 越来越多的新项目开始采纳，特别是对新功能有需求、追求更高安全性和性能的团队。
  - Java 17 的功能较为现代，但使用普及程度仍稍逊于 Java 8 和 11。



Java 11 对比 Java 8 的优点在于：

1. **开发更简洁**：新字符串操作、`var`、集合工厂方法等。
2. **性能提升**：改进的垃圾收集器、TLS 1.3、Docker 感知。
3. **现代化功能**：HTTP/2 客户端、模块化系统、运行时优化。

如果是正在维护的老项目，可以继续使用 Java 8；而对于新项目，Java 11 的特性明显能提高开发效率和性能。

## JDK (Java Development Kit) 17

> https://www.oracle.com/java/technologies/downloads/#java17?er=221886

**新增系统变量：**

- 在 "系统变量" 区域点击 "新建"。
- **变量名**：`JAVA_HOME`
  **变量值**：JDK 的解压路径，例如 `C:\Java\jdk-17`

**编辑 Path 环境变量：**

- 在 "系统变量" 区域，找到 `Path` 变量并点击 "编辑"。

- 点击 "新建"，添加以下路径：

  ```bash
  %JAVA_HOME%\bin
  ```

# 快速入门

重点语法,通用方法

git工具

idea工具

mysql语法
