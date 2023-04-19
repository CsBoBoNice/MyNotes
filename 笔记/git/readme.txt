



安装
sudo apt install git

配置git
git config --global user.name "CsBoBoNice"
git config --global user.email "751541594@qq.com"

#查看配置
git config --list


生成密钥
ssh-keygen -t rsa -C "751541594@qq.com"
cat ./.ssh/id_rsa.pub 
或
cat /c/Users/75154/.ssh/id_rsa.pub


测试是否设置成功
ssh -T git@github.com

打印如下则配置成功
Hi CsBoBoNice! You've successfully authenticated, but GitHub does not provide shell access.




#查看系统的config
git config --system --list

#查看当前用户（global）配置
git config --global --list
