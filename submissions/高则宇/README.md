# 第二课作业：Ubuntu 22.04 环境搭建与命令练习

- 姓名：高则宇
- 宿主机：Windows 11 家庭版 25H2（Build 26200）
- 环境方式：QEMU 11.1.3 虚拟机（MSYS2 安装，TCG 软件模拟；未使用 WSL / Docker）
- Ubuntu 版本：Ubuntu 22.04.5 LTS (Jammy Jellyfish)
- Agent 工具：DeepSeek Harness（模型 DeepSeek-V4.1-Flash）

## 环境与操作说明

当前 Windows 账户没有管理员权限，无法安装 WSL2 或 Docker Desktop，因此选择 QEMU 虚拟机方案：

1. 用 MSYS2 安装 `mingw-w64-ucrt-x86_64-qemu`；
2. 下载 Ubuntu 22.04 cloud image（`jammy-server-cloudimg-amd64.img`），并扩容 8 GiB；
3. 用 cloud-init 的 NoCloud seed ISO 创建 `student` 用户并注入 SSH 公钥；
4. 启动参数：`qemu-system-x86_64 -m 4096 -smp 4 -drive file=jammy.img,format=qcow2,if=virtio -netdev user,hostfwd=tcp:127.0.0.1:2222-:22`；
5. 通过 `ssh -p 2222 student@127.0.0.1` 登录，在 `~/practice` 目录完成练习。

## 截图清单

| 文件 | 内容 |
| --- | --- |
| 01_Ubuntu版本.png | `cat /etc/os-release`、`uname -r`、`hostnamectl`，可见 `VERSION_ID="22.04"` |
| 02_目录定位.png | `cd`、`pwd`、`ls -la`、`cd ..` |
| 03_文件操作.png | `touch`、`cp -i`、`mv -i`、`rm -i`（含确认提示） |
| 04_文本查看.png | `cat`、`head -n 3`、`tail -n 4`、`wc -l` |
| 05_Agent过程.png | Agent 界面中的方案、排错分析和执行记录 |

## 心得体会（约 200 字）

这次作业里，Agent 先帮我分析环境：电脑没有管理员权限，装不了 WSL 和 Docker，于是改用 MSYS2 里的 QEMU 跑 Ubuntu 22.04 云镜像。它替我写了 cloud-init 配置和启动脚本，也帮我排查了第一次 SSH 登录失败的问题——串口日志显示 user-data 带了 UTF-8 BOM，cloud-init 直接忽略了配置，去掉 BOM、重建镜像后才登录成功。命令部分我按课程要求逐条输入并核对输出：用 pwd、ls、cd 确认目录位置，用 touch、cp、mv、rm 观察提示和文件变化，用 cat、head、tail 查看练习文本。我最大的收获是学会看串口日志和用 SSH 连接虚拟机，也理解了 -i 选项和管道 | 的作用；Agent 能加快搭建，但每一步结果还是要自己确认。
