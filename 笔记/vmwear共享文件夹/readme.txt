安装VMware tools



cp VMwareTools-10.3.25-20206839.tar.gz ~/
cd
sudo tar -xzvf VMwareTools-10.3.25-20206839.tar.gz
cd vmware-tools-distrib/
sudo ./vmware-install.pl
sudo rm VMwareTools-10.3.25-20206839.tar.gz
sudo rm vmware-tools-distrib/ -rf

在VMware虚拟机中安装了Ubuntu系统之后，需要安装VMware tools工具软件， 可以得到更好的操作体验。

(1) 打开Ubuntu虚拟机，选择菜单：虚拟机(M) —> 安装 VMware Tools（T）

作者的Ubuntu虚拟机已经安装过VMware Tools工具，所以，提示重新安装。如下图：

然后，Ubuntu系统的桌面，弹出一个VMware Tools光盘目录，如下图：

双击光盘，弹出对话框如下：

然后，打开一个终端，查看 /media目录，如下：

可以看到，虚拟机光盘挂载到 /media/VMware Tools目录下。

然后，执行如下命令：

tar -xvzf VMwareTools-9.6.1-1378637.tar.gz -C /tmp/

把
VMwareTools-9.6.1-1378637.tar.gz文件解压到 /tmp 目录下。

解压完成之后，就得到 /tmp/vmware-tools-distrib目录。


进入到 /tmp/vmware-tools-distrib目录，执行如下命令：

sudo ./vmware-install.pl





常用命令

查看共享目录 vmware-hgfsclient
常见问题
问题1: /mnt/hgfs 目录下找不到共享文件

解决方案: 执行命令： sudo /usr/bin/vmhgfs-fuse .host:/ /mnt/hgfs -o subtype=vmhgfs-fuse,allow_other

在~/.bashrc 文件写入
echo "123qweasd" | sudo -S /usr/bin/vmhgfs-fuse .host:/ /mnt/hgfs -o subtype=vmhgfs-fuse,allow_other
echo ""
