第二课作业：Ubuntu 环境搭建与 Agent 实践
- 姓名：汪欣智
- 宿主机系统：Windows 11 家庭版 中文版
- 环境方式：Docker 容器（Docker Desktop 29.9.3，WSL2 后端）
- Ubuntu 版本：22.04.5 LTS（容器内执行 cat /etc/os-release 确认，非宿主机）
- Agent 工具：WorkBuddy（AI Agent，用于方案指导、命令讲解与排错）
提交内容
文件
说明
01_Ubuntu版本.png
容器内执行 cat /etc/os-release，可见 VERSION_ID="22.04"
02_目录定位.png
pwd、ls、ls -la、cd、cd ..
03_文件操作.png
mkdir -p、touch、cp -i、mv -i、rm -i（含 y 确认）
04_文本查看.png
echo 写入内容后 cat、head -n、tail -n
05_Agent过程.png
Agent 排错过程：分析报错、给出方案
心得
这次作业我用 Agent 辅助搭建了 Docker 环境并练习了 Ubuntu 基础命令。Agent 帮我规划了整个流程：从安装 Docker Desktop、配置 WSL2，到拉取 Ubuntu 22.04 镜像的每一步都给出了具体指令，我负责执行并确认每个结果。开始我并不明白学习Ubuntu的意义，于是询问了AI，明白了这是用虚拟环境创造零成本试错的机会。过程中遇到的主要问题是拉取镜像失败：在Agent指导下进行了多次操作，都未成功。后来才知道Docker Hub 国内直连不通，且代理软件的端口每次重启都会变化导致配置失效。Agent 分析后建议放弃代理、改用国内镜像加速源直连，才成功完成练习。我的收获很大：首先了解虚拟机的意思和存在的意义；然后理解了容器的隔离性——命令必须在容器内执行，在 Windows 终端里跑只会报"找不到文件"；最后也是体会到 Agent 的正确用法是让它出方案、自己做决策和验证，遇到报错把信息完整反馈给它，这样可以快速发现问题，高效完成任务。
