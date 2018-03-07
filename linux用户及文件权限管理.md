### 本章小结
1. 主要讲了关于如何进行用户的管理，如添加用户（useradd和adduser的区别），删除用户，用户权限的修改等等。//这里面并不熟悉
2. 讲了文件权限的一些东西，还有如何修改文件权限变更所有者。
3. 还有一些本章用到的常用命令。

### 常用命令
1. 查看当前用户who am i 只查看当前登录的用户名汉字洁whoami，不需要空格就可以
2. who 命令的参数
```
-a	打印能打印的全部
-d	打印死掉的进程
-m	同am i,mom likes
-q	打印当前登录用户数及用户名
-u	打印当前登录用户登录信息
-r	打印运行等级
其中打印运行等级又分为如下几个
0： 关机
1： 单用户
2： 无网络的多用户
3： 命令行模式
4： 未用
5： GUI（图形桌面 模式）
6 ： 重启

如果想在运行级别之间进行切换 
init 想要切换的运行级别如init 3可以直接切换到命令行模式
并不是所有的如行界面运行几倍都是5也不是所有的命令行模式运行都是3,运行级别是相对于系统来说的

这个运行界别可以
* 用来节约资源，如服务器上面不需要用到5
* 修改密码，直接进入3模式然后修改
```
### 查看文件权限
ls -l会显示
```
-rw-r--r-- 1 pi pi  304516 Nov 23 01:15 2017-11-22-171558_1440x900_scrot.png
-rw-r--r-- 1 pi pi   48665 Nov 23 01:18 2017-11-22-171815_655x390_scrot.png
-rw-r--r-- 1 pi pi 1791975 Nov 23 01:19 2017-11-22-171905_1440x900_scrot.png
drwxr-xr-x 2 pi pi    4096 Mar  1 00:39 Desktop
drwxr-xr-x 6 pi pi    4096 Nov 23 00:25 Documents
drwxr-xr-x 4 pi pi    4096 Jan 27 01:12 Downloads
drwxr-xr-x 2 pi pi    4096 Sep  8 00:12 Music
drwxr-xr-x 2 pi pi    4096 Sep  8 00:12 Pictures
drwxr-xr-x 2 pi pi    4096 Sep  8 00:12 Public
drwxr-xr-x 2 pi pi    4096 Sep  8 00:12 Templates
drwxr-xr-x 2 pi pi    4096 Sep  8 00:12 Videos
-rw-r--r-- 1 pi pi      38 Nov 30 23:57 a.sh
-rw-r--r-- 1 pi pi     375 Nov 30 01:24 led.py
drwxr-xr-x 2 pi pi    4096 Sep  7 23:45 python_games


drwxr-xr-x（文件类型和权限） 2（链接树） pi（所有者） pi（所属用户组）    4096（文件大小byte） Sep  8 00:12（最后修改时间） Videos（文件名）

```
* 文件类型和权限
```
drwxr-xr-x
第一位标识文件类型
d 目录
i 软链接（还有硬链接）
b 块设备
c 字符设备
s socket网络套接字
p pipe管道
- 普通文件
后面9位为文件权限
前三个属于拥有者的权限，中间三个是所属用户组权限，最后三个是其他用户组权限
r 表示允许读权限
w 表示允许写权限
X 表示允许执行权限
```
* 链接数
这个不是特别理解，可以理解这个文件的快捷方式个数吧，义务内分为硬链接和软链接
* 文件大小
单位是byte 可以给ls 命令加一个 -lh显示的更加直观

### 变更文件所有者
```
cd /home/lilei
ls iphone6
sudo chown shiyanlou iphone6
```
### 修改文件权限
1. 二进制数字表示  
* r（这个权重是2的2次方）W（这个权重是2的一次方）X（这个权重是2的0次方），如果全部都有是7  
每个文件有三个用户组（拥有者，所属用户组，其他用户），每个用户组有一个数字表示相应的权限。  
修改权限用这个命令 ‘’chmod 700 iphone6’‘
2. 加减赋值操作  
* chmod go-rw iphone6 其中
g、o 还有 u 分别表示 group、others 和 user，+ 和 - 分别表示增加和去掉相应的权限。
