ctrl+shift+p 打开搜索，搜索C++打开配置json
或
F1 打开搜索，搜索C++打开配置json




搜索所有生成路径
g++ -v -E -x c++ -

将此路径添加到"includePath": 下

arm用

{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**",
                "/usr/lib/gcc-cross/aarch64-linux-gnu/9/../../../../aarch64-linux-gnu/include/c++/9",
                "/usr/lib/gcc-cross/aarch64-linux-gnu/9/../../../../aarch64-linux-gnu/include/c++/9/aarch64-linux-gnu",
                "/usr/lib/gcc-cross/aarch64-linux-gnu/9/../../../../aarch64-linux-gnu/include/c++/9/backward",
                "/usr/lib/gcc-cross/aarch64-linux-gnu/9/include",
                "/usr/lib/gcc-cross/aarch64-linux-gnu/9/../../../../aarch64-linux-gnu/include",
                "/usr/include"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/aarch64-linux-gnu-gcc-9",
            "cStandard": "c17",
            "cppStandard": "c++17",
            "intelliSenseMode": "linux-gcc-arm64"
        }
    ],
    "version": 4
}


x86用
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**",
                "/usr/include/c++/9",
                "/usr/include/x86_64-linux-gnu/c++/9",
                "/usr/include/c++/9/backward",
                "/usr/lib/gcc/x86_64-linux-gnu/9/include",
                "/usr/local/include",
                "/usr/include/x86_64-linux-gnu",
                "/usr/include"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/gcc",
            "cStandard": "c17",
            "cppStandard": "c++17",
            "intelliSenseMode": "linux-gcc-x64"
        }
    ],
    "version": 4
}





