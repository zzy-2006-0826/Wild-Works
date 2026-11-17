# 第二课作业：Ubuntu 环境搭建与 Agent 实践

- 姓名：何荣齐
- 学号：1120261426
- 宿主机系统：Windows 11 家庭版（无管理员权限，未启用 WSL）
- 虚拟化方式：QEMU 11.1.3（纯软件模拟，MSYS2 安装）
- Ubuntu 版本：Ubuntu 22.04.5 LTS（Jammy Jellyfish），内核 5.15.0-203-generic
- Agent 工具：DeepSeek Harness（对话式 Agent）

## 心得（约 200 字）

这次最麻烦的不是敲命令，而是让 Ubuntu 真正跑起来。本机没有 WSL，也没有管理员权限装 VMware，Agent 帮我比较了几种方案，最后选了免安装的 QEMU，并给出用 cloud-init 设置账号、用 monitor 通道注入按键的思路。

中间踩了一个坑：我按提示写好 user-data，虚拟机却一直登录失败。Agent 分析后判断是文件带了 BOM，导致 cloud-init 不认这段配置；去掉 BOM 重写后一次就登录成功了。这一步让我记住了"配置文件对格式很敏感"。

命令部分我自己确认过每一步：pwd、ls -la 看目录，touch/cp -i/mv -i/rm -i 做文件操作，cat/head/tail 看文本，删除只在练习目录里做。截图都是实际执行的结果。