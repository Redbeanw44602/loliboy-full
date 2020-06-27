#### **1.安装基础软件包**
```
apt update -y
apt install build-essential
apt install make
apt install software-properties-common
```
  

#### **2.导入PPA源**
 - 中途询问什么的，回车即可
```
add-apt-repository ppa:ubuntu-toolchain-r/test
```

#### TIPS：由于某个东西对PPA源**极不友好**，建议使用apt-fast安装 [**传送门**](https://www.loliboy.com/topic/9/%E6%96%B9%E6%95%99%E6%8E%88%E5%93%AD%E4%BA%86-%E4%B8%AD%E5%9B%BD%E9%9D%92%E5%B9%B4%E8%BF%99%E6%A0%B7%E5%8A%A0%E9%80%9Fppa%E6%BA%90%E4%B8%8B%E8%BD%BD)
  

#### **3.安装G++-9并设定默认g++**
```
apt-fast install g++-9
g++-9 -v
```
 - 若最后输出类似于下，说明安装成功
```
gcc version 9.2.1 20200110 (Debian 9.2.1-23)
```

 - 一般系统预装了G++X，使用命令更换
```
mv /usr/bin/g++ /usr/bin/g++-X.bak  #wtm服了群里的某些大佬了
mv /usr/bin/g++-9 /usr/bin/g++
```

 - BDL最新Makefile要求gcc版本≥9，顺便把gcc也整活
```
mv /usr/bin/gcc /usr/bin/gcc-X.bak #wtm服了群里的某些大佬了
mv /usr/bin/gcc-9 /usr/bin/gcc
```