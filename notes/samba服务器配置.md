安装samba36
cd /usr/ports/net/samba36/ && make WITHOUT_X11=yes config install clean

修改配置
vi /usr/local/etc/smb.conf
workgroup = WORKGROUP

[ria]
  comment = ria's Service
  path = /usr/riafiles
  valid users = lidan
  public = no
  writable = yes
  printable = no

新建系统帐号及samba帐户
addusr username
smbpasswd -a username

启动samba
/usr/local/etc/rc.d/samba start
 
参考
http://www.freebsd.org/doc/zh_CN/books/handbook/network-samba.html
http://www.douban.com/note/10997329/


通过组的方式管理共享服务器。
1、创建用户组，并添加用户。
2、将每个用户添加到samba 
smbpasswd -a username
3、修改配置文件,并保证用户添加得目录都具有写权限。
path = /usr/samba/riashare
read only = no
public    = no
create mode = 0770
directory mode = 0770
vaild users = @ria
write list = @ria

  