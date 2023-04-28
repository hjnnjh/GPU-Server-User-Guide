# XJTU-SOM机器学习中心公共GPU服务器使用指南

## 如何登陆

### SSH命令行登陆

在校园网或者webvpn环境下，在终端中使用以下命令登陆虚拟机。

```sh
 ssh ubuntu@202.117.45.239 -p port
```

`port`为端口号，由管理员发送给使用者，登陆密码为：`test`。

每个虚拟机有两个账户：`root`和`ubuntu`，通过命令：

```sh
 su ubuntu
 su
```

可在两个账户之间互相切换。通过命令：

```sh
 passwd root
 passwd ubuntu
```

可自行修改两个账户的密码（同时也是登陆密码），并且也可以自行配置SSH密钥登陆。

如果有校外登陆服务器的需求，可使用webvpn，也可自行用具有公网IP的服务器作为跳板机，配置`frp`[内网穿透服务](http://pluckytyx.top/2021/01/%E5%9C%A8%E5%AE%B6%E8%BF%9E%E5%86%85%E7%BD%91%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%AE%8C%E5%85%A8%E6%8C%87%E5%8D%97)。

### SSH登陆图形化桌面

在校园网或者webvpn环境下，使用软件MobaXterm登陆虚拟机的图形化桌面。软件配置步骤如下：

- 选择Session选项卡；
- `Remote host`填202.117.45.239，`Specify username`填ubuntu，`Port`填端口号，`Remote environment`选择Xfce4 desktop，其他选项默认；

MobaXterm的功能很强大，可参考如下[使用教程](https://zhuanlan.zhihu.com/p/61013117)。

### VScode Remote SSH

Vscode Remote SSH可以实现在服务器上写代码像在本地环境中写代码一样舒适的体验，可参考此[教程](https://zhuanlan.zhihu.com/p/68577071)。

## 虚拟机环境配置

默认配置，可按需调整。

### 硬件配置

- CPU：4核
- 内存：32GB
- DISK：125GB
- GPU：按需分配

### 软件配置

- ubuntu版本：18.04.01；
- 显卡驱动版本：470.103.01；
- CUDA版本：11.3；
- cuDNN版本：无，可自行安装；
- Anaconda 3 2021-05 with two environments:
  - `base`
  - `deep_learning`
- Pycharm 2021
- PyTorch 1.10.2 in env `deep_learning`
- Pyro 1.8.0 in env `deep_learning`

其他软件和环境可按需配置。

## 常用命令

查看显卡信息和占用情况：

```sh
 nvidia-smi
```

实时查看显卡运行情况（0.1秒间隔刷新）：

```sh
 watch -n 0.1 nvidia-smi
```

查看系统信息：

Install neofetch first:

```sh
 sudo apt install neofetch
```

```sh
 neofetch
```

查看CPU、内存占用情况：

Install stop first:

```sh
 sudo apt install htop
```

```sh
 htop
```

