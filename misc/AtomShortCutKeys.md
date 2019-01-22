#### Atom常用快捷键
Atom设置选项 keybindings 中列举了相当长的一份关于快捷键的绑定列表，你也可以自定义快捷键的配置文件，有相同的快捷键则会覆盖掉原有的，使用你自己设定的。下面是一些常用的快捷键：

```
Crtl+Shift+M    开启Markdown实时预览
Command+Shift+P    打开命令窗口，可以运行各种菜单功能
Command + T    快速多文件切换
Command + F    文件内查找和替换
Command + Shift + F    多文件查找和替换
Command + [    对选中内容向左缩进
Command + ]    对选中内容向右缩进
Command + \    显示或隐藏目录树
Crtl + m    相应括号之间，html tag之间等跳转
Crtl + Alt + B    格式化代码（需要安装atom-beautify）
Crtl + `    调起CLI命令行界面（需要安装terminal-panel）
```
#### Branch 相关命令
1. 查看远程分支
```
$ git branch -a
```
2. 查看本地分支
```
$ git branch
```
3. 切换分支
```
$ git checkout -b dev_0.0.1 origin/dev_0.0.1
```
```
$ git branch
  master
\* dev_0.0.1
```
```
$ git checkout master
```
在切换branch时，应该先commit或者stash;

4. merge分支branchA到branchB
```
$ git checkout branchB
$ git merge --no-ff branchA
```

5. 为本地branch设置远程同步branch
```
git branch --set-upstream-to=origin/branchA branchLocal
```
#### Markdown 用法
