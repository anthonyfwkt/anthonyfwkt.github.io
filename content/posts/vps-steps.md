---
title: "vps配置教程"
date: 2024-09-04T11:08:22+08:00
draft: false
categories: ["VPS"]
tags: ["VPS"]
summary: "VPS教程"
---

> 最新VPS促销优惠活动: https://p3terx.com/archives/cheap-vps-racknerd.html
>
> - [ ] 更换vps邮箱账户
> - [ ] 更换vps

1. 购买域名,绑定域名和`VPS IP`[`ping`通域名,确认ip关联成功]

2. VPS系统选择

   建议首选 Debian ，稳！

3. **安装常用软件**

   ```bash
   apt update
   
   apt install mc vim sudo aptitude ufw curl
   ```

   

4. x-ui脚本

   ```bash
   bash <(curl -Ls https://raw.githubusercontent.com/FranzKafkaYu/x-ui/master/install.sh) 0.3.4.4
   ```

   X-UI是一个基于xray-core为核心的简易代理搭建工具，前端使用Vue框架，后端使用Golang编写。 它的目的是为了帮助各位更好地去搭建属于自己的代理服务，并且能够通过Telegram bot进行便捷地监控与管理。

   https://github.com/vaxilu/x-ui

   

:flushed: steps:

- 输入x-ui

- 输入15 -> 安装bbr

- 输入16> 为域名申请SSL证书  ->  SSL证书安装目录为/root/cert目录

  参照:  https://github.com/chika0801/Xray-install/blob/main/acme.md

- 输入7 -> 根据面板信息,ip+端口 登录

- 配置面板域名证书(`先配置面板的证书,然后使用https访问,后续节点会自动填入`):

  /root/cert/fullchain.cer

  /root/cert/域名.key

- [`ping`通域名,确认ip关联成功]

- **VPS更改x-ui重置登录密码为admin,使用https域名访问x-ui面板,修改登录密码**

4. 配置warp

   https://github.com/P3TERX/warp.sh

   https://p3terx.com/archives/cloudflare-warp-configuration-script.html

   添加 WARP Wire­Guard 双栈全局网络，直接使用以下 WARP 脚本命令一把梭

   ```bash
   # 自动配置 WARP WireGuard 双栈全局网络（所有出站流量走 WARP 网络）
   bash <(curl -fsSL git.io/warp.sh) d
   ```

   其它相关命令

   > 配置为双栈全局代理，有可能会出现 vps 无法 ping 通外网的问题，有可能是 dns 或者是 host 受到了影响，不需要复杂的操作，直接运行
   > systemctl restart wg-quick@wgcf

   ```bash
   # 查看 WARP 脚本子命令列表
   bash <(curl -fsSL git.io/warp.sh) help
   
   # 重启 WARP WireGuard 网络接口
   systemctl restart wg-quick@wgcf
   
   # 禁用 WARP WireGuard 网络接口
   systemctl disable wg-quick@wgcf --now
   ```

   

