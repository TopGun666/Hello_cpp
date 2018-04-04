## Ubuntu apt-get用法

&emsp;&emsp;如何在ubuntu下面直接查找想要安装的软件？
&emsp;&emsp;比如我想安装tomcat，但是我又不知道ubuntu里面有哪些版本，也不知道都需要装什么，但是我能确认我装的是tomcat，那么我就可以用搜索命令：例如：apt-cache search tomcat，这样我就会得到以下的结果：
libtomcat5-java - Java Servlet engine -- core libraries
tomcat5 - Java Servlet 2.4 engine with JSP 2.0 support
tomcat5-admin - Java Servlet engine -- admin web interfaces
tomcat5-webapps - Java Servlet engine -- documentation and example web applications
这样我就知道，ubuntu的软件库里面有tomcat5，那么我就可以用apt-get install tomcat5去安装了。

**1) apt-get upgrade and apt-get dist-upgrade**
使用 apt-get upgrade 和 apt-get dist-upgrade 的结果，基本上是一样的，不过apt-get dist-upgrade 在升级的同时会为了解决依赖性而安装新套件，而 apt-get upgrade 并不会，因此要升级的话，建议还是用 apt-get dist-upgrade 较佳。


**2) apt-cache search**
搜寻：我们可以用这个指令来搜寻升级包，
例如：apt-cache search httpd，
apt-cache depends
相依性：我们可以用这个指令来看到软件包的所有相依性档案
例如：apt-cache depends httpd，

**3) apt-get install**
安装：安装软件包，
例如：apt-get install httpd，这样 apt 就会自动上网下载httpd 回来安装，若httpd 有相依性套件的时候，apt 也会自动下载安装,在Ubuntu16.04之后，可以用apt install 直接自动下载安装，并且还会在Terminal底部显示安装进度。

**4)apt-get clean**
清除：当使用 apt-get install 指令安装套件，下载下来的 rpm 会放置於 /var/cache/apt/archives，使用 apt-get clean 指令可以将之清除，避免占用硬碟空间

**5）apt-get remove**
移除：例如：apt-get remove httpd，就会移除 httpd 了，假如有相依性套件的时候，apt 也会一并移除
以上这几个指令应该就够用了，若想要得到更进一步的指令，请善用 man

**6）apt-get update**
更新：这指令是用来取得记录在 /etc/apt/sources.list 内的远端服务器的套件档案清单 在使用 「apt-get dist-upgrade」指令升级套件前，一定要记得先用这条指令将套件档案清单更新

**7）apt-get dist-upgrade**
升级：这里的升级主要是根据已有的软件包更新而言，并不是更新整个系统，也可以使用图形界面的新立得包管理器：）

如果没有安装这个管理器的话，可以执行以下指令
apt-get install synaptic
安装完毕后，直接在命令行上敲入synaptic就可以启动了。

ubuntu下apt-get命令参数

**常用的APT命令参数**
apt-cache search package 搜索包
apt-cache show package 获取包的相关信息，如说明、大小、版本等
apt-cache depends package 了解使用依赖
apt-cache rdepends package 查看该包被哪些包依赖
sudo apt-get install package 安装包
sudo apt-get install package --reinstall 重新安装包
sudo apt-get -f install 修复安装"-f = --fix-missing"
sudo apt-get remove package 删除包
sudo apt-get remove package --purge 删除包，包括删除配置文件等
sudo apt-get update 更新源
sudo apt-get upgrade 更新已安装的包
sudo apt-get dist-upgrade 升级系统
sudo apt-get dselect-upgrade 使用 dselect 升级
sudo apt-get build-dep package 安装相关的编译环境
apt-get source package 下载该包的源代码
sudo apt-get clean && sudo apt-get autoclean 清理无用的包
sudo apt-get check 检查是否有损坏的依赖

其中：
1 有sudo的表示需要管理员特权！
2 在Ubuntu中命令后面参数为短参数是用“-”引出，长参数用“--”引出
3 命令帮助信息可用man 命令的方式查看或者
命令 -H（--help）方式查看
4 在MAN命令中需要退出命令帮助请按“q”键！！
选项 含义 作用
sudo -h Help 列出使用方法，退出。
sudo -V Version 显示版本信息，并退出。
sudo -l List 列出当前用户可以执行的命令。只有在sudoers里的用户才能使用该选项。
sudo -u username|#uid User 以指定用户的身份执行命令。后面的用户是除root以外的，可以是用户名，也可以是#uid。
sudo -k Kill 清除“入场卷”上的时间，下次再使用sudo时要再输入密码。
sudo -K Sure kill 与-k类似，但是它还要撕毁“入场卷”，也就是删除时间戳文件。
sudo -b command Background 在后台执行指定的命令。
sudo -p prompt command Prompt 可以更改询问密码的提示语，其中%u会代换为使用者帐号名称，%h会显示主机名称。非常人性化的设计。
sudo -e file Edit 不是执行命令，而是修改文件，相当于命令sudoedit

