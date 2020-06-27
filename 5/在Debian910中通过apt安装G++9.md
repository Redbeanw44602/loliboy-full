##### **1.安装基础软件包**
```
apt update -y #更新源
apt install build-essential
apt install make
apt install software-properties-common
```

##### **2.添加官方源(Debian有官方g++源!)**
```
vim /etc/apt/sources.list  #编辑源列表
```
 - 新建一行，添加 **远离某科大,某科大速度就是百度网盘**

```
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ sid main contrib non-free
```
 - 保存后刷新源

```
apt update
```

##### **3.安装并切换默认G++版本**
 - 直接安装就行了

```
apt install g++-9
g++-9 -v
```
 - 若最后输出类似于下，说明安装成功
```
gcc version 9.2.1 20200110 (Debian 9.2.1-23)
```

 - 一般系统预装了G++Older，使用命令更换
```
mv /usr/bin/g++ /usr/bin/g++-X.bak #我佛了群里某些大佬了
mv /usr/bin/g++-9 /usr/bin/g++
```

 - BDLauncher最新Makefile要求gcc版本≥9，顺便把gcc也整活
```
mv /usr/bin/gcc /usr/bin/gcc-X.bak #我佛了群里某些大佬了
mv /usr/bin/gcc-9 /usr/bin/gcc
```