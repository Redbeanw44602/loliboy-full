> 用apt-fast可以加速PPA源安装速度（apt-fast使用aria2多线程加速下载）

#### 0.基础软件包
```
apt-get install aria2 git -y
```

#### 1.克隆
```
git clone https://github.com/ilikenwf/apt-fast.git
cd apt-fast
```

#### 2.安装
```
cp apt-fast /usr/bin/
chmod +x /usr/bin/apt-fast
cp apt-fast.conf /etc
```