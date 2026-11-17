# 第二课作业：Ubuntu 22.04 命令练习

- 姓名：卢照炜
- 学号：1120252323
- 宿主机系统：Windows 11 24H2（Build 26100）
- 环境方式：VirtualBox 7.1.8 虚拟机（非容器），ISO 为 ubuntu-22.04.5-live-server-amd64.iso
- Ubuntu 版本：Ubuntu 22.04.5 LTS（jammy），内核 5.15.0-203-generic
- Agent 工具：DeepSeek Harness（Web GUI）

## 心得体会

这次作业我本来想用 Docker容器，但 WSL 下载一直停在 0.9%，Agent 判断是下载通道的问题，建议我换成 VirtualBox 加国内镜像，还提醒安装时必须把 Mirror 改掉，否则会卡在软件源上。我确认后照着做，十多分钟就装好了。分区、重启这些关键步骤都是我按提示自己点下去的，rm -i 删除时的 y/n 也是我自己判断的。中途遇到过找不到引导盘、装完重启又回到安装界面、登录名打错提示 Login incorrect，都是按 Agent 给的步骤一步步排查的。命令因为不能粘贴只能手敲，反倒让我记住了 cd、ls、cp -i 的写法。期间遇到了几次语法报错提醒，在agent辅助下完成修改并重新练习指令，印象更加深刻。
