#### 如果想杀掉4040端口进程，我的Mac为例：
```
sudo lsof -i :4040
```
会输出如下信息：
```
COMMAND   PID USER   FD   TYPE            DEVICE SIZE/OFF NODE NAME
java    38639 eric  262u  IPv6 0x731427fd0077f5d      0t0  TCP *:yo-main (LISTEN)
```
然后运行：
```
sudo kill -9 38639
```

#### 启动spark的操作是在其根目录下输入，在终端中输入：
```
 ./bin/spark-shell
```
#### 退出的正确操作是：
```
:quit
```
