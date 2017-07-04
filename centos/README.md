1. 安装配置依赖项

如想使用Postfix来发送邮件,在安装期间请选择'Internet Site'. 您也可以用sendmai或者 配置SMTP服务 并 使用SMTP发送邮件.

在 Centos 6.8 系统上, 下面的命令将在系统防火墙里面开放HTTP和SSH端口.

sudo yum install curl openssh-server openssh-clients postfix cronie

sudo service postfix start

sudo chkconfig postfix on

sudo lokkit -s http -s ssh

2. 添加GitLab仓库,并安装到服务器上

curl -sS http://packages.gitlab.cc/install/gitlab-ce/script.rpm.sh | sudo bash

sudo yum install gitlab-ce

3. 启动GitLab

sudo gitlab-ctl reconfigure


4. 使用浏览器访问GitLab

首次访问GitLab,系统会让你重新设置管理员的密码,设置成功后会返回登录界面.

默认的管理员账号是root,如果你想更改默认管理员账号,请输入上面设置的新密码登录系统后修改帐号名.

![image](https://github.com/greatsharp/docker-gitlab/blob/master/centos/gitlab_first_login.png)


5. 配置external url 配置GitLab显示的远程仓库的git@...和http(s)//...中的域名

为使用户可以正确的获取到GitLab上显示的当前仓库的clone地址， GitLab需要你设置好哪个url才是用户可以访问到GitLab

修改文件/etc/gitlab/gitlab.rb

external_url "http://git.rapheal.sdc" #替换为你自己的地址

运行 sudo gitlab-ctl reconfigure 使修改生效。
![image](https://github.com/greatsharp/docker-gitlab/blob/master/centos/gitlab-external_url.png)
