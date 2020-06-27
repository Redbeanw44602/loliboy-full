#### **0.本文用到的工具**
 - **本教程不适用Ubuntu19以下的版本！请不要再费力尝试了！**
 - **请先升级到Ubuntu19!!!!**
 - ~~不需要X11类软件~~

#### **1.安装基础软件包**
```
apt update -y
apt install git wget vim unzip p7zip-full -y
```

#### **2.安装FAudio**
> 建议进行一切操作前看[这篇文章](https://www.loliboy.com/topic/9/%E6%96%B9%E6%95%99%E6%8E%88%E5%93%AD%E4%BA%86-%E4%B8%AD%E5%9B%BD%E9%9D%92%E5%B9%B4%E8%BF%99%E6%A0%B7%E5%8A%A0%E9%80%9Fppa%E6%BA%90%E4%B8%8B%E8%BD%BD)，以防引发焦虑症
 - Wine5新依赖FAudio，官方Ubuntu包库中并无这个软件。使用(中途询问回车即可)
```
add-apt-repository ppa:cybermax-dexter/sdl2-backport
```
 - 安装该依赖
```
#apt-fast安装，如果你对你的网速飞常自信就用apt-get(以下所有步骤同理)
apt-fast install libfaudio0
```
#### **3.安装Wine**
 - 下载并导入密钥
```
wget -nc https://dl.winehq.org/wine-builds/winehq.key
apt-key add winehq.key
```
 - 添加官方源
```
# Ubuntu 19.x
apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ eoan main'
apt update
```
 - 这样就可以安装辣
```
#大概要下载200M的东西，强烈建议使用apt-fast（不要对你的网速太自信了）
apt-fast install --install-recommends winehq-devel
```
 - 一切Ojbk，看看装成了没有？
```
wine64 --version
wine --version
```
 - 若输出均为
```
wine-5.2
```
 - 则成功，（如果小于5.2也不行）

#### **4.开服前的准备**
 - 下载wine-bdlauncher
```
mkdir wtfbdlwine
cd wtfbdlwine
wget https://github.com/codehz/wine-bdlauncher/releases/latest/download/pkg.tar.xz
xz -d pkg.tar.xz
tar -xvf pkg.tar
mv Dist/* .
rm -rf Dist
```
![1.png](/assets/uploads/files/1582106213780-1.png) 
 - 下载服务端 [**官方网站**](https://www.minecraft.net/en-us/download/server/bedrock/)
 - 注意要下载Windows版服务端，这里直接wget
```
wget https://minecraft.azureedge.net/bin-win/bedrock-server-1.14.30.2.zip
unzip bedrock-server-1.14.30.2.zip #和仓库在同一目录
rm -rf bedrock-server-1.14.30.2.zip
```
 - 安装运行库 **（CodeHz提取）**
```
wget https://ipfs.hertz.services/ipfs/QmYDqnHa7VeB9dqFczaR2K3Sj9qAr5JWNnYGtSg7WsR9r6/dlls.7z
7z x dlls.7z
rm -rf dlls.7z
```
#### **5.设定系统环境变量**
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
#### **6.开服**
```
wine bedrock_server_mod.exe
```