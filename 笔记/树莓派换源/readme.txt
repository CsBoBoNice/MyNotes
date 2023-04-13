



查看自己的版本类型
lsb_release -a


清华源地址
https://mirrors.tuna.tsinghua.edu.cn/help/debian/

Debian Buster 以上版本默认支持 HTTPS 源。如果遇到无法拉取 HTTPS 源的情况，请先使用 HTTP 源并安装：

sudo apt install apt-transport-https ca-certificates


换源

sudo vim /etc/apt/sources.list

/**************************************************************************************/
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free

deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free

deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free

deb https://mirrors.tuna.tsinghua.edu.cn/debian-security bullseye-security main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian-security bullseye-security main contrib non-free

# deb https://security.debian.org/debian-security bullseye-security main contrib non-free
# # deb-src https://security.debian.org/debian-security bullseye-security main contrib non-free
/**************************************************************************************/

sudo vim /etc/apt/sources.list.d/raspi.list

/**************************************************************************************/
deb http://mirrors.tuna.tsinghua.edu.cn/raspberrypi/ bullseye main
/**************************************************************************************/






未使用

Connection reset by peer

在 apt 2.1.9 及以后的版本中，apt 的 HTTP Pipelining 特性与 Nginx 服务器疑似存在一定的不兼容问题，可能导致高带宽从镜像站下载大量软件包 （例如系统升级）时出现偶发的 Connection reset by peer 错误 （详见 Debian bug #973581）。
目前，用户可以通过关闭 HTTP Pipelining 特性解决此问题。 如果需要关闭，可以在使用 apt 命令时加上 -o Acquire::http::Pipeline-Depth=0 参数， 或使用以下命令将相关设置加入 apt 系统配置中：

echo "Acquire::http::Pipeline-Depth \"0\";" > /etc/apt/apt.conf.d/99nopipelining

