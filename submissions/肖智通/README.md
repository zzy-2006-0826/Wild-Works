# 第二课作业：Ubuntu 22.04 环境与命令练习

**姓名**：肖智通
**宿主机系统**：Windows 11（25H2，Intel Core i7-14650HX）
**环境方式**：WSL2（Windows Subsystem for Linux 2，Windows 11 上的轻量 Linux 环境，真 Linux 内核）
**Ubuntu 版本**：Ubuntu 22.04.5 LTS（Jammy Jellyfish）
**辅助 Agent 工具**：DeepSeek（负责环境方案选择、命令练习设计、排错建议）

## 截图说明

| 文件名 | 内容 |
| --- | --- |
| 01_Ubuntu版本.png | Ubuntu 22.04 版本信息（VERSION_ID="22.04"） |
| 02_目录定位.png | pwd / ls / ls -la / cd / cd .. 目录定位练习 |
| 03_文件操作.png | mkdir -p / touch / cp -i / mv -i / rm -i 文件操作练习 |
| 04_文本查看.png | cat / head -n / tail -n / grep / wc 文本查看练习 |
| 05_Agent过程.png | Agent 对话界面中的方案分析与排错过程 |

## 心得体会（约 200 字）

这次作业我在 Agent 辅助下用 WSL2 在 Windows 11 上搭建了 Ubuntu 22.04.5 LTS 环境，练习了 pwd、cd、ls、mkdir、touch、cp、mv、rm、cat、head、tail、grep 等命令。Agent 帮我完成了方案选择与排错：一开始想用 Docker，检查发现本机未安装；改用 WSL 时又遇到应用商店下载太慢、GitHub 下载不通等问题，Agent 逐个排查，最后用清华镜像的官方最小系统包配合 WSL2 完成搭建。启用系统组件和重启由我自己确认操作。我的体会是：遇到报错先自己读错误信息，再带着具体现象问 Agent，效率最高；这次也真正理解了相对路径与绝对路径、> 与 >> 重定向的区别。
