> **建议** 无特殊需求人员不要自编译EZ，实在太麻烦。用预编译版本就好
#### **0.本文使用的工具/软件**
 - VisualStudio 2019
 - Git
 - VcPkg
 - Bedrock Server
 - x64 Native Tools Command Prompt for VS 2019

#### **0.1 食用方法**
 - 如果已经有vs和git，跳过第一节和第二节
 - 开始操作前请预备足够的时间！
 - 本文各操作目录。自行变动、更改！
```
C:\Users\Administrator\Desktop   #本文操作目录
C:\Users\Administrator\Desktop\Eat  #本文EatPdb生成目录
C:\Users\Administrator\Desktop\ElementZero  #本文EZ项目目录
C:\Users\Administrator\Desktop\vcpkg  #本文vcpkg安装目录
G:\  #本文VS安装盘盘符
```

#### **1.安装Visual Studio**
 - 在[这里](https://visualstudio.microsoft.com/zh-hans/vs/community/)下载免费的社区版VS
 - 完成后运行，继续

![2.png](/assets/uploads/files/1584247521241-2.png) 
 - 选择 **.NET桌面开发**，**C++桌面开发**和**Windows平台开发**。当然你如果是个dalao并且闲的蛋疼并且心疼流量可以通过组件单选择安装  [**组件目录**](https://docs.microsoft.com/zh-cn/visualstudio/install/workload-component-id-vs-community?vs-2019=&view=vs-2019)
```
(Hz提供的组件单,直接按下图选不需要这个)
Microsoft.VisualStudio.Workload.NativeDesktop
Microsoft.VisualStudio.Workload.ManagedDesktop
Microsoft.VisualStudio.Component.VC.Tools.x86.x64
Microsoft.VisualStudio.Component.Windows10SDK.18362
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang
```

![5.png](/assets/uploads/files/1584251206593-5.png) 
 - Two hours、、、

![6.png](/assets/uploads/files/1584251347063-6.png) 
 -  登录，爱登不登

![4.png](/assets/uploads/files/1584249136767-4.png) 

#### **2.安装Git**
 - 在[**这里**](https://git-scm.com/download/win)下载
 - 如果死慢，可以用TX软件中心的 [**32位**](https://pc.qq.com/detail/12/detail_22692.html) [**64位**](https://pc.qq.com/detail/13/detail_22693.html)
 - 一路**Next**即可

![1.png](/assets/uploads/files/1584254188966-1.png) 

#### **3.安装VcPkg**
 - 打开万年Cmd
```
cd C:\Users\Administrator\Desktop
: 克隆vcpkg仓库
git clone https://github.com/microsoft/vcpkg.git
cd vcpkg
```
![3.png](/assets/uploads/files/1584254769210-3.png) 
 - 运行
```
bootstrap-vcpkg.bat
```
![4.png](/assets/uploads/files/1584254947441-4.png) 
 - 为所有用户安装VcPkg
```
vcpkg integrate install
```
![5.png](/assets/uploads/files/1584255081715-5.png) 

#### **4.克隆EZ仓库并安装需要的包**
```
cd ..
git clone https://github.com/Element-0/ElementZero
cd ElementZero
```
> **注意** vcpkg大部分包从Github获取，然鹅国内Github速度感人，普通的代理(v2rayN,ssrr) vcpkg是**不走的**，目前已知的可以用sstap（虚拟网卡）或者路由器代理也行
**如果** 实在不能用sstap，按以下文件表下载并重命名后丢到` C:\Users\Administrator\Desktop\vcpkg\downloads `  里

下载 | 命名
-|-
[Here](https://github.com/PowerShell/PowerShell/releases/download/v6.2.1/PowerShell-6.2.1-win-x86.zip) | PowerShell-6.2.1-win-x86.zip
[Here](https://github.com/open-source-parsers/jsoncpp/archive/1.9.2.tar.gz) | open-source-parsers-jsoncpp-1.9.2.tar.gz
[Here](https://github.com/boostorg/math/archive/boost-1.72.0.tar.gz) | boostorg-math-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/type_index/archive/boost-1.72.0.tar.gz) | boostorg-type_index-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/format/archive/boost-1.72.0.tar.gz) | boostorg-format-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/foreach/archive/boost-1.72.0.tar.gz) | boostorg-foreach-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/functional/archive/boost-1.72.0.tar.gz) | boostorg-functional-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/function/archive/boost-1.72.0.tar.gz) | boostorg-function-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/io/archive/boost-1.72.0.tar.gz) | boostorg-io-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/exception/archive/boost-1.72.0.tar.gz) | boostorg-exception-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/unordered/archive/boost-1.72.0.tar.gz) | boostorg-unordered-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/algorithm/archive/boost-1.72.0.tar.gz) | boostorg-algorithm-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/endian/archive/boost-1.72.0.tar.gz) | boostorg-endian-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/filesystem/archive/boost-1.72.0.tar.gz) | boostorg-filesystem-boost-1.72.0.tar.gz
[Here](https://github.com/past-due/bzip2-mirror/releases/download/v1.0.6/bzip2-1.0.6.tar.gz) | bzip2-1.0.6.tar.gz
[Here](https://github.com/xz-mirror/xz/archive/v5.2.4.tar.gz) | xz-mirror-xz-v5.2.4.tar.gz
[Here](http://www.zlib.net/zlib-1.2.11.tar.gz) | zlib1211.tar.gz
[Here](https://github.com/facebook/zstd/archive/10f0e6993f9d2f682da6d04aa2385b7d53cbb4ee.tar.gz) | facebook-zstd-10f0e6993f9d2f682da6d04aa2385b7d53cbb4ee.tar.gz
[Here](https://github.com/boostorg/iostreams/archive/boost-1.72.0.tar.gz) | boostorg-iostreams-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/tokenizer/archive/boost-1.72.0.tar.gz) | boostorg-tokenizer-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/date_time/archive/boost-1.72.0.tar.gz) | boostorg-date_time-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/thread/archive/boost-1.72.0.tar.gz) | boostorg-thread-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/locale/archive/boost-1.72.0.tar.gz) | boostorg-locale-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/proto/archive/boost-1.72.0.tar.gz) | boostorg-proto-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/phoenix/archive/boost-1.72.0.tar.gz) | boostorg-phoenix-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/pool/archive/boost-1.72.0.tar.gz) | boostorg-pool-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/tti/archive/boost-1.72.0.tar.gz) | boostorg-tti-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/variant/archive/boost-1.72.0.tar.gz) | boostorg-variant-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/spirit/archive/boost-1.72.0.tar.gz) | boostorg-spirit-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/serialization/archive/boost-1.72.0.tar.gz) | boostorg-serialization-boost-1.72.0.tar.gz
[Here](https://github.com/boostorg/multi_index/archive/boost-1.72.0.tar.gz) | boostorg-multi_index-boost-1.72.0.tar.gz
[Here](https://sqlite.org/2020/sqlite-amalgamation-3310100.zip) | sqlite-amalgamation-3310100.zip
[Here](https://github.com/SRombauts/SQLiteCpp/archive/09dd10886c560ab5af41cfe694567f34c88cd101.tar.gz) | SRombauts-SQLiteCpp-09dd10886c560ab5af41cfe694567f34c88cd101.tar.gz
[Here](https://github.com/boostorg/scope_exit/archive/boost-1.72.0.tar.gz) | boostorg-scope_exit-boost-1.72.0.tar.gz
[Here](https://github.com/msgpack/msgpack-c/archive/cpp-3.2.0.tar.gz) | msgpack-msgpack-c-cpp-3.2.0.tar.gz
[Here](https://github.com/jbeder/yaml-cpp/archive/yaml-cpp-0.6.2.tar.gz) | jbeder-yaml-cpp-yaml-cpp-0.6.2.tar.gz

> or [快乐一键包](https://dfile.top/Cloud/fuck.7z)
 - 整活后，一键安装~
```
vcpkg install @vcpkg.txt
```
 - 中途我遇到了一个司马问题，让安装英文语言包。

![6.png](/assets/uploads/files/1584257878553-6.png) 
 - 重新打开VS安装程序，如此

![7.png](/assets/uploads/files/1584257981164-7.png) 
 - 重新执行安装就好。

#### **5.EatPDB**
> 又一个Hz巨佬之作。
```
cd ..
git clone https://github.com/codehz/EatPdb.git
```
 - 冉后，点开EatPdb.sln

![1.png](/assets/uploads/files/1584268597034-1.png) 
 - ~~沃日，好JB炫酷~~

![2.png](/assets/uploads/files/1584268657564-2.png) 
 - 打包发布

![1.png](/assets/uploads/files/1584317339651-1.png) 
 - 选择你喜欢的文件夹

![2.png](/assets/uploads/files/1584317365421-2.png) 
 - 点发布

![3.png](/assets/uploads/files/1584317380833-3.png) 
 - 这样。EatPdb就编译成功le~

![4.png](/assets/uploads/files/1584317409748-4.png) 

#### **6.编译ElementZero**
 - 打开项目

![5.png](/assets/uploads/files/1584270592982-5.png) 

 - 叫装clang，那就装罢（不赘述）

![4.png](/assets/uploads/files/1584269674152-4.png)
 - 这时，我们需要一个Bedrock Server  [**官方**](https://www.minecraft.net/zh-hans/download/server/bedrock)or[**镜像**](http://redbeanw.ys168.com/) （注意下载的是Windows版BDS！）
 - 将ElementZero/eatpdb.yaml复制到刚刚生成的EatPdb目录
 - 将刚刚下载的bds复制到EatPdb目录
 - EatPdb生成目录现在看起来应该是这样

![2.png](/assets/uploads/files/1584318322058-2.png) 
 - 进入EatPdb目录，打
```
cd ../Eat
eatpdb exec eatpdb.yaml
```
![3.png](/assets/uploads/files/1584318418679-3.png) 
 - 打开x64 Native Tools Command Prompt for VS 2019（VS已预装）

![4.png](/assets/uploads/files/1584318489167-4.png) 
 - 进入目录，生成Lib
```
c:
cd C:\Users\Administrator\Desktop\Eat
lib /def:bedrock_server_mod.def /machine:x64
```
![5.png](/assets/uploads/files/1584318602400-5.png) 
 - 将bedrock_server_mod.lib复制到ElementZero/Lib，Lib没有就新建

![6.png](/assets/uploads/files/1584318716704-6.png) 
 - 回到VS，快乐编译（点安装）

![8.png](/assets/uploads/files/1584321041515-8.png) 
 - 生成在Dist目录 **（bedrock_server_mod.exe自己复制过来就星）**

![9.png](/assets/uploads/files/1584321133683-9.png) 
——
> 感谢@WangYneos 的帮助~