## Git的使用

**1. 在本地创建一个文件夹，进入文件夹后，鼠标右键打开git bush here**

**2. 初始化**
~~~
git init
~~~


**3. 设置全局变量**
~~~
git config --global user.name "your name"
git config --global user.email "your@email.com"
~~~

**4. 解决github提交代码不用输入密码**
~~~
git config --global credential.helper store
~~~
这一步会在用户目录下的.gitconfig文件最后添加：
~~~
[credential]
    helper = store
~~~

**5. 克隆仓库**

git内输入这个，克隆仓库到本地
~~~
git clone git@github.com:xxx（克隆连接）
~~~

**6. 拉取仓库**

git pull：相当于是从远程获取最新版本并merge到本地
~~~
git pull origin master
~~~

**7. 提交**

add：将文件添加到索引(将修改添加到暂存区)
~~~
git add .
git add hello.c hello.h
~~~

commit：将暂存区里的改动给提交到本地的版本库

> 每次使用git commit命令，我们都会在本地版本库生成一个40位的哈希值，这个哈希值也叫commit-id，commit-id 在版本回退的时候是非常有用的，它相当于一个快照，可以在未来的任何时候通过与git reset的组合命令回到这里。
~~~
git commit . -m "a commit message"
~~~

push：将本地版本库的分支推送到远程服务器上对应的分支
>一般形式为 git push <远程主机名> <本地分支名> <远程分支名> 

>例如 git push origin master：refs/for/master ，即是将本地的master分支推送到远程主机origin上的对应master分支， origin 是远程主机名。第一个master是本地分支名，第二个master是远程分支名。

>refs/for 的意义在于我们提交代码到服务器之后是需要经过code review 之后才能进行merge的，而refs/heads 不需要

~~~
git push origin master
//将本地的master分支推送到origin主机的master分支。如果master不存在，则会被新建。
~~~


**8. 删除文件**

>在Git中，删除也是一个修改操作。pull拉取下来，删除，再重新提交就行了
~~~
git rm xxx(文件)
~~~

>删错了，用git checkout -- test.txt 还原。因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本。


