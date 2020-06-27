#### **0.准备**
 - 安装基础软件包
```
apt update -y
apt install gcc g++ make flex bison xserver-xorg-dev unzip p7zip-full vim #必须
apt install xterm xorg #不用X11可以不安装
```
 - ~~不需要X11类软件~~
#### **1.安装FAudio**
 - 下载软件包
```
wget https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Debian_10/amd64/libfaudio0_20.01-0~buster_amd64.deb
```
 - 安装
```
dpkg -i libfaudio0_20.01-0~buster_amd64.deb
```

![1.png](/assets/uploads/files/1582953993880-1.png) 
 - 一定出现依赖问题，用以下命令解决
```
apt-get -f install
```
 - 完成后再次安装
```
dpkg -i libfaudio0_20.01-0~buster_amd64.deb
```
![1.png](/assets/uploads/files/1582954075829-1.png) 
 
#### **2.编译安装Wine**
 - 下载源码
```
wget https://dl.winehq.org/wine/source/5.x/wine-5.5.tar.xz
```
 - 解压，进入目录
```
xz -d wine-5.5.tar.xz
tar -xvf wine-5.5.tar
cd wine-5.5
```
 - 编译
```
./configure --enable-win64 --without-freetype
```
 - 一般会出现一堆WARNING，反正用不到不用管它
```
configure: WARNING: gettext tools not found (or too old), translations won't be built.
configure: WARNING: libxrender 64-bit development files not found, XRender won't be supported.
configure: WARNING: No OpenGL library found on this system.
OpenGL and Direct3D won't be supported.
configure: WARNING: libxml2 64-bit development files not found (or too old), XML won't be supported.
configure: WARNING: libxslt 64-bit development files not found, xslt won't be supported.
configure: WARNING: libgnutls 64-bit development files not found, no schannel support.
configure: WARNING: libjpeg 64-bit development files not found, JPEG won't be supported.
```
 - 直接make 、、一个小时
```
make #tips:可以使用make -jX 进行多核编译，前提是你有多核心(X为核心数)
```
 - 完成后，如果最后一行类似如下，说明成功
```
Wine build complete.
```
 - 然后就很快了
```
make install
```
 - 检查是否成功
```
wine64 --version
输出：wine-5.5
```

#### **3.开服前**
> 奥利给！你已经成功一半了！
 - 下载&安装BDS **参考:**[国内镜像](https://www.loliboy.com/topic/23)
 - 注意要下载Windows版的端！
```
cd .. #退出wine安装目录
mkdir mc  && cd mc #名称随意
wget https://minecraft.azureedge.net/bin-win/bedrock-server-1.14.30.2.zip
unzip bedrock-server-1.14.30.2.zip
rm -rf bedrock-server-1.14.30.2.zip
```
 - 安装运行库 **（CodeHz提取）**
```
wget https://ipfs.hertz.services/ipfs/QmYDqnHa7VeB9dqFczaR2K3Sj9qAr5JWNnYGtSg7WsR9r6/dlls.7z
7z x dlls.7z
rm -rf dlls.7z
```
 - 安装Wine-Bdlauncher **参考:**[国内镜像](https://www.loliboy.com/topic/23)
```
wget https://github.com/codehz/ElementZero/releases/download/[XXX]/pkg.tar.xz #自行更换为最新版本
xz -d pkg.tar.xz
tar -xvf pkg.tar
mv Dist/* .
rm -rf Dist
rm -rf pkg.tar
```
#### **4.设定系统环境变量**
 - 据说这种方法可以省进程
 - 编辑
```
vim /etc/profile
```
 - 在图示位置添加以下两行（按a编辑）

![1.png](/assets/uploads/files/1583029371043-1.png) 
```
export WINEDLLOVERRIDES="vcruntime140_1,vcruntime140=n;mscoree,mshtml,explorer.exe,winemenubuilder.exe,services.exe,playplug.exe=d"  #必须
export WINEDEBUG=-all  #非必须，添加后可以避免输出太多调试信息
```
 - 按Esc后输入`:wq`保存
 - 刷新
```
source /etc/profile
```
 - 使用`env`列出所有环境变量
 - 找下输出有没有这两行，如果有说明成功

![12.png](/assets/uploads/files/1583029508839-12.png) 
#### **5.开服**
```
wine64 bedrock_server_mod.exe
```