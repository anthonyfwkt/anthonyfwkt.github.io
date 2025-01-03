---
title: "golang"
date: 2024-12-29T10:08:22+08:00
draft: false
categories: ["Note","go"]
tags: ["Note","golang","go"]
summary: golang
---

# golang

> 一般用于服务器端 server side programming

## setting up vscode for golang on windows

### Install Go (Golang)

https://go.dev/dl/

**.msi* *

1. 直接安装到目录: `C:\DevOps\Go\go版本号`

2. 配置代理(七牛云): 

   ```bash
   # 启用 Go Modules 功能,到v1.16版本开始Go Module默认开启
   go env -w GO111MODULE=on
   
   # 配置 GOPROXY 环境变量，以下三选一
   
   # 1. 七牛 CDN
   go env -w  GOPROXY=https://goproxy.cn,direct
   
   # 2. 阿里云
   go env -w GOPROXY=https://mirrors.aliyun.com/goproxy/,direct
   
   # 3. 官方
   go env -w  GOPROXY=https://goproxy.io,direct
   ```

   

**.zip**

1. 下载解压到目录: `C:\DevOps\Go\go版本号`

2. 配置系统环境变量: 

   1. 新建`GROOT`变量,指定更目录`C:\DevOps\Go\go版本号`
   2. 系统变量path中,添加值: `%GROOT%\bin`

3. 配置用户环境变量: 

   1. 新建`GOPATH`变量,值为: `%USERPROFILE%\go`

4. 配置代理(七牛云): 

   ```bash
   go env -w GOPROXY=https://goproxy.cn,direct
   ```

   

**配置完成测试**

1. 查看版本: go version
2. 查看配置文件: go env
3. `goland` 配置`GROOT`,开启`Go模块集成`



**目录说明**

GROOT:  为了方便计算,找到我们所安装的SDK,路径一般写到bin目录的上一级,就是go的安装路径，也是为了方便配合PATH使用

​		假如SDK的存放路径修改了只需要修改GOROOT,而不用修改GOPATH

**GOPATH: 工作目录,创建项目时指定的存放目录，go install/go get和 go的工具等会也用到GOPATH环境变量,默认在`%USERPROFILE%\go`下**

GOBIN: go语言生成可执行程序的路径,可以自己指定

```bash
一般约定的三个目录：
        bin(存放编译后的二进制文件)
        pkg(存放编译后的库文件)
        src(存放源代码文件,该目录下可以包含很多包)
其他目录：
        api(内部包含各种api，方便IDE内部的工作)
        doc:Go语言的各种文档，官网上有的，这里基本会有。
        lib：目录内包含文档模板
        misc：其他的一些工具，例如cgo等
        test：包含很多测试程序
        AUTHORS：官方 Go语言作者列表
        CONTRIBUTORS：第三方贡献者列表
        LICENSE：Go语言发布授权协议
        PATENTS：专利
        README：文件提示用户怎么操作
        VERSION：顾名思义安装的Go语言版本
```



### Install Goland

> https://jcshan709.github.io/jetbrains-activating-tutorial/

**第 1 步 - 查找 JetBrains 许可证服务器**

1. 访问[Censys 搜索](https://search.censys.io/)

2. 输入以下文本并搜索：

   ```bash
   services.http.response.headers.location: account.jetbrains.com/fls-auth
   ```

3. 找到一个开放了 80 端口的站点，点击查看状态码是否为**302**，如果不是，再找一个。



**第 2 步 - 激活你的 IDE**

1. 启动您的 IDE 并`License Server`在激活页面上进行选择。
2. 复制地址，包括协议（`http://`）（不包括端口），然后单击`Activate`
3. 与 JetBrains 插件的方法相同`Code With Me`
4. 若激活失败，请寻找其他服务器尝试。

## Tutorial

> https://golang.halfiisland.com/

下面对本站的内容进行一个简单的介绍，以便各位可以按需阅读，部分页面是空白的代表着还未更新。

- 语言入门：主要讲解关于 Go 语言本身的内容，偏理论。
  - [语法基础](https://golang.halfiisland.com/essential/base/)：主要讲一些十分基础的语法，像是`if`，`for`之类的语法规则。
  - [语法进阶](https://golang.halfiisland.com/essential/senior/)：讲一些 Go 独有的东西，关于模块，测试，协程等相关内容。
  - [标准库](https://golang.halfiisland.com/essential/std/)：对 Go 自带的标准库的一个简单介绍，因为标准库的内容实在太过庞大所以随缘更新。
  - [实现原理](https://golang.halfiisland.com/essential/impl/)：主要讲 Go 语言的一些内部设计原理，比如协程调度，内存管理，垃圾回收等。
- 社区生态：主要讲解 Go 周边的生态，偏应用。
  - [数据库](https://golang.halfiisland.com/community/database/)：通过 Go 操作主流的数据库。
  - [微服务](https://golang.halfiisland.com/community/micro/)：介绍一些与 Go 有关的微服务工具。
  - [第三方库](https://golang.halfiisland.com/community/pkgs/)：介绍一些由 Go 编写的第三方库，随缘更新，也可以直接在[依赖导航](https://golang.halfiisland.com/deb.html)里面查看。

### 字符串拼接

```go
func main() {
   builder := strings.Builder{}
   builder.WriteString("this is a string ")
   builder.WriteString("that is a int")
   fmt.Println(builder.String())
}
```

### Golang泛型

> 如果你经常要分别为不同的类型写完全相同逻辑的代码，那么使用泛型将是最合适的选择
> 参考: https://www.cnblogs.com/insipid/p/17772581.html



## Golang for Embedded Systems



## Server side programming

### Website

