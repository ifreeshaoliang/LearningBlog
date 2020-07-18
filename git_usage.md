## Git的使用

**1. 在本地创建一个文件夹，进入文件夹后，鼠标右键打开git bush here**

**2. 设置全局变量**
~~~
git config --global user.name "your name"
git config --global user.email "your@email.com"
~~~

**3. 解决github提交代码不用输入密码**
~~~
git config --global credential.helper store
~~~
这一步会在用户目录下的.gitconfig文件最后添加：
~~~
[credential]
    helper = store
~~~

**4. 克隆仓库**
git内输入这个，克隆仓库到本地
~~~
git clone git@github.com:xxx（克隆连接）
~~~

**5. 提交**
