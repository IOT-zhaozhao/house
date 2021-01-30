

	unsigned char = uint8_t ＝u8
	unsigned short int = uint16_t ＝u16
	unsigned long int =uint32_t ＝u32


stdint.h 这里放着C语言的标准表达方式
 
typedef   signed        char      int8_t; 
typedef   signed short  int       int16_t;
typedef   signed        int       int32_t;
typedef   signed      __int64     int64_t;
 
typedef unsigned           char       uint8_t;
typedef unsigned short     int        uint16_t;
typedef unsigned           int        uint32_t;
typedef unsigned         __int64      uint64_t;


本文主要介绍c语言中条件编译相关的预编译指令，包括  
·#define、#undef、#ifdef、#ifndef、#if、#elif、#else、#endif、defined。

·#define           定义一个预处理宏

·#undef            取消宏的定义

·#if               编译预处理中的条件命令，相当于c语法中的if语句

·#ifdef            判断某个宏是否被定义，若已定义，执行随后的语句

·#ifndef           与#ifdef相反，判断某个宏是否未被定义

·#elif             若#if, #ifdef, #ifndef或前面的#elif条件不满足，则执行#elif之后的语句，相当于c语法中的else-if

·#else             与#if, #ifdef, #ifndef对应, 若这些条件不满足，则执行#else之后的语句，相当于c语法中的else

·#endif          #if, #ifdef, #ifndef这些条件命令的结束标志.

·defined         与#if, #elif配合使用，判断某个宏是否被定义

%d 　　有符号10进制整数（%ld 长整型，%hd短整型 ）

%hu 　 无符号短整形（%u无符号整形，%lu无符号长整形）

%i 　　 有符号10进制整数 （%i 和%d 没有区别，%i 是老式写法，都是整型格式）

%o 　　无符号8进制整数

%u 　　无符号10进制整数

%x 　　无符号的16进制数字，并以小写abcdef表示

%X 　 无符号的16进制数字，并以大写ABCDEF表示

%f　　 输入输出为浮点型 （%lf双精度浮点型）

%E/e 用科学表示格式的浮点数

%c 输入输出为单个字符

%s 输入输出为字符串

简介：
&&是逻辑与运算符，||是逻辑或运算符，都是逻辑运算符，两边只能是bool类型
&与| 既可以进行逻辑运算，又可以进行位运算，两边既可以是bool类型，又可以是数值类型

区别：
if (A && B) 如果 A 为 false ，整个表达式就为 false，不再计算 B 的值了。
if (A & B) 如果 A 为 false ，整个表达式就为 false，但还要计算 B 的值。
if (A && B++) 如果A 为 false，&&不会再计算后面的值
if (A & B++) 如果A 为 false，&则会计算后面的值

	square  平方
	sqrt	开根号
	使用时需要添加头文件：#include "math.h"