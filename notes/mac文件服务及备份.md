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

進階功能: 讓前述服務可被 Mac 還原模式搜尋到

雖然以上所提已可與 Mac OS X 合作無間，
但若碰到要做系統還原的時候，還必須搭配 avahi 將服務廣播出去。

##安装avahi
首先以 ports 安裝 avahi，此處只需選擇 avahi-libdns
cd /usr/ports/net/avahi/ && make WITHOUT_X11=yes config install clean

於 /etc/rc.conf 加入:
avahi_daemon_enable="YES"


启动 avahi-daemon:
/usr/local/etc/rc.d/avahi-daemon start

##环境说明
FreeBSD9.1 
OS X Mountain Lion

##参考
http://mikuru.tw/wordpress/archives/1980

