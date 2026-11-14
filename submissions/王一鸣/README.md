# 第二课作业：Ubuntu 22.04 环境搭建与 Agent 实践

- **姓名**：王一鸣
- **宿主机系统**：Windows 11 家庭版 25H2（Build 26200）
- **环境方式**：Docker 容器。Docker Engine 运行在 WSL2（Hyper-V 虚拟机）中的 Ubuntu 22.04 上，容器镜像为 `ubuntu:22.04`（由 Ubuntu 官方 ubuntu-base-22.04.5 根文件系统 `docker import` 构建），容器名为 `ubuntu-practice`；Ubuntu 虚拟磁盘、Docker 数据与下载的镜像都存放在 `E:\ubuntu`，未在 C 盘新增安装（WSL 组件为系统原有）。
- **Ubuntu 版本**：22.04.5 LTS（`VERSION_ID="22.04"`，见 01 截图）
- **Agent 工具**：DeepSeek Harness（DSH）

## 截图

| 文件 | 内容 |
|---|---|
| `01_Ubuntu版本.png` | 容器内执行 `hostname`、`cat /etc/os-release`，可确认 `VERSION_ID="22.04"` |
| `02_目录定位.png` | `pwd`、`ls -la`、`cd`、`cd ..` |
| `03_文件操作.png` | `mkdir -p`、`touch`、`cp -i`、`mv -i`、`rm -i` |
| `04_文本查看.png` | `cat`、`head -n 3`、`tail -n 3` |
| `05_Agent过程.png` | Agent 界面中可见方案、分析步骤、排错记录与工具调用 |

## 心得体会（约 200 字）

这次作业是在 Agent 辅助下完成的。给他读作业说明，再根据我的电脑情况（无管理员权限、C 盘满了）规划方案：把 Ubuntu 22.04 装到 E 盘，以 WSL2 作为虚拟机，再用 Ubuntu 官方 ubuntu-base 根文件系统在 Docker 容器里搭练习环境。中途遇到 Docker Hub 直连失败，Agent 改用 `docker import` 离线构建镜像；截图时又碰到缩放和中文输入法干扰，它改成 DPI 感知截图并用剪贴板粘贴命令，问题都解决了。

我自己确认了每一步的结果：用 `cat /etc/os-release` 看到 `VERSION_ID="22.04"`，用 `docker ps` 确认容器在运行，最后逐张检查了截图和命令输出。通过练习，我熟悉了 pwd、ls、cd、mkdir、cp、mv、rm、cat、head、tail 等命令，也体会到 Agent 说“完成”之后，还要自己看输出再验证。
