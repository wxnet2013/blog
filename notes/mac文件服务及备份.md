#mac文件服务及time machine备份
##安装netatalk
cd /usr/ports/net/netatalk/ && make WITHOUT_X11=yes config install clean

编辑 /etc/rc.conf
netatalk_enable="YES"
afpd_enable="YES"
cnid_metad_enable="YES"

编辑 /usr/local/etc/AppleVolumes.default
/home/share/apple "Time Machine" allow:kmd options:usedots,upriv,tm cnidscheme:dbd
Time Machine 是备份空间的名称
/home/share/apple 备份空间的路径
kmd 系统用户名

启动netatalk
/usr/local/etc/rc.d/netatalk start

再finder里cmd+k 
afp://10.58.101.124
这个时候应该就可以链接到服务器了。

特别要注意服务器目录的访问权限。

進階功能: 讓前述服務可被 Mac 還原模式搜尋到

雖然以上所提已可與 Mac OS X 合作無間，
但若碰到要做系統還原的時候，還必須搭配 avahi 將服務廣播出去。

##安装avahi
以 ports 安装 avahi，配置里只需要选择 avahi-libdns
cd /usr/ports/net/avahi/ && make WITHOUT_X11=yes config install clean

在 /etc/rc.conf 添加:
avahi_daemon_enable="YES"


启动 avahi-daemon:
/usr/local/etc/rc.d/avahi-daemon start

##环境说明
FreeBSD9.1 
OS X Mountain Lion

##TODO
在pc上跑文件服务器比较费电，是否可以 树莓派＋linux，以及性能问题等。
##参考
http://mikuru.tw/wordpress/archives/1980

