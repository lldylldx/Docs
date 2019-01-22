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

#### git add, status, diff

1. 如果想查看精简版的git status:
```
$ git status -s
```
2. 查看已缓存的改动：
```
$ git diff --cached
```
3. 查看已缓存的与未缓存的所有改动
```
$ git diff HEAD
```
