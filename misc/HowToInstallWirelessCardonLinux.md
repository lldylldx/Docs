0. 运行命令
```
apt-get install make build-essential linux-headers-2.6.32.5-amd64
```
你可以查看一下自己的打开/boot就能看到

1. 查看网卡的芯片型号
通过lsusb -v找到这块网卡的芯片型号，RTL8188CUS
有看到wlan0 RTL8188CUS
然后到realtek官网去下载相应的linux驱动
下载后放到/usr/src
然后开始解压

2. 解开tar包
```
tar zxvf "包名"
```
3. 进入驱动目录，运行安装命令
```
sh INSTALL.sh
```
然后选择1

4. 开启无线网卡托管
```
sudo gedit /etc/NetworkManager/NetworkManager.conf

[ifupdown]
managed=true
```
5. 重启系统
进入桌面后右上角设置加入网络

6. Useful Link:
[WikiDevi](https://wikidevi.com/w/index.php?title=Category:TP-LINK&pagefrom=TP-LINK+TGR1900+%28Google+OnHub%29#mw-pages)

7. TP-LINK TL-WN826N 无线网卡芯片组
```
TP-LINK TL-WN826N USB 300M无线网卡。
芯片：Realtek RTL8192CU
接口：USB 2.0
```
