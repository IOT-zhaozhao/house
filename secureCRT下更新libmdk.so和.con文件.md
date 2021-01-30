# secureCRT控制台替换终端.so文件操作步骤 #

备注：.con文件操作类似，不过.con文件相当于一个压缩包，复制到相关路劲下面，**upgrader**命令解压即可

1.先使用kill命令杀死一些进程，使log信息停止滚动
	
	killall ywupdate
	killall mdk_core
	feeder&
2.要修改init.d下的rcS文件信息，需要先增加权限

	mount -o rw,remount /
	mount -o rw,remount /appset/
	chmod 777 /etc/init.d/rcS
	ls -l /etc/init.d //查看权限有没有修改成功
3.注释掉rcS文件里面的/bin/protector
	
	vi /etc/init.d/rcS
	在 /bin/protector 前面加 #
4.使用ls命令查看usb里面保存的.so文件

	ls /mnt/usb/
5.复制.so文件到 /appset/lib/路径下，覆盖原来的文件

	cp /mnt/usb/libmdk_app.so /appset/lib

.con文件路径则是 /tmp/upgrade

	cp /mnt/usb/appset.con /tmp/upgrade
6.reboot或者关开电源重启终端

7.对于K5T的相关升级文件，比如k5t…….cla之类的文件，直接改成libmdk_app.so文件然后进行1到6的替换操作就可以了。

8.通过tftp传输文件（先进行前面1~3的操作）

	ifconfig eth0 192.168.3.182 netmask 255.255.255.0
9.进入appset/lib路径下面

	cd /appset/lib
10.Tftpd64工具配置相关IP和端口和**选择文件**

	192.168.3.79  //服务器ip
	192.168.3.182 //tftp客户端IP，端口默认：69
11.在/appset/lib路径下获取文件

	tftp -g -r libmdk_app.so 192.168.3.79//文件路径与tftp程序路径一致
12.Tftpd64工具点击发送（put),然后查看日志（log viewer)是否发送成功，或者观察CRT日志是否报错。
	
c)	远程升级 

K5P：*#43*公网IP*路由器开启外网映射端口#

	例如：*#43*183*56*143*88*51124#
K5T：*#380*文件名.yet*ip*端口*用户名*密码#

	380*APPSET_20201113_00.yet*106.15.46.184*21*shengji*shengji_317#


