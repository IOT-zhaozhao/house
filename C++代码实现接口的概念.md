# C++代码实现接口的概念 #

接口：不能实例化的东西，只需把构造函数私有化即可！

文件：PrintMainViewProxy.h
内部代码：

	#ifndef __PRINTMAINVIEWPROXY_H__
	#define __PRINTMAINVIEWPROXY_H__
 
	class PrintMainViewProxy{
 
		public:
			static char *getHelloWorld();
			static char *getHowAreYou();
 
 
		private:
			PrintMainViewProxy();
 
	};
 
 
	#endif	//__PRINTMAINVIEWPROXY_H__

文件：PrintMainViewProxy.cpp
内部代码：

	#include "PrintMainViewProxy.h"
 
	char * PrintMainViewProxy::getHelloWorld()
	{
		return "Hello World";
	}
 
	char * PrintMainViewProxy::getHowAreYou()
	{
		return "How Are You";
	}
 
	PrintMainViewProxy::PrintMainViewProxy()
	{
 
	}

文件：main.cpp
内部代码：

	#include <iostream>
	#include "PrintMainViewProxy.h"
	using namespace std;
 
	void main(){ 
 
		char *helloWorld = PrintMainViewProxy::getHelloWorld();
		char *howAreYou = PrintMainViewProxy::getHowAreYou();
		cout << helloWorld << endl;
		cout << howAreYou << endl;
 
		getchar();
	}

生成的程序运行结果：

	Hello World
	How Are You

如果实例化就会报错！