# 第二课作业：Ubuntu 环境搭建与 Agent 实践

| 项目 | 内容 |
|---|---|
| 姓名 | 熊乐 |
| 宿主机系统 | Windows 11 家庭中文版 25H2（Build 26200.9974） |
| 虚拟化方式 | VMware Workstation 17.6.4 虚拟机（非 Docker） |
| Ubuntu 版本 | Ubuntu 22.04.5 LTS（Desktop，64 位） |
| Agent 工具 | DeepSeek Harness（deepseek-flash） |
| 提交日期 | 2026-11-16 |

## 心得（约 200 字）

先用 Agent 检查了电脑：它确认 VMware 已经装好，还发现我之前那台虚拟机是 Ubuntu 24.04.5，与作业要求的 22.04 不符，磁盘里也只有 24.04 的镜像。它据此规划了新建 22.04 虚拟机的步骤，并给出命令练习脚本；而下载 ISO、在 VMware 里新建虚拟机、填账号密码、进系统敲命令并截图，都由我自己确认并完成。

遇到的问题主要是版本不对，现成的虚拟机只能放弃、重新装一台；另外 Agent 的终端连不上外网，镜像必须我自己用浏览器下载。VMware 的简易安装跳过了大部分向导，我不太确定它装了什么，最后靠 `cat /etc/os-release` 才确认版本正确。

收获是学会用它快速确认系统版本，也体会到带 `-i` 的命令会先问一句，能减少误删；Agent 适合查环境、给步骤、解释报错，但每一步的结果仍要自己验证。

## 截图清单

| 文件 | 内容 |
|---|---|
| `01_Ubuntu版本.png` | 终端执行 `cat /etc/os-release`，可见 `VERSION_ID="22.04"` |
| `02_目录定位.png` | `pwd`、`ls`、`ls -la`、`cd`、`cd ..` |
| `03_文件操作.png` | `mkdir -p`、`touch`、`cp -i`、`mv -i`、`rm -i` |
| `04_文本查看.png` | `cat`、`head -n`、`tail -n`、`less`（按 q 退出） |
| `05_Agent过程.png` | Agent 检查环境、规划步骤、讲解命令的界面 |

## 环境信息（自查用）

- 练习目录：`~/lesson2`
- 确认版本：`cat /etc/os-release` → `VERSION_ID="22.04"`
- 提交路径：`submissions/熊乐/`
