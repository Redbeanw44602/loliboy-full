#### **1.效果图**
 - 效果通过魔改base.mod并配合两个插件文件实现~

![c-l64i4pv1-t0b48-7bqnot.png](/assets/uploads/files/1582516189652-c-l64i4pv1-t0b48-7bqnot.png) 

#### **2.环境要求：**```sysstat``` ```screen```
 - 需要通过syssatat获取服务器信息，screen维持脚本运行。使用命令安装：
```
apt install sysstat screen -y
```

#### **3.修改插件文件**
 - 下载魔改过的base.mod源码：[蓝奏云](https://www.lanzous.com/i9hwvgf) or [社区](/assets/uploads/files/1582516619692-base.zip) 
 - 解压到**bdlauncher-git/mod/base**下，覆盖源文件，编译。
```
make mod-base RELEASE=1 && copy ./build/mods/base.mod ../mods/
```
 - 此外，base里有个魔改函数依赖我另一个魔改过的mod：money.mod

#### **4.两个脚本**
 - 需要两个脚本 [蓝奏云](https://www.lanzous.com/i9hwzra) or [社区](/assets/uploads/files/1582517026663-scripts.zip) 
 - 解压后放到服务端根目录就ok

#### **5.启动screen**
 - 为了让脚本持续运行，需要使用screen
```
screen -S script #名称随意
```
 - 接着，
```
chmod +x getInfo.sh & ./getInfo.sh
```
 - 如无错误提示，脚本会每秒获取一次服务器状态，请使用**Ctrl+A+D**退出screen

#### **6.修改cmd.json**
 - 这里提供我的配置文件，仅供参考；5秒刷新一次服务器状态

![NO)YJ4OEEDK6LL@VYN%84ZD.png](/assets/uploads/files/1582123221846-no-yj4oeedk6ll-vyn-84zd.png) 

#### **7.base.mod魔改内容解释(可选)**
 - 解释一下我魔改的base.mod的新增内容
```
<$(<command>)/> #管道执行shell指令，并返回输出结果
```
 - 效果的话，举个栗子（配图有错误，应该为：```$<(uname -a)/>```）

![1I~DL%W`IL%0RW5C_2G8@0R.png](/assets/uploads/files/1582123447011-1i-dl-w-96-il-0rw5c_2g8-0r.png) 

 - 玩家加入的时候，就会提示如下消息：

![UO1$UL7GFL@YV7294G0@O0.png](/assets/uploads/files/1582123719505-uo1-ul-7gfl-yv7294g0-o0.png) 

 - 注意，我并没有为shell指令进行过滤，请小心**不要以root身份执行**。
> 执行耗时较长的指令将会阻塞服务器 ，请务必小心使用该功能！
> **请勿用于商业用途，转载请留下作者名称meetinaxd@ltiex.com**

 #### **8.最后留下要饭方式，您的支持将是我继续~~折腾~~工作的动力~**
 - **支付宝**，不使用微信）

![u-ce-r8-te9g7n4-fw8-t.png](/assets/uploads/files/1582517748626-u-ce-r8-te9g7n4-fw8-t.png)