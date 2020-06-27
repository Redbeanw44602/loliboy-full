> **目录**
> —[【第一章】选择服务器与系统](https://www.loliboy.com/topic/13/bdl%E5%BC%80%E6%9C%8D%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E6%94%BE%E5%BC%83-%E7%AC%AC%E4%B8%80%E7%AB%A0-%E9%80%89%E6%8B%A9%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8E%E7%B3%BB%E7%BB%9F) 
> —[【第二章】部署BDS并开启BDL](https://www.loliboy.com/topic/14/bdl%E5%BC%80%E6%9C%8D%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E6%94%BE%E5%BC%83-%E7%AC%AC%E4%BA%8C%E7%AB%A0-%E9%83%A8%E7%BD%B2bds%E5%B9%B6%E5%BC%80%E5%90%AFbdl) 
> —[【第三章】其他的文档](https://www.loliboy.com/topic/16/bdl%E5%BC%80%E6%9C%8D%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E6%94%BE%E5%BC%83-%E7%AC%AC%E4%B8%89%E7%AB%A0-%E5%85%B6%E4%BB%96%E7%9A%84%E6%96%87%E6%A1%A3) *(完)

#### 本章纯属水章。主要讲一下部分插件的配置问题（可以说是把**官方文档**讲的**更啰嗦**一点），大佬请绕道。

# 按官方文档顺序介绍(官方文档好像没有顺序)
#### **1.编译**
 - 编译安装BDL在上一章讲过了，这里就不再赘述了
 - 在bdlauncher-git下执行

| 命令| 介绍|
| ------- | ----------- |
| ```make preload RELEASE=1``` | 编译preload |
| ```make mods RELEASE=1``` | 编译mods |
| ```make list-mod RELEASE=1``` | 显示模组列表|
| ```make mod-XXX RELEASE=1``` | 编译某个mod |

#### **2.故障排查**
 - 来自官方文档

| 错误模式 | 可能的解决方案 |
| - | - |
| `RapidJson::xxxxx` | 更新configs |
| `JSON ERROR` | 检查json语法 |
| 服务端崩溃 | 将BDS与BDL更新到最新版本 |

#### **3.更新BDL**
 - BDL的数据文件都在 **config/** 和 **data_v2/** 里，升级前注意备份
```
git clone https://github.com/BDLDev/bdlauncher bdlauncher-git -b master --depth=1
pushd bdlauncher-git
make RELEASE=1
make install RELEASE=1 DESTDIR=..
popd
```

#### 本 *”书“* 就这样完了（嘿嘿）其他的我认为官方文档讲的很清楚，自己[去看吧](https://github.com/BDLDev/bdlauncher/tree/master/docs/Plugins)