# 第二课作业：Ubuntu 环境搭建与 Agent 实践

## 基本信息

| 项目        | 内容                                                        |
| --------- | --------------------------------------------------------- |
| 姓名        | 林苏阳                                                       |
| 宿主机系统     | Windows 11 家庭中文版（版本 10.0.26300）                           |
| 虚拟化方式     | VirtualBox 7.2.22 虚拟机                                     |
| Ubuntu 版本 | Ubuntu 22.04.5 LTS (Jammy Jellyfish)，`VERSION_ID="22.04"` |
| Agent 工具  | DeepSeek Harness（dsh，MIT 协议开源）                            |

## 心得体会（约 200 字）

刚开课的时候其实有点懵，课程录制默认我已经安装了ubuntu，所以其实完全没接触过的我听得一头雾水，而我运用了课程提到的agent，让他帮我访问了虚拟器网站，找到了正确的版本。同时，他还跟我合作解决了虚拟器未强化无法粘贴的问题。这一次经历震撼了我，我发现agent居然真的可以操作我的电脑，执行很多行为，而我只需要提出需求。这真的是一个充满潜力的生产工具，同时正因如此，我觉得课程提到的让每一步操作都可追责，并且自己一定要核对是完全正确的，ai的处理能力可能让我们给他过多的信任，还是需要自己审查的。这次我也把课件给agent，他给了我更清晰的一个讲解，帮我巩固了内容，总的来说，这次课让我第一次接触agent，我打开了新世界的大门。


**一、Agent 帮我完成了什么，哪些操作由我自己确认**

agent帮我分析了优化虚拟机过程中的报错，给出了原因和处理办法，但他可能因为截图不全导致误判了我的版本，他显示了24那版。我自己核查后纠正。

**二、搭建或练习中遇到的问题，怎么解决的**

装系统时先误进了「试用 Ubuntu」桌面，没有真正安装，硬盘一直是 2 MB，后来才从桌面里的
Install Ubuntu 重新启动安装程序；

- 虚拟硬盘中途丢失过一次，重新创建后才装上（11.25 GB）；
- 增强功能安装报 make: not found，装了 gcc make perl 后重新编译才成功；
- 粘贴一开始用不了，装完匹配版本（7.2.22）的增强功能并重启后才正常。

**三、对 Ubuntu 命令或 Agent 使用的收获**

- 一开始不理解为什么要加参数，实际用 cp -i 时看到它停下来问 overwrite?，
  发现这是在保护已有文件；
- 加了 -la才看得到 .bashrc 这类隐藏文件和权限信息；
- 对 Agent 的认识：它能给出分析和步骤，但结论需要自己用命令核对，比如版本号这种事一定要
  自己 cat /etc/os-release 看一眼。

---

## 截图说明

| 文件                    | 内容                                                                                                   |
| --------------------- | ---------------------------------------------------------------------------------------------------- |
| `01_Ubuntu版本.png`     | 在终端执行 `cat /etc/os-release`，可见 `VERSION_ID="22.04"`、`VERSION="22.04.5 LTS (Jammy Jellyfish)"`        |
| `02_目录定位.png`         | 练习 `pwd`、`ls`、`ls -la`、`cd /etc`、`cd ..`；`ls -la` 可看到 `.bashrc`、`.profile`、`.config` 等隐藏项及权限、时间信息    |
| `03_文件操作.png`         | 练习 `mkdir -p docs/sub`、`touch`、`cp -i`（出现 `overwrite?` 提示并输入 y）、`mv -i`、`rm -i`（出现 `remove` 提示并输入 y） |
| `04_文本查看.png`         | 生成 20 行测试文件后执行 `cat`、`head -n 5`、`tail -n 5`，可看出前 5 行与后 5 行的区别                                       |
| `05_Agent过程.png`      | 向 DeepSeek Harness 提问报错原因，界面显示它读取截图并给出「原因」分析的过程                                                      |
| `06_Agent过程_原因分析.png` | 同一对话的延续，显示它定位到 `make: not found` 并解释内核模块编译失败的原因                                                      |

## 命令练习记录

练习目录：`/home/linsuyang/practice`

```bash
# 目录定位
pwd
ls
ls -la
cd /etc
pwd
cd ..
pwd

# 文件操作
mkdir -p docs/sub
touch note.txt
cp -i note.txt note_copy.txt
cp -i note.txt note_copy.txt    # 第二次触发 overwrite 确认
mv -i note_copy.txt docs/
mv -i docs/note_copy.txt docs/moved.txt
ls
ls docs
rm -i docs/moved.txt
ls docs

# 文本查看
seq 1 20 > numbers.txt
wc -l numbers.txt
cat numbers.txt
head -n 5 numbers.txt
tail -n 5 numbers.txt
```






