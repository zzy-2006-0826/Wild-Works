# 第二课作业

- 姓名：陈怀政
- 学号：1120252814
- 宿主机系统：Windows 11 家庭中文版 24H2
- 环境方式：WSL2（Ubuntu 22.04）
- Ubuntu 版本：Ubuntu 22.04.5 LTS（`VERSION_ID="22.04"`）
- Agent 工具：DeepSeek Harness

## 心得

这次先用DSH确认了电脑是 Windows 11 家庭中文版、内存完整性开着，然后选择了 WSL2 。一开始以为跑一条 `wsl --install` 就能直接安装，但实际要先装 WSL 本体再导入 Ubuntu 发行版，这步是DSH帮我完成的。然后下载时 GitHub 直连只有 37 KB/s，DSH测了几个国内镜像，最后用阿里云拉 Ubuntu 镜像、用加速镜像拉 WSL 安装包。敲命令cat /etc/os-release 时，第一次漏了空格和斜杠，经几次检查才看到；对cp -i、mv -i、rm -i的确认有点不熟，不知道要敲 y；现在理解了 -i会在覆盖和删除前先问一句，按 Tab 也能补全路径。
