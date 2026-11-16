#
姓名：谢渊然
宿主机系统：Windows 11 家庭版 中文版
虚拟机或容器方式：VMware Workstation Pro
Ubuntu 版本：22.04
Agent 工具：DeepSeek

心得：
在本次实践中，Agent（DeepSeek）帮我完成了Ubuntu升级时磁盘空间不足的扩容方案梳理，包括VMware虚拟硬盘扩展及GParted分区调整步骤。但其余关键操作均由我亲自确认并执行，包括实际的磁盘分区扩展、应用改动、系统版本升级以及后续的Git提交与PR创建。

搭建中遇到的最大问题是第一次更新Ubuntu时提示空间不足。我将报错现象交给DeepSeek分析，按其指导在VMware中扩容并在Ubuntu内完成分区，最终成功解决。

这次经历让我收获颇丰：不仅巩固了df -h、lsb_release -a等Ubuntu命令，更深刻体会到了虽然Agent能高效提供思路，但执行与最终确认必须由人负责。