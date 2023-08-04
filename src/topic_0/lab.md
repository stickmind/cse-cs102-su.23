# 实验 0：上手 Linux 开发环境

本课程开发环境选用远程 Linux 云端服务器和命令行工具，搭配本地终端和 VS Code 即可完成所有练习。

本次实验将带大家练习远程开发的流程，实验结束后，你应该能够连接上课程的远程服务器，并能够使用终端命令，搭配 VS Code 进行代码编辑。

>**❓FAQ** 为什么使用远程服务器进行开发？
>
>如果回到上个世纪 80 年代，即使电脑就在你的面前，你也必须使用终端才能对计算机进行操作。现如今，随着个人计算机的发展，虽然图形界面早已成熟，但在真实的开发场景中，使用终端开发仍然占据主导地位。大量的前后端框架、开源项目、开发工具，也严重依赖终端操作。
>
>本课程尽量还原类似的真实开发场景。当你以后有机会去软件公司实习时，你会发现，在这里掌握的技能，将会给你带来极大的回报。

## 登录课程云服务器

服务器 IP 地址为 `106.14.165.94`，在任何支持 `ssh` 命令的**计算机终端**[^1]上输入如下命令。

- Window 11 已搭载 Windows Terminal
- Linux/macOS 内置 Terminal

```
ssh YourName@106.14.165.94
```

第一次使用会弹出确认信息，输入 `yes` 后紧接着输入服务器用户密码（输入过程中，密码不会显示），成功后的输出信息如下。

```
The authenticity of host '106.14.165.94 (106.14.165.94)' can't be established.
ED25519 key fingerprint is SHA256:LHvn4qDvTdM1+GcJtG2f+uywxDA2JSys.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

Warning: Permanently added '106.14.165.94' (ED25519) to the list of known hosts.
YourName@106.14.165.94's password:     

Welcome to Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-52-generic x86_64)
```

查看服务器信息常用命令

- 查看主机名：`hostname`
- 查看用户名：`whoami`
- 查看硬盘空间：`df -h` （仅 `root` 权限）
- 查看内存状态：`free -h`
- 查看当前文件夹空间：`du --max-depth=1 -h`
- 修改登录密码：`passwd`

---

[^1]: [终端](https://wiki.mbalib.com/wiki/%E7%BB%88%E7%AB%AF%EF%BC%88%E8%AE%A1%E7%AE%97%E6%9C%BA%EF%BC%89)是一台电子计算机或者计算机系统，用来让用户输入数据，及显示其计算结果的机器。