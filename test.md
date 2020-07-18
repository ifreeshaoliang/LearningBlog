## 在VScode上配置Git

> 前置条件：有VScode，有GitHub账号，创建了GitHub项目。

**1. 在本地创建一个文件夹，进入文件夹后，鼠标右键打开git bush here**

**2. 设置全局变量**
~~~
git config --global user.name "your name"

git config --global user.email "your@email.com"
~~~

**3. 登陆GitHub，创建SSHkey**

git内输入这个，连续点击三次回车键，创建SSHkey。
~~~
ssh-keygen -t rsa -C "your@email.com"
~~~
然后本地用户文件夹下生成.ssh的文件夹，里面包含id_rsa和id_rsa.pub两个文件。复制id_rsa.pub的内容。

打开GitHub需要配置的项目，点击Setting->Deploy keys->Add deploy keys。随便输入个title，将前面复制的内容粘贴到key中。

回到git输入
~~~
ssh -T git@github.com
~~~
出现yes就配置成功了。

**4. 克隆仓库**
git内输入这个，克隆仓库到本地
~~~
git clone git@github.com:xxx（克隆连接）
~~~

