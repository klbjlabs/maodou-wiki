# Install Docker on Mac OS X

#### 1. 为啥不用官方的安装包
虽然Mac系统下安装docker官方推荐的是使用 *`DockerToolbox`* 来安装

但是这货巨坑，常常莫名其妙的就不好用了，卸载还卸不干净，所以找了一种干净一些的方法来安装docker

> *linux用户可以无视，ubuntu上安装docker很简单，而且mac上安装docker的目的也不在于做生产，纯粹以连手和试验的目的使用的。*

#### 2. 准备工作
首先你得有个虚拟机软件，有以下几种选择：

| Software  | Description |
| --------- | ----------- |
| VirtualBox| mac版的vbox完全不像是mac软件啊，丑的一B，还有文字重叠的bug，完全不能忍 |
| VMware    | 据说很不错，没用过 |
| Parallels | 这个非常爽，不过是收费软件，缺点是价格很不良心 |

#### 3. 获取官方boot2docker镜像
获取地址：[https://github.com/boot2docker/boot2docker/releases](https://github.com/boot2docker/boot2docker/releases)

可以去这个网址找最新版本的 `boot2docker.iso` 来使用

#### 4. 安装
没啥说的，加载iso镜像直接就能用了
> 需要注意的是，这个是精简的linux系统除了docker和一些最基本的命令外其他的命令都没有。而且貌似也不能装软件，反正玩的是docker，宿主机环境提供基本的命令就够了。