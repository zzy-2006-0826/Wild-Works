# 第二课作业：Ubuntu 环境搭建与 Agent 实践

- 姓名：张晋松
- 宿主机系统：Windows 11
- 环境方式：QEMU 11.1.3 虚拟机
- Ubuntu 版本：Ubuntu 22.04.5 LTS
- Agent 工具：DeepSeek Harness（DSH）

## 心得体会

Agent 先帮我确认宿主机没有 Docker 和 WSL，再把任务拆成下载 Ubuntu 镜像、注入 SSH 公钥、配置端口转发、命令练习和截图几步。我复核了 `VERSION_ID="22.04"` 及 `pwd`、`ls -la`、`cp -i`、`head` 的实际输出。QEMU 无法识别中文路径，改用 `subst` 映射 U: 盘；SSH 首次连接超时，等 cloud-init 完成后重试成功。这次练习让我更熟悉目录、文件和文本查看命令，也体会到 Agent 的方案要逐项验证，需要我来修改与整理。

## 截图

1. `01_Ubuntu版本.png`：Ubuntu 22.04.5 LTS 版本与内核信息
2. `02_目录定位.png`：`pwd`、`ls -la`、`cd`、`cd ..`
3. `03_文件操作.png`：`mkdir -p`、`touch`、`cp -i`、`mv -i`、`rm -iv`
4. `04_文本查看.png`：`cat`、`head -n`、`tail -n`、`wc -l`
5. `05_Agent过程.png`：Agent 的任务分解、实际命令与排错记录
