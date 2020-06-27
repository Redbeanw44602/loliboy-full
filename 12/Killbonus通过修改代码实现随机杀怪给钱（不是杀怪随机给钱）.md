> 在使用BDL开服的过程中，你是否有如下烦恼？
> - Killbonus插件给玩家加钱加的太快了！
>
> 这容易产生资本主义，最终可能**导致革命** #滑稽

# Killbonus配置**随机杀怪给钱**（不是杀怪随机给钱）
>**警告!** 大佬请勿浏览此文！

### 为了避免zzkids，有必要解释一下：Killbonus自带了一个**杀怪随机给钱**功能，可以在killbonus.json中配置。但**默认**玩家只要一杀某生物100%会给钱（无论给多少）
**——————————————————**
#### **1.打开/mod/killbonus/main.cpp**
#### **2.在约第61行后添加**
```
int killucky;
srand(time(NULL));
killucky=rand()%100+1;
```

#### **3.然后，在约第61行的if替换**
 - 原代码
```
if (it != bonus_mp.end()) {
```
 - 修改为
```
if (it != bonus_mp.end() && killucky<=概率) {
```
 - 记得把概率改为整数，如78%给钱就写78

#### **4.编译并替换当前killbonus.mod就行**
 - 不会编译？（在git根目录）
```
make mod-killbonus
```