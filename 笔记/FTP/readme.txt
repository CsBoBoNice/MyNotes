



安装FTP
sudo apt-get install vsftpd

设置成开机启动
sudo systemctl enable vsftpd

关闭防火墙
service ufw stop

开启防火墙但允许FTP
ufw allow ftp

启动ftp服务
sudo systemctl start vsftpd

确认服务是否启动
sudo netstat -antup | grep ftp

vsftpd服务程序的主配置文件在/etc/vsftpd.conf

把源文件做一个备份
sudo mv /etc/vsftpd.conf /etc/vsftpd.conf_bak 

过滤注释
sudo grep -v "#" /etc/vsftpd.conf_bak > /etc/vsftpd.conf

修改配置文件
sudo vim /etc/vsftpd.conf

/*******************************************************************************/
# vsftpd 在独立模式下运行
listen=YES

# 监听 ipv6 还是 IPv4
#listen_ipv6=YES

#匿名用户登陆
anonymous_enable=NO

#本地用户登录
local_enable=YES

# 当用户第一次进入新目录时显示提示消息
dirmessage_enable=YES

use_localtime=YES

# 一个存有详细的上传和下载信息的日志文件
xferlog_enable=YES

# 保持标准日志文件格式
xferlog_std_format=YES

# 在服务器上针对 PORT 类型的连接使用端口 20（FTP 数据）
connect_from_port_20=YES

# vsftpd 将使用的 PAM 验证设备的名字
pam_service_name=vsftpd

rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem

rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

ssl_enable=NO

# 启用可以修改文件的 FTP 命令
write_enable=YES

# 本地用户创建文件的 umask 值
local_umask=022

# 打开 tcp 包装器
tcp_wrappers=YES

#只有用户名被明确列出在/etc/vsftpd.userlist 中的用户才允许登录到 FTP 服务器
#userlist_enable=YES                   # vsftpd 将会从所给的用户列表文件中加载用户名字列表
#userlist_file=/etc/vsftpd.userlist    # 存储用户名字的列表
#userlist_deny=NO

#将 FTP 用户限制在其 home 目录
#chroot_local_user=YES      #登录以后默认情况下是其 home 目录
#allow_writeable_chroot=YES #具有可写权限
#secure_chroot_dir=/var/run/vsftpd/empty

#开启被动模式
pasv_enable=YES
#local_root=/var/ftp
#pasv_min_port=40000
#pasv_max_port=45000 

/*******************************************************************************/

创建ftp用户，使用m参数，把ftp用户的home目录一起创建
sudo useradd -m ftpuser

设置ftp用户密码
sudo passwd ftpuser 


创建并编辑 /etc/vsftpd.userlist 文件
sudo vim /etc/vsftpd.userlist

没用到:

权限设置
如果是使用ftpuser的home目录，给与sudo权限
sudo vim /etc/sudoers
增加一行
ftpuser ALL=(ALL) NOPASSWD: ALL



FTP具有两种模式，分别是port模式(也叫主动模式)和pasv模式(也叫被动模式)

在主动模式下：客户端给服务器端的21端口发命令说，我要下载什么什么，
并且还会说我已经打开了自己的20端口，你就从这里把东西给我吧，
服务器收到后就会连接客户端已打开的20端口把东西传给客户端，这就是主动模式，
可以理解为服务端主动给客户端传输文件。

在被动模式下：客户端给服务器端的21端口发命令说，我要下载什么什么，
服务器端知道后，就打开一个空闲的高端口，
然后告诉客户端，我已经打开了某某端口，你自己进去拿吧，
于是客户端就从那个高端口进去拿文件了，这就是被动模式，可以理解为服务端被客户端拿走了东西


从主动模式到被动模式

在很久以前没有共享上网这种技术，一个电脑一个ip。
但是后来出现了，所以也就有了下面的问题。
大家都知道，共享上网就是很多台电脑共享一个公网IP去使用internet，
再打个比喻吧，某个局域网络出口的公网IP是210.33.25.108，
当一个内网用户192.168.1.100去访问外网的FTP服务器时，
如果采用主动模式的话，192.168.1.100告诉了FTP服务器我需要某个文件和我打开了20端口之后，
由于共享上网的原因，192.168.1.100在出网关的时候自己的IP地址已经被转换成了210.33.25.108这个公网IP，
所以服务器端收到的消息也就是210.33.25.108需要某个文件并打开了20端口，
FTP服务器就会往210.33.25.108的20端口传数据，这样当然会连接不成功了，
因为打开20端口的并不是192.168.1.100这个地址，在这种情况下被动模式就有用了。

在主动模式中，FTP的两个端口是相对固定的，如果命令端口是n的话，那数据端口就是n-1，
也就是说默认情况下，命令端口是21，数据端口就是20，
你把命令端口改成了600，那么数据端口就是599。
这样使用防火墙就很方便了，只要开通这两个端口就可以了，
但是如果客户端是共享上网的话那岂不是不能正常使用FTP了，
这样还是不行，一定需要被动模式。

在被动模式中，默认情况下命令端口是21，但是数据端口是随机的。
不过，因为被动模式中数据端口的范围是可以自定义的，因此也可以通过端口范围去配置防火墙。








