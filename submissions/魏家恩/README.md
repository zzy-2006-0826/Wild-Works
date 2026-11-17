# 第二课作业：Ubuntu 环境搭建与 Agent 实践

- 姓名：魏家恩
- 宿主机系统：macOS（Apple Silicon，arm64）
- 环境方式：Docker Desktop，容器内运行 Ubuntu
- Ubuntu 版本：Ubuntu 22.04 LTS（`/etc/os-release` 中 `VERSION_ID="22.04"`）
- Agent 工具：CodeArts 代码智能体客户端（组内优先推荐开源 Codex CLI，本次使用该客户端完成方案规划与排错，如实注明）

## 环境搭建过程

1. 下载并安装 Docker Desktop（Apple Silicon 版），启动后确认 `docker version` 可用。
2. 直接执行 `docker pull ubuntu:22.04` 时提示 `context deadline exceeded`，判断为 Docker Hub 直连超时。
3. 改用国内镜像拉取：`docker pull docker.m.daocloud.io/library/ubuntu:22.04`，成功后用 `docker tag` 重命名为 `ubuntu:22.04`。
4. 用 `docker run -d --name ubuntu-practice ubuntu:22.04 sleep infinity` 启动容器，`docker exec -it ubuntu-practice bash` 进入。
5. 在容器内执行 `cat /etc/os-release`，确认 `VERSION_ID="22.04"`，截图保存为 `01_Ubuntu版本.png`。
6. 退出后用 `docker start -ai ubuntu-practice` 可重新进入同一容器继续练习。

## 命令练习

练习目录为容器内 `/root/practice`，只操作自己创建的文件。

- 目录定位：`pwd`、`ls`、`ls -la`、`cd`、`cd ..`（截图 `02_目录定位.png`）
- 文件操作：`mkdir -p`、`touch`、`cp -i`、`mv -i`、`rm -i`（截图 `03_文件操作.png`）
- 文本查看：`cat`、`head -n`、`tail -n`，补充 `less` 按 q 退出（截图 `04_文本查看.png`）
- Agent 辅助过程（截图 `05_Agent过程.png`）

## 心得（约 200 字）

这次作业第一次在自己电脑上搭 Ubuntu 环境，选的是 Docker 容器。Agent 先帮我理清顺序：启动 Docker Desktop、确认守护进程、拉镜像、进容器验证版本；安装和拉取由我确认，版本和目录结果也是逐条核对后才截图。实际拉 `ubuntu:22.04` 时 Docker Hub 报 `context deadline exceeded`，Agent 提示换国内镜像 `docker.m.daocloud.io`，拉下来后重新打 tag，这一步让我第一次分清镜像地址和本地镜像名的区别。命令里最不熟悉的是 `cp -i` 和 `rm -i` 的确认提示，输入 `y` 才执行，我用 `ls -la` 核对文件确实变了。退出容器后终端回到 Mac，我一度以为环境没了，用 `docker start -ai` 重新进入并 `pwd` 确认位置才放心。收获是：命令不难，难的是随时确认当前在哪、改的是哪个文件，Agent 给步骤，结果必须自己核对。

## 截图清单

| 文件 | 内容 |
|---|---|
| `01_Ubuntu版本.png` | 容器内 `cat /etc/os-release`，可见 `VERSION_ID="22.04"` |
| `02_目录定位.png` | `pwd`、`ls`、`ls -la`、`cd`、`cd ..` |
| `03_文件操作.png` | `mkdir -p`、`touch`、`cp -i`、`mv -i`、`rm -i` |
| `04_文本查看.png` | `cat`、`head -n`、`tail -n`、`less` |
| `05_Agent过程.png` | Agent 给出的步骤/排错过程界面 |