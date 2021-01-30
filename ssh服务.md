## ubuntu12.04开启SSH服务 ##

1--确认sshserver是否启动

	ps -e | grep ssh

如果只有ssh-agent那ssh-server还没有启动，需要

	/etc/init.d/ssh start
如果看到sshd那说明ssh-server已经启动了


2.--安裝ssh-server服务

	sudo apt-get install openssh-server

ubuntu12.04安裝ssh-server(选择服务器）

	客户端：apt-get install openssh-client=1:5.9p1-5ubuntu1

	服务器：apt-get install openssh-server=1:5.9p1-5ubuntu1

3、ssh-server配置文件位于

	/ etc/ssh/sshd_config
在这里可以定义SSH的服务端口，默认端口是22，你可以自己定义成其他端口号，如222。然后重启SSH服务：

	sudo /etc/init.d/ssh resart