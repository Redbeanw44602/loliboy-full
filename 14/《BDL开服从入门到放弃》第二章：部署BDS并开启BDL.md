> **目录**
> —[【第一章】选择服务器与系统](https://www.loliboy.com/topic/13/bdl%E5%BC%80%E6%9C%8D%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E6%94%BE%E5%BC%83-%E7%AC%AC%E4%B8%80%E7%AB%A0-%E9%80%89%E6%8B%A9%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8E%E7%B3%BB%E7%BB%9F) 
> —[【第二章】部署BDS并开启BDL](https://www.loliboy.com/topic/14/bdl%E5%BC%80%E6%9C%8D%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E6%94%BE%E5%BC%83-%E7%AC%AC%E4%BA%8C%E7%AB%A0-%E9%83%A8%E7%BD%B2bds%E5%B9%B6%E5%BC%80%E5%90%AFbdl) *
> —[【第三章】其他的文档](https://www.loliboy.com/topic/16/bdl%E5%BC%80%E6%9C%8D%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E6%94%BE%E5%BC%83-%E7%AC%AC%E4%B8%89%E7%AB%A0-%E5%85%B6%E4%BB%96%E7%9A%84%E6%96%87%E6%A1%A3) (完)

#### **1.升级Debian10**
 - 本人选的是Debian9，因为TX云无10镜像。推荐升级到10后再开服。**可以免去libssl/libcurl烦恼**（稍后我会写不升级的错误处理方法）
 - 推荐Debian社区的这篇文 [传送门](https://www.debian.cn/archives/3136)
 - 大略方法可以在上述链接中看到，中途的问题我还是说一下吧

#### **2.一些注意事项**
  > **提醒Linux白痴** "#"在Bash中是**注释**的意思，喜欢复制粘贴的先生们一定要注意！

 - 出现如下图这样选 **（以后出现类似图都这样选）**

![2.png](/assets/uploads/files/1581846030443-2.png) 
 - 出现这个直接按q

![3.png](/assets/uploads/files/1581846317070-3.png) 
 - 出现这个，No

![4.png](/assets/uploads/files/1581846368384-4.png) 
 - 出现这个，Ok

![5.png](/assets/uploads/files/1581846428637-5.png) 
 - 最后要检查一下是不是升级到10了？如果输出不类似下面，可以留言回复问题~

![6.png](/assets/uploads/files/1581846845945-6.png) 
 - 有些升级会提示类似这样的东西

![1.png](/assets/uploads/files/1583026295821-1.png) 
 - 记得一定选**Y**

#### 3.安装BDS
 - 基本的工具先装下
```
apt update -y
apt install unzip vim -y
```
 - 可以在Mjjang官网下载后上传，也可以直接wget [传送门](https://www.minecraft.net/zh-hans/download/server/bedrock/)
 - 我这里直接wget **参考:**[国内镜像](https://www.loliboy.com/topic/23)
```
mkdir mc #创建文件夹放服务端，名称随意
cd mc
wget https://minecraft.azureedge.net/bin-linux/bedrock-server-1.14.30.2.zip #请自行检查最新版本
unzip bedrock-server-1.14.30.2.zip
rm -rf bedrock-server-1.14.30.2.zip
```
 - 这样就ok了，这时候可以测试下
```
LD_LIBRARY_PATH=. ./bedrock_server
```
 - 你马上就酸了
```
./bedrock_server: /lib/x86_64-linux-gnu/libm.so.6: version `GLIBC_2.27' not found (required by ./bedrock_server)
./bedrock_server: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `CXXABI_1.3.11' not found (required by ./bedrock_server)
./bedrock_server: /usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: version `OPENSSL_1_1_1' not found (required by ./libCrypto.so)
```
 - 嘿嘿。这里推荐先安装openssl，可以一键安装的
```
apt install openssl -y
```
 - gcc与g++安装看[这里](https://www.loliboy.com/topic/5/%E8%8B%8F%E8%81%94%E9%9D%92%E5%B9%B4%E8%BF%99%E6%A0%B7%E5%9C%A8debian%E9%87%8C%E5%AE%89%E8%A3%85g-9-%E7%BE%8E%E5%9B%BD%E4%BA%BA%E7%9C%8B%E5%AE%8C%E5%93%AD%E4%BA%86)如果你在上述测试步骤中有GLIBC和CXXAPI报错，[这里](https://www.loliboy.com/topic/5/%E8%8B%8F%E8%81%94%E9%9D%92%E5%B9%B4%E8%BF%99%E6%A0%B7%E5%9C%A8debian%E9%87%8C%E5%AE%89%E8%A3%85g-9-%E7%BE%8E%E5%9B%BD%E4%BA%BA%E7%9C%8B%E5%AE%8C%E5%93%AD%E4%BA%86)教程文末的修改默认g++和gcc就**不用执行**了（如果安装后gcc/g++ -v后的输出版本＜9.x，那当然要执行）
 - 完成后再次测试，success

![7.png](/assets/uploads/files/1581848267499-7.png) 

#### 4.安装BDL
 - 先安装依赖
```
apt install libreadline-dev python3 python3-pip clang-format git -y
pip3 install --user ply
```
 - 然后直接按官方文档装就行
```
git clone https://github.com/sysca11/bdlauncher bdlauncher-git -b master --depth=1
pushd bdlauncher-git
make RELEASE=1 #这一步必须有
make install RELEASE=1 DESTDIR=..
popd
```
 - 然后，你就可以开服辣！
```
./bdlauncher
```