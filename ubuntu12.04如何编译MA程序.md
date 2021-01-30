# 如何编译MA程序 #

1、安装公司给的ubuntu12.04版本的虚拟机

2、虚拟机桥接模式连上本地网络，公司的安全管理系统在虚拟机上面启动运行

3、安装同步加密工具Beyond Compare

4、查看虚拟机里面有无如下路径，没有就自己创建一下
	
	/home/yw332/Public/MPU/ywgpskit

5、Beyond Compare新建同步会话：

	左边选择本地svn下载项目的文件夹路径
	右边\\【虚拟机IP】\MPU\ywgpskit 

6、Beyond Compare选择会话设置→名字过滤器添加下面的内容
	
	.svn
	mappboot
	.vs
	Temp
	Bin
	pzh
7添加执行权限

	sudo su

8、编译路径
	
	/home/yw332/Public/MPU/ywgpskit/Compile

9、编译命令（k5、k7为例）

	make -f mkf_mpu_k5.mk		//编译k5程序
	make -f mkf_mpu_k7i.mk		//编译k7程序
10、编译失败的话，查看mkf_mpu_xx.mk文件（makefile)里面的编译环境是否配置正确，不正确的话得重新配置

	vim /etc/envirmont   //配置编译path
	source /etc/envirmont  //执行修改后得配置
