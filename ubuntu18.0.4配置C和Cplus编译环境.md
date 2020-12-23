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
# 在ubuntu中编译C++代码的两种方法 #



