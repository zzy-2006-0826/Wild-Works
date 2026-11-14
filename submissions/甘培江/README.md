# 第二课作业：Ubuntu 环境搭建与 Agent 实践

- 姓名：甘培江
- 宿主机系统：Windows 11（Build 26200）
- 环境方式：WSL2（手动安装 WSL 2.2.4 MSI，再从国内镜像导入 Ubuntu 根文件系统）
- Ubuntu 版本：Ubuntu 22.04.5 LTS，`VERSION_ID="22.04"`
- Agent 工具：TRAE

## 环境搭建方式

没有使用 `wsl --install` 默认流程：本机访问 GitHub 与微软下载服务器超时，命令长时间卡在 2% 左右。实际步骤为：

1. 用 DISM 启用 `Microsoft-Windows-Subsystem-Linux` 与 `VirtualMachinePlatform` 两个系统功能；
2. 下载并安装 WSL 2.2.4 的 MSI 组件；
3. 从南京大学镜像站下载 Ubuntu 22.04 的 WSL rootfs，用 `wsl --import` 导入为 `Ubuntu-22.04`；
4. 创建用户 `ganpeijiang` 并加入 sudo 组，在 Ubuntu 内配置 git 用户名与邮箱。

## 命令练习

练习目录为 `~/course-lab/day1`，覆盖三组内容：

- 目录定位：`pwd`、`ls`、`ls -la`、`cd`、`cd ..`
- 文件操作：`mkdir -p`、`touch`、`cp -i`、`mv -i`、`rm -i`
- 文本查看：`cat`、`head -n 2`、`tail -n 2`，查看内容为自建的 5 行文本文件

## 截图清单

| 文件 | 内容 |
|---|---|
| `01_Ubuntu版本.png` | `cat /etc/os-release`，确认 `VERSION_ID="22.04"` |
| `02_目录定位.png` | 目录定位命令及输出 |
| `03_文件操作.png` | 文件创建、复制、改名与交互式删除 |
| `04_文本查看.png` | `cat`、`head`、`tail` 查看文本 |
| `05_Agent过程.png` | Agent 诊断网络问题并给出替代安装方案的过程 |

## 心得体会（约 200 字）

这次搭建环境，Agent 主要帮我规划步骤、解释命令和排错，真正在 Ubuntu 里敲命令、截图、核对输出都是我自己完成的。最麻烦的问题是 `wsl --install` 一直卡在 2%，我原以为是自己操作错了；Agent 逐项测试网络后确认是访问 GitHub 和微软服务器超时，改用国内镜像站下载 Ubuntu 根文件系统并手动导入后，环境很快装好，我也理解了镜像的作用——同样的文件从国内服务器下载快很多。推送时又遇到两个坎：GitHub 早已不支持账号密码认证，而终端里粘贴令牌反复失败，最后改用 SSH 密钥才推送成功，一次配置之后就不用再输密码。练习中 `rm -i` 删除前会再次询问，`history` 能回看操作记录，这些细节让我意识到命令行虽然直接，但每一步都要自己确认。Agent 明显提升了排错和搭建效率，但它说“已完成”时，结果仍要我自己验证，不能直接照单全收。
