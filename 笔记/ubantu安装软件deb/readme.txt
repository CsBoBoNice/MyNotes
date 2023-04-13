sudo dpkg -i code_1.76.2-1678817801_amd64.deb
sudo apt-get -f install



卸载 彻底清除，包括配置
sudo dpkg --purge code


sudo find / -name .vscode
sudo rm /home/cs/.vscode/ -rf







1、Linux安装vs code

　　（1）、一键安装

　　直接在终端运行这航代码就可以了

sudo snap install --classic code

　　（2）、先下载安装包再安装

　　在官网下载好安装包后切换到下载目录下输入以下命令等待安装完成：

sudo dpkg -i code_1.71.0-1662018389_amd64.deb 

 

2、卸载vs code

　　vscode 在 Ubuntu 上的软件包名称为 code 。卸载vscode的方法有很多，选其中之一即可。具体如下：

　　(1)、 通过 apt-get 方式安装的,删除时会提示确认

sudo apt-get remove code # 只是卸载，保留配置
sudo apt-get --purge remove code # 彻底清除，包括配置
sudo apt-get purge code # 也是彻底清除

 

　　(2)、 通过 dpkg 方式安装的,删除时将没有确认提示

sudo dpkg -r code # 只是卸载，保留配置
sudo dpkg --remove code # 只是卸载，保留配置
sudo dpkg -r code # 彻底清除，包括配置
sudo dpkg --purge code # 彻底清除，包括配置




