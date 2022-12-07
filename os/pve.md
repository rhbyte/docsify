# Proxmox VE

> PVE，全称Proxmox Virtual Environment，是基于Debian的Linux系统，虚拟机内核为KVM.

[项目官网Wiki](https://pve.proxmox.com/wiki/Main_Page)

---

## PVE系统安装——在J4125工控机

**step1：准备**

1. J4125工控机外接显示器、键盘

2. U盘-需要制作启动盘  

3. 准备rufus软件，用于制作启动盘  

4. 下载pve镜像 [官网地址](https://pve.proxmox.com/wiki/Main_Page )

**step2：制作镜像**

* 启动refus，选择U盘，然后选择pve的镜像，然后开始即可，注意会清空U盘的全部数据。

**step3：主机设置U盘启动**

* 进入主机bios设置即可。

**step4：安装PVE**

1. 选择一个硬盘格式化储存空间。  

2. 设置国家地区，能联网的话会自动帮你选择。  

3. 设置密码，邮箱随意。  

4. 依次设置网口、主机名、ip、网关、DNS的信息，最好接入一个路由器，设置一个静态ip即可从另外一台机子浏览器访问。  

5. 点击next后点击install进行安装。

6. 安装完毕重启后记得拔掉U盘。

**step5：配置PVE**

1.根据配置的ip地址访问PVE  `https://192.168.x.x:8006/`

---
