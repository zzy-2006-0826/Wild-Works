# 第二课作业：Ubuntu 环境搭建与 Agent 实践

- **姓名**：刘子铭
- **学号**：1120253357
- **宿主机系统**：Windows 10（10.0.26200，x64）
- **实际方式**：VMware Workstation 虚拟机 + 其中运行的 Docker 容器（`docker exec -it ubuntu22 bash`）
- **Ubuntu 版本**：22.04.4 LTS（jammy），容器内 `cat /etc/os-release` 显示 `VERSION_ID="22.04"`
- **Agent 工具**：ZCode CLI

## 心得与遇到的问题

我用 VMware 里已有的 Ubuntu 虚拟机，在其中用 Docker 跑 ubuntu:22.04 容器，命令都在容器内执行。Agent 帮我确认系统情况，用 vmrun 和 SSH 建好连接，再装 Docker、导入 22.04 根文件系统。遇到两个问题：apt 源报 403 且签名失效，换镜像站后恢复；第一次截图窗口是空的，排查发现桌面锁屏，中文输入法还把命令拦成乱码，关掉输入法后才正常。每组输出我都自己核对，`pwd`、`ls` 确认目录，`cp -i`、`mv -i`、`rm -i` 的覆盖提示都真实出现。收获是分清了容器与虚拟机的区别，也明白排错要先看现象再定位原因。
