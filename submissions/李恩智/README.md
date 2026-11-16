# 第二课作业：Ubuntu 22.04 环境搭建与命令练习

- 姓名：李恩智
- 宿主机系统：Windows 25H2（内部版本 26200，Intel Core Ultra 9 275HX）
- 环境方式：QEMU 5.0 虚拟机（免安装便携版）+ Ubuntu 22.04.5 LTS 云镜像（cloud-init 自动配置）
- Ubuntu 版本：Ubuntu 22.04.5 LTS，`VERSION_ID="22.04"`（内核 5.15.0-203-generic）
- Agent 工具：DeepSeek Harness（DSH）Agent，负责方案规划、环境搭建、排错与命令练习辅助

## 截图清单

| 文件 | 内容 |
|---|---|
| `01_Ubuntu版本.png` | 虚拟机内 `cat /etc/os-release`，可见 `VERSION_ID="22.04"` |
| `02_目录定位.png` | `cd` / `pwd` / `ls` / `ls -la` / `mkdir -p sub1/sub2` / `cd ..` |
| `03_文件操作.png` | `mkdir -p` / `touch` / `cp -i`（覆盖询问回答 n、y）/ `ls -la` |
| `04_文本查看.png` | `seq 1 20 > nums.txt` / `cat nums.txt` |
| `05_Agent过程.png` | Agent 界面中可见的搭建方案、执行步骤与排错过程 |

## 搭建过程简述

1. 先用 Agent 检查宿主机：我考虑到电脑本身内存吃紧，所以暂时放弃安装较大模块的虚拟机，因此 DSH 建议选择免管理员权限的 QEMU 便携虚拟机方案（QEMU 来自本机已安装的 Vitis 2020.2 自带组件）；
2. 下载 Ubuntu 22.04.5 官方云镜像并校验 SHA256，用 `qemu-img` 建立 20 GB 写时复制磁盘；
3. 制作 cloud-init 种子盘，自动创建 `student` 用户、配置时区/SSH/apt 国内镜像与自动登录；
4. 启动虚拟机，在控制台执行 `cat /etc/os-release` 确认 `VERSION_ID="22.04"`；
5. 在 `~/practice/lesson2` 中练习目录定位、文件操作、文本查看三组命令并截图。

## 心得与问题

这次作业，Agent 帮我完成了方案选择、镜像下载、虚拟机搭建与练习操作的建议；我确认了版本输出，然后进行练习测试并截图。在使用 Agent 过程中我发现 Agent 没有管理员权限，使得 WSL 安装时报错 `0x80073D28 需要管理员权限`。解决方式很朴素，我直接让 Agent 换了一种搭建方式，当然，这个想法也是 Agent 提出的，但是基于它的便捷性和可行性，我毫无疑问选择听从 Agent，之后 DSH 从 QEMU 上游补齐 `pc-bios` 固件后成功启动 QEMU 虚拟机方案。对于这次作业，收获肯定是有不少的，比如我第一次真正意义上接触了 GitHub 和虚拟机，同时对于这种对我来说独特而新奇的命令行操作方式有了体验和实感。但是我现在对于这些东西的了解几乎是有些照葫芦画瓢了，这些基础内容在我们的实际工程中究竟发挥怎样的作用？我依然没有明白，当然，我接下来会在这些问题上继续加深了解。
