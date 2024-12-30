---
title: "golang"
date: 2024-12-29T10:08:22+08:00
draft: false
categories: ["Note","go"]
tags: ["Note","golang","go"]
summary: golang
---

# golang

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



### Install VS Code

1. Install the Go Extension in VS Code

   的

