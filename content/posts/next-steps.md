---
title: "博客后续操作"
date: 2024-09-04T10:08:22+08:00
draft: false
categories: ["Blog"]
tags: ["Blog", "Hugo"]
summary: "个人博客简易教程"
---

## 下载hugo,配置环境变量

1. 下载源码或者编译好的exe文件(windows-amd64.zip): https://github.com/gohugoio/hugo  
2. 配置环境变量,`hugo version`查看版本

## 安装git,设置github账户凭据

> 要更改你的 Git 账户并连接到 GitHub，你需要按照以下步骤进行操作：
>
> 如果 Git 在尝试推送代码时仍然使用旧的凭据，你可能需要清除已保存的凭据。根据你使用的操作系统，步骤会有所不同：
>
> - **Windows:**
>   1. 打开“控制面板”。
>   2. 转到“用户账户” > “凭据管理器”。
>   3. 在“Windows 凭据”或“普通凭据”下找到与 GitHub 相关的条目，并删除它们。
>
> 然后重新认证绑定设备: git - github账户凭据 - github

1. 下载安装: https://git-scm.com/ 下载安装无脑直接下一步(选择下默认的文本编辑器为notepad++即可)

2. 设置用户名与邮箱（用户标识，必要）

   ```bash
   git config --global user.name "xxx"  #名称
   git config --global user.email xxx@qq.com   #邮箱
   ```

3. 配置代理: vpn工具->设置->参数设置->查看vpn的http监听端口

   ```bash
   git config --global http.proxy "127.0.0.1:vpn的http监听端口"  # 10808
   git config --global https.proxy "127.0.0.1:vpn的https监听端口" #10808
   ```


## 克隆仓库到本地

```bash
git clone https://github.com/anthonyfwkt/anthonyfwkt.github.io.git
```

## 发布blog

1. 新建blog,或者在 `posts`目录下新建`md`文件,编辑md文件完成后,将`draft`更新为`false`

   > 注意,hugo命令生成的`md`文件 `front matter`不是 `Yaml`格式的,删掉,然后在第一行`---`,然后使用`Yaml`格式输入

   ```bash
   hugo new posts/my-first-post.md
   ```

2. hugo发布

   ```bash
   hugo
   ```

3. 更新仓库

   ```bash
   git add .
   git commit -m "update posts"
   git push
   ```

4. 等待`github`仓库`Actions`自动部署网站,`Actions`查看部署网站

   部署会有延迟,过段时间查看就行

## 博客主题设置

参考文档: https://github.com/adityatelange/hugo-PaperMod/wiki/Features

## 添加 Giscus 评论功能

1. 添加giscus参照 1-3 步: https://www.haoyep.com/posts/hugo-add-component/

2. 配置参照官方文档

   创建一个 html 文件

   ```bash
   layouts/partials/comments.html
   ```

3. 并粘贴评论提供商(giscus)提供的代码

4. 在配置中开启此项

   ```yaml
   params:
     comments: true
   ```

