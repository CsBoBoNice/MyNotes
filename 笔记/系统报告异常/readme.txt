解决Ubuntu系统中的程序崩溃报告，打开一个终端，输入以下命令：
sudo vim /etc/default/apport
把文件最后一行的把enabled=1改为enabled=0,保存并关闭文件.