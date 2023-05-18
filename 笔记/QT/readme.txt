http://download.qt.io/



// 最新的都是在线安装,选择在线安装包
archive/online_installers/

https://download.qt.io/official_releases/online_installers/

qt-unified-windows-x64-4.5.2-online.exe --mirror https://mirrors.aliyun.com/qt
qt-unified-windows-x64-4.5.2-online.exe --mirror https://mirrors.tuna.tsinghua.edu.cn/qt/

qt-unified-windows-x64-4.5.1-online.exe

qt-unified-windows-x64-4.5.2-online.exe --mirror https://mirrors.aliyun.com/qt
qt-unified-windows-x64-4.5.2-online.exe --mirror https://mirrors.tuna.tsinghua.edu.cn/qt


// 更新组件
./MaintenanceTool.exe --mirror https://mirrors.tuna.tsinghua.edu.cn/qt

./MaintenanceTool.exe --mirror https://mirrors.aliyun.com/qt


安装组件中
勾选msvc2019 64-bit
勾选Qt Creator
勾选MinGW

ubantu安装

sudo apt install libgl1 libx11-xcb1 libx11-6 libxext6  libxfixes3 libxi6 libxrandr2 libxrender1 libxcb1
sudo apt install libxcb-xinerama0
sudo apt install mesa-common-dev

chmod +x qt-unified-linux-x64-4.5.2-online.run

./qt-unified-linux-x64-4.5.2-online.run --mirror https://mirrors.tuna.tsinghua.edu.cn/qt



交叉编译
下载源码
https://download.qt.io/archive/qt/6.2/6.2.4/







