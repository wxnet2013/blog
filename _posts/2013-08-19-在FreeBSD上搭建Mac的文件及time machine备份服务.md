#在FreeBSD上搭建Mac的文件及time machine备份服务
上周将工作用电脑由公司配备的台式机切换到自己低配的macbook air上面，小本本的128G SSD远远不能满足工作的储存需要，但又不舍得入手昂贵的AirPort Time Capsule，于是考虑将空闲下来的pc主机作为Mac的文件及time machine的备份服务器。

服务器的操作系统当然要用我最爱的FreeBSD，她无论在稳定性、性能和易用性方面都要完胜已经是四分五裂的linux。需要在服务器上面安装netatalk及avahi。


netatalk是一个开源的afp文件服务器，可为Mac Os提供文件共享服务。

安装过程采用FreeBSD的ports编译方式。

##安装netatalk
cd /usr/ports/net/netatalk/ && make WITHOUT_X11=yes config install clean
文件服务器不需要工作在桌面环境下，所以要特别注意编译的时候排除掉X11.

编辑 /etc/rc.conf 以保证开机的时候能够启动文件服务。

netatalk_enable="YES"
afpd_enable="YES"
cnid_metad_enable="YES"

编辑netatalk的共享配置 /usr/local/etc/AppleVolumes.default
/home/share/apple "Time Machine" allow:kmd options:usedots,upriv,tm cnidscheme:dbd
Time Machine 是备份空间的名称
/home/share/apple 备份空间的路径
kmd 系统用户名

启动netatalk
/usr/local/etc/rc.d/netatalk start


到mac下的finder里按快捷键command+k 
afp://[服务器ip]
这个时候应该就可以正常的连接到文件服务器，进行正常的读写操作。但是要特别注意服务器目录的访问权限。



##安装avahi
为了让Mac Os在还原模式下（开机时按command＋R快捷键）能够搜索到netatalk，文件服务器还需要安装avahi服务，Avahi和苹果的Bonjour同为Zeroconf规范的开源实现。

以 ports 方式安装 avahi，配置里只需要选择 avahi-libdns
cd /usr/ports/net/avahi/ && make WITHOUT_X11=yes config install clean

在 /etc/rc.conf 添加:
avahi_daemon_enable="YES"


启动 avahi-daemon:
/usr/local/etc/rc.d/avahi-daemon start

##开始享受time machine吧
首次备份需要很长的时间，由机器性能及网络环境决定的，以后会定期自动进行增量备份。

##操作环境说明
FreeBSD9.1 
OS X Mountain Lion

##Next..
在pc上跑文件服务器还是比较费电的， 以后要尝试下树莓派＋FreeBSD的方式，目前树莓派的磁盘IO有瓶颈，可能会有性能问题等。

##参考
http://mikuru.tw/wordpress/archives/1980

TAG：FreeBSD、mac os、time machine、netatail、avahi

