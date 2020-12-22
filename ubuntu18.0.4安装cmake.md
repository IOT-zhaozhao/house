# ubuntu18.0.4安装Cmake #
1.本地安装
先检查有没有安装好**gcc**和**g++**,装好之后将下载好的tar.gz压缩包放到opt的路径下

	tar xzvf cmake-3.19.2.tar.gz
	cd camke-3.19.2/
没装好gcc和g++的

	apt-get install gcc
	apt-get install g++

切换到camke-3.19.2/路径下,运行

	./bootstrap

问题1：
C compiler on this system is: gcc
C++ compiler on this system is: g++
---------------------------------------------
Error when bootstrapping CMake:
Cannot find appropriate Makefile processor on this system.
Please specify one using environment variable MAKE.


提示could not find OpenSSL，此处解决办法：
	
	sudo apt-get install openssl
	sudo apt-get install libssl-dev

问题2：

g++ : 依赖: g++-4.8 (>= 4.8.2-5~) 但是它将不会被安装

E: 无法修正错误，因为您要求某些软件包保持现状，就是它们破坏了软件包间的依赖关系。

解决办法：

   就是使用aptitude包依赖管理工具来帮我们解决，具体方法如下：

    sudo apt-get install aptitude

    sudo aptitude install g++

问题3：
	
Could NOT find OpenSSL, try to set the path to OpenSSL root folder in the system variable OPENSSL_

安装openssl和编译依赖
	sudo aptitude install  openssl
	sudo aptitude install libssl-dev

最后，运行编译：

    ./bootstrap
    make
    make install