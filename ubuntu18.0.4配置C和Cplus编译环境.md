# ubuntu下搭建C/C++编译环境 #

## 1. 环境准备 ##

首先需要安装ｇcc和ｇ++环境

安装之前查看是否有安装,使用命令:

	gcc --version
	g++ --version

没有安装就使用apt-get命令安装

	apt-get install gcc
	apt-get install g++

## 2.编写程序 ##

## C语言 ##

1.建立一个文件夹
	
	mkdir learnC
2.进入文件夹，建立一个C语言程序
	
	cd /learnC
	touch hello.c
3.进入编程界面，编写程序代码
	
	vim hello.c
4.输入 i 进入编辑模式，输入代码
	
	include<stdio.h>
	
	int main()
	{
		printf("Hello World！\n");
		return 0;
	}
5.按ESC退出编辑模式，shift + ： ，然后输入 wq 保存退出。

6.生成可执行的代码文件
	
	gcc hello.c -o hello
7.执行生成的可执行文件
	
	./hello
8.输出执行结果
	
	Hello World!

## C++ ##

1.建立一个文件夹
	
	mkdir Cplus
2.进入文件夹，建立一个C语言程序
	
	cd /Cplus
	touch hello.cpp
3.进入编程界面，编写程序代码
	
	vim hello.cpp
4.输入 i 进入编辑模式，输入代码
	
	include<iostream>
	
	using namespace std;
	int main()
	{
		cout<<"Hello World！\n"<<endl;
		return 0;
	}
5.按ESC退出编辑模式，shift + ： ，然后输入 wq 保存退出。

6.生成可执行的代码文件(注意，是 **g++** 而不是 **gcc** )
	
	g++ hello.cpp -o hello
7.执行生成的可执行文件
	
	./hello
8.输出执行结果
	
	Hello World!
# 在ubuntu中使用cmake编译C++代码 #

先安装cmake，不会安装的参考我的 《ubuntu18.0.4安装cmake》

使用cmake首先得有个CMakeLists.txt文件，你需要把配置信息写在该文件中，然后通过cmake去处理该文件。


	touch CMakeList.txt
	touch helloworld.cpp

在CMakeLists.txt中配置以下信息；

	cmake_minimum_required(VERSION 2.8)
	#工程名
	project(HELLOWORLD)
	#包含原程序,即把给定目录下的源程序复制给变量DIR_SRC
	#将指定路径下的源文件储存在指定的变量中
	#下面这句话，有些博客中写错了，需要注意
	aux_source_directory(./ DIR_SRC )
	#生成程序
	add_executable(HELLOWORLD  ${DIR_SRC})

在helloworld.cpp中输入以下信息：
	
	#include<iostream>
	int main()
	{
    	std::cout<<"hello world!"<<std::endl;
    	return 0;
	}	

然后在终端中输入：


	//按照顺序依次输入下面的命令
	// mkdir 做一个工作空间，名称是build
	// cd 进入build的目录 
	//HELLOWORLD 是文件中的工程名称
	//以上仅仅是注释
 
	mkdir build 
	cd build
	cmake ..
	make
	./HELLOWORD  //区分大小写，CMakeLists.txt定义是大写就得用大写

输出结果如下：

	hello world!