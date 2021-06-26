https://blog.csdn.net/ren648154292/article/details/111151724
基本步骤
要在VSCode中配置C语言环境，我们首先可能要一个VSCode（废话），所以先下载安装一个VSCode；
然后肯定需要相关插件，因为VSCode不能直接拿来写C；
然后任何语言的程序在运行前都需要编译，那还需要一个编译器，很可惜VSCode插件里面不自带，所以要自己下载然后配置；
最后在VSCode中进行相关配置，就可以

下载并安装VSCode


安装相关插件

打卡后进入如下界面，选择这个C/C++的，然后点击install进行安装，大概几秒钟就好了，安装完成后install按钮会变成uninstall（卸载）：

安装编译器（MinGW-W64 GCC）

配置path

在cmd.exe中输入如下命令：
gcc -v -E -x c++ -

配置
最后在VSCode中进行相关配置：
先新建一个文件夹作为C语言项目文件，然后点击菜单栏中的File——>Open Folder，找到刚才新建的文件夹，然后点击选择文件夹打开这个项目文件。
然后在里面新建一个hello.c文件（名字随便起，以.c结尾就行了）
然后再建一个
.vscode文件夹（注意前面有个点），在里面建三个文件，c_cpp_properties.json、launch.json、tasks.json

c_cpp_properties.json：将这段代码复制进去
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceRoot}",
                "C:/Program Files/mingw64/include/**",
                "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include/c++",
                "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include/c++/x86_64-w64-mingw32",
                "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include/c++/backward",
                "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include",
                "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include-fixed",
                "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/../../../../x86_64-w64-mingw32/include"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "__GNUC__=6",
                "__cdecl=__attribute__((__cdecl__))"
            ],
            "intelliSenseMode": "msvc-x64",
            "browse": {
                "limitSymbolsToIncludedHeaders": true,
                "databaseFilename": "",
                "path": [
                    "${workspaceRoot}",
                    "C:/Program Files/mingw64/include/**",
                    "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include/c++",
                    "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include/c++/x86_64-w64-mingw32",
                    "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include/c++/backward",
                    "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include",
                    "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/include-fixed",
                    "C:/Program Files/mingw64/bin/../lib/gcc/x86_64-w64-mingw32/8.1.0/../../../../x86_64-w64-mingw32/include"
                ]
            }
        }
    ],
    "version": 4

}
然后，下方红框里的内容需要修改，将所有的 改为自己的安装路径，就是我们之前下载的编译器的地址：
把你的MinGW-W64 GCC解压后的文件中的mingw64的地址复制下来，替换代码里所有的 D:/Program Files (x86)/softwareFactory/x86_64-8.1.0-release-win32-sjlj-rt_v6-rev0/mingw64/ ：

launch.json：复制粘贴，然后miDebuggerPath属性里的内容也要改成自己的路径

{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(Windows) Launch",
            "type": "cppvsdbg",
            "request": "launch",
            "program": "cmd",
            "preLaunchTask": "echo",
            "args": [
                "/C",
                "${fileDirname}\\${fileBasenameNoExtension}.exe",
                "&",
                "echo.",
                "&",
                "pause"
            ],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole":true
        },
        {
            "name": "(gdb) Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/${fileBasenameNoExtension}.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": true,
            "MIMode": "gdb",
            "miDebuggerPath": "C:\\Program Files\\mingw64\\bin\\gdb.exe",// 自己电脑的gdb
            "preLaunchTask": "echo",//这里和task.json的label相对应
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
 
        }
    ]
}
tasks.json：复制粘贴
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "echo",
            "type": "shell",
            "command": "gcc",
            "args": [
                "-g", 
                "${file}", 
                "-o", 
                "${fileBasenameNoExtension}.exe",
                "-fexec-charset=GBK"//解决中文乱码
            ]
        }
    ],
    "presentation": {
        "echo": true,
        "reveal": "always",
        "focus": false,
        "panel": "shared", 
        "showReuseMessage": true,
        "clear": false
    }
}
然后就可以在之前建的hello.c文件里面写程序啦，比如我们熟悉的hello world：

#include<stdio.h>
main()
{
    printf("hello world\n");
   
    //system("pause");

————————————————
版权声明：本文为CSDN博主「SchizophreniA6」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/ren648154292/article/details/111151724