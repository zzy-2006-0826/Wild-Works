# 第二课作业：Ubuntu 22.04 环境与命令练习

- 姓名：谢镍权
- 学号：1120260094
- 宿主机系统：Windows 11
- 环境方式：Docker Desktop（WSL2 后端），容器 ubuntu:22.04；镜像由 Ubuntu 官方 base rootfs 导入（Docker Hub 拉取超时）
- Ubuntu 版本：22.04.5 LTS
- Agent 工具：DeepSeek（对话式 Agent）

## 心得

在这次作业中，我让 DeepSeek 帮我梳理 Windows 11 上 WSL2 和 Docker Desktop 的安装顺序。它提醒我要用管理员权限安装并重启，我照做后检查了 docker info 和容器状态。拉取 ubuntu:22.04 时 Docker Hub 一直超时，DeepSeek 建议改用 Ubuntu 官方 base rootfs 导入，我才把容器跑起来。练习命令时我对 cp -i、mv -i 的覆盖提示不熟悉，它解释了 -i 的作用，我用 y/n 分别测试了覆盖和取消。现在我能分清宿主机和容器的目录，也会用 pwd、ls、cp、head 等命令完成基本文件操作了，总的来说收获挺大的。
