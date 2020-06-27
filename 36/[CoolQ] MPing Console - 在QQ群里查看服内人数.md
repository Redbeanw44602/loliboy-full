### 简介
> 这个插件基于酷Q SDK（机器人插件），接口由CodeHz开发，这个本来是给我自己服务器开发的一个插件。特点是不能自定义查询的服务器IP和端口，仅支持**通过名称**来查询服务器状态。

### 展示
> 从Config可以看出来自由度还是很高的~ 

![1.png](/assets/uploads/files/1585048485543-1.png) 

### 变量说明
Name | 可用 | 备注(在消息发出时...)
-|-|-
[servername] | 正常/故障 | 替换为服务器名
[nowplayers] | 正常 | 替换为服务器当前在线玩家数
[maxplayers] | 正常 | 替换为服务器最大玩家数
[cleanname] | 正常 | 替换为服务器内部名
[version] | 正常 | 替换为服务器版本

### 常量说明
Name | 可用 | 备注(在消息发出时...)
-|-|-
[#linebreak] | 正常/故障 |  替换为标准换行符

> **务必注意** 涉及换行请使用[#linebreak]，而不是潇洒一回车。。。

### 兼容性
> 在Wine中测试未发现严重Bug

### Download
 - [com.loliboy.mping.cpk](/assets/uploads/files/1585067208351-com.loliboy.mping.cpk) 

### API接口搭建
> 可以使用自带的接口 https://api-mping.loliboy.com （实时获取，安全可信任），也可以自行搭建API接口。
> 该接口是CodeHz开发的，再次感谢大佬~
 - **依赖Node.js**，此处不再赘述。
```
apt install screen #deb系
mkdir mping #目录名称随意
wget https://www.loliboy.com/assets/uploads/files/1585066571407-mping.zip
unzip 1585066571407-mping.zip #解压
npm install -production #安装依赖包
screen node main.js #若要持续运行，请使用screen！
```

 - 修改监听端口
> MPing默认是监听1234端口，可不可以改呢？当然是可以的！
```
// 编辑main.js，在最后一行我们可以看见这样
app.listen(+(process.env.PORT || 1234));  //1234就是端口号，改掉即可。
```
 - Github API仓库地址
> 吹了这么久🐂🍺，还没说仓库地址呢
```
https://github.com/codehz/mcpe-ping-dashboard
```
 - 不喜欢仓库里的这个风格，一个Dashboard感觉毫无卵用。搭API还是用我上面给的那个（作者也是Hz大佬）**记得去给他一个:star:~**

### 此插件的意义
> 有人问，仅支持通过名称查询意义何在？对我来说当然有意义，我不能忍受一个一百年没见过玩家的在我服务器群里公然Ping自己的服务器地址。