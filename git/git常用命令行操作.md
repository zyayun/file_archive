git常用命令行操作：

# git用户相关

```shell
git config --global user.name [username]
git config --global user.email [email]
```

重置用户名+密码

```shell
git config --system --unset credential.helper
```

存储用户名+密码

```shell
git config --global credential.helper store
git pull
然后就会要求输入用户名(邮箱)+密码，git就会保存了
```

git clone时拼接用户名+密码

```shell
//git clone http://username:pwd@remoterUrl
如果username或者pwd中有@或其他特殊符号，需要转义
@的转义是%40
git clone http://1111111%40qq.com:123456@remoteUrl
```

报如下错误时的解决方式：

```shell
git.exe push --progress "origin" master:master

Enumerating objects: 33, done.
Counting objects: 100% (33/33), done.
Delta compression using up to 4 threads
Compressing objects: 100% (15/15), done.
Writing objects: 100% (18/18), 1.79 KiB | 612.00 KiB/s, done.
Total 18 (delta 9), reused 0 (delta 0)
fatal: the remote end hung up unexpectedly
fatal: the remote end hung up unexpectedly
error: RPC failed; curl 52 Empty reply from server
Everything up-to-date
原因：
文件太大(我也没懂，我的文件并不大)
解决方式:
git config http.postBuffer 524288000
```

# 报错

报openssl错误时的解决办法

```yaml
报错信息：
 OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443
解决办法:
git config --global --unset http.proxy
```

git 将其他分支某一个提交记录合并至当前分支

```shell
首先切换到当前分支
git checkout branch-vxxx;
然后找到提交的id，合并至当前分支
git cherry-pick commitId
最后，push所做更改，值得注意的是，这个操作不需要commit，直接push就OK
git push
```

git 出现密码错误的解决办法-mac：

```shell
报错信息
Authentication failed for 'http://xxx/app/xxx.git/'
解决办法
打开：/Users/username/Library/Keychains文件夹，找到login.keychain-db
搜索git相关项后，删除
在AS命令行 重新 git pull 会要求重新输入密码
```



# 分支管理

## 创建切换分支

```shell
git clone https://github.com/wlz1244/qingoo.git  //下载一个master分支代码 

git branch wlz //新建wlz分支

git checkout wlz //切换到wlz分支

git pull origin dev //将远程dev分支更新到本地wlz分支

··············写代码
```

## 分支合并

```shel
git add .

git commit -m "XXXXX" //现在还是wlz分支

git checkout dev  //切换到dev分支

git pull origin  //将本地dev分支更新到最新远程dev分支，一摸一样

git merge wlz //将本地wlz分支合并到本地最新dev分支

·············有冲突的话，解决冲突
```



```shell


// git add .

// git commit -m "XXXXX"

git push origin dev //提交到远程dev分支

git checkout wlz //切换到wlz分支

git pull origin dev //更新最新代码到本地

git reset --hard origin/dev   后退已经commit的东西到git服务器的最新代码

git checkout -b 分支名称(新建本地分支)

git push origin 分支名称（本地分支推送到远程）

git push origin --delete wlz  删除远程wlz分支
把新建的本地分支push到远程服务器，远程分支与本地分支同名（当然可以随意起名）：

$ git push origin localbranch:localbranch

使用git branch -a查看所有分支，会看到remotes/origin/localbranch这个远程分支，说明新建远程分支成功。

删除远程分支
我比较喜欢的简单方式，推送一个空分支到远程分支，其实就相当于删除远程分支：

$ git push origin :localbranch
也可以使用：

$ git push origin --delete localbranch
这两种方式都可以删除指定的远程分支

```

# 切换远程分支

```shell
当我想从远程仓库里拉取一条本地不存在的分支时：
git checkout -b 本地分支名 origin/远程分支名
git checkout -b dev0.1 origin/dev0.1
```



