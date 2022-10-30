# Git 的使用

​	**Git十分简单!!**（放屁，写了2天！）

## 版本控制

​	版本迭代，新的版本 版本管理器。
​	版本控制是一种在开发过程中用于管理我们对文件、目录、或工程等内容的修改历史，方便查看更改历史记录，备份以便回复以前版本的软件工程技术。	

* 实现跨区域的多人协同开发
* 追踪和记载一个或者多个文件的历史记录
* 组织和保护你的源代码和文档
* 统计工作量
* 并行开发、提高开发效率
* 跟踪记录整个软件的开发过程
* 减轻开发人员的负担，节省时间，同时降低认为错误

## 分布式版本控制 Git

​	每个人都拥有全部的代码。
​	不会因为网络问题造成不能工作的情况

## Git环境配置

​	怎么卸载。先删除环境变量，然后卸载。

​	安装就行，无脑下一步

## git相关的配置文件

​	当你安装Git后首先要做的事情是设置你的用户名和e-mail地址。这是非常重要的，因为每次Git提交都会使用该信息。它被永远地嵌入到了你地提交中.

```C
git config --global user.name "***" //名称
git config --global user.email ***  //邮箱
```

​	所有地配置文件都保存在Git的本地文件目录下

## Git核心理论

​	Git本地有三个工作区域 工作目录、暂存区、资源库。如果在加上远程的git仓库就可以分为四个工作区域。

![image-20221029141441024](C:\Users\aesash\AppData\Roaming\Typora\typora-user-images\image-20221029141441024.png)

* Workspace: 工作区，就是你平时存放代码的地方
* Index/Stage：暂存区，用于临时存放数据的位置，事实上它只是一个文件，保存即将提交到文件列表的信息
* Repositor：仓库区（或本地仓库），就是安全存放数据的位置，这里面有你提交所有版本的数据。其中HEAD指向最新放入仓库的版本
* Remote：远程仓库，托管代码的服务器，可以简单的认为你项目组中的一台电脑用于远程数据交换

![image-20221029143717110](C:\Users\aesash\AppData\Roaming\Typora\typora-user-images\image-20221029143717110.png)



![](https://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg)

**HEAD是指向master的一个“游标”。**

 **HEAD，它指向你最后一次提交的结果。**

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-process.png)

* 克隆Git资源作为工作目录

* 在克隆的资源上添加或修改文件

* 如果其他人修改了，你就可以更新资源

* 在提交前查看修改

* 提交修改

* 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交

  

## Git分支管理

使用分支意味着你可以从开发主线上分离开，然后在不影响主线的同时继续工作。

![img](https://static.runoob.com/images/svg/git-brance.svg)

有人把Git的分支模型称为**必杀技模型**，而正是因为它，将Git从版本控制系统家族里区分出来。

创建分支命令：

```bash
git branch (name)
```

切换分支命令：

```bash
git checkout (name)
```





## Git的使用

### 本地仓库的搭建

把git目录调到指定文件，然后输入以下命令即可搭建本地仓库

```bash
$ git init
```

复制Github上或者是Gitee上仓库的链接，然后输入以下命令即可搭建本地的克隆仓库

```bash
git clone [url] 
```

### 提交与修改

> git add     			#添加文件到暂存区
>
> git status 			#查看仓库当前的状态， 显示有变更的文件
>
> git diff				  #比较文件的不同，即暂存区和工作区的差异
>
> git commit		  #提交暂存区到本地仓库
>
> git reset			   #回退版本
>
> git rm				   #将文件从暂存区和工作区删除
>
> git mv				   #移动或重命名工作区文件





### git commit 命令

[![Git 基本操作](https://www.runoob.com/images/up.gif)Git 基本操作](https://www.runoob.com/git/git-basic-operations.html)

------

前面章节我们使用 git add 命令将内容写入暂存区。

git commit 命令将暂存区内容添加到本地仓库中。

提交暂存区到本地仓库中:

```bash
git commit -m [message]
```

[message] 可以是一些备注信息。

提交暂存区的指定文件到仓库区：

```bash
$ git commit [file1] [file2] ... -m [message]
```

**-a** 参数设置修改文件后不需要执行 git add 命令，直接来提交

```bash
$ git commit -a
```

##### 设置提交代码时的用户信息

开始前我们需要先设置提交的用户信息，包括用户名和邮箱：

```bash
$ git config --global user.name 'runoob'
$ git config --global user.email test@runoob.com
```

如果去掉 --global 参数只对当前仓库有效。

##### 提交修改

接下来我们就可以对 hello.php 的所有改动从暂存区内容添加到本地仓库中。

以下实例，我们使用 -m 选项以在命令行中提供提交注释。

```bash
$ git add hello.php
$ git status -s
A  README
A  hello.php
$ git commit -m '第一次版本提交'
[master (root-commit) d32cf1f] 第一次版本提交
 2 files changed, 4 insertions(+)
 create mode 100644 README
 create mode 100644 hello.php
 
```

现在我们已经记录了快照。如果我们再执行 git status:

```bash
$ git status
# On branch master
nothing to commit (working directory clean)
```

以上输出说明我们在最近一次提交之后，没有做任何改动，是一个 "working directory clean"，翻译过来就是干净的工作目录。

如果你没有设置 -m 选项，Git 会尝试为你打开一个编辑器以填写提交信息。 如果 Git 在你对它的配置中找不到相关信息，默认会打开 vim。屏幕会像这样：

```bash
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
# modified:   hello.php
#
~
~
".git/COMMIT_EDITMSG" 9L, 257C
```

如果你觉得 git add 提交缓存的流程太过繁琐，Git 也允许你用 -a 选项跳过这一步。命令格式如下：

```bash
git commit -a
```

我们先修改 hello.php 文件为以下内容：

```bash
<?php
echo '菜鸟教程：www.runoob.com';
echo '菜鸟教程：www.runoob.com';
?>
```

再执行以下命令：

```bash
$ git commit -am '修改 hello.php 文件'
[master 71ee2cb] 修改 hello.php 文件
 1 file changed, 1 insertion(+)
```









### git reset 命令

[![Git 基本操作](https://www.runoob.com/images/up.gif)Git 基本操作](https://www.runoob.com/git/git-basic-operations.html)

------

git reset 命令用于回退版本，可以指定退回某一次提交的版本。

git reset 命令语法格式如下：

```bash
git reset [--soft | --mixed | --hard] [HEAD]
```

**--mixed** 为默认，可以不用带该参数，用于重置暂存区的文件与上一次的提交(commit)保持一致，工作区文件内容保持不变。

```bash
git reset  [HEAD] 
```

实例：

```bash
$ git reset HEAD^            # 回退所有内容到上一个版本  
$ git reset HEAD^ hello.php  # 回退 hello.php 文件的版本到上一个版本  
$ git  reset  052e           # 回退到指定版本
```

**--soft** 参数用于回退到某个版本：

```bash
git reset --soft HEAD
```

实例：

```bash
$ git reset --soft HEAD~3   # 回退上上上一个版本 
```

**--hard** 参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交：

```bash
git reset --hard HEAD
```

实例：

```bash
$ git reset --hard HEAD~3  # 回退上上上一个版本  
$ git reset –hard bae128  # 回退到某个版本回退点之前的所有信息。 
$ git reset --hard origin/master    # 将本地的状态回退到和远程的一样 
```

**注意：** **谨慎使用 –-hard 参数，它会删除回退点之前的所有信息。**

**HEAD 说明：**

- HEAD 表示当前版本

- HEAD^ 上一个版本

- HEAD^^ 上上一个版本

- HEAD^^^ 上上上一个版本

  

- 以此类推...

  

可以使用 ～数字表示

- HEAD~0 表示当前版本

- HEAD~1 上一个版本

- HEAD^2 上上一个版本

- HEAD^3 上上上一个版本

- 以此类推...

  

##### git reset HEAD

git reset HEAD 命令用于取消已缓存的内容。

我们先改动文件 README 文件，内容如下：

```bash
# Runoob Git 测试
# 菜鸟教程 
```

hello.php 文件修改为：

```bash
<?php
echo '菜鸟教程：www.runoob.com';
echo '菜鸟教程：www.runoob.com';
echo '菜鸟教程：www.runoob.com';
?>
```

现在两个文件修改后，都提交到了缓存区，我们现在要取消其中一个的缓存，操作如下：

```bash
$ git status -s
    M README
    M hello.php
$ git add .
$ git status -s
M  README
M  hello.php
$ git reset HEAD hello.php 
Unstaged changes after reset:
M    hello.php
$ git status -s
M  README
    M hello.php
```

现在你执行 git commit，只会将 README 文件的改动提交，而 hello.php 是没有的。

```bash
$ git commit -m '修改'
[master f50cfda] 修改
    1 file changed, 1 insertion(+)
$ git status -s
    M hello.php
```

可以看到 hello.php 文件的修改并未提交。

这时我们可以使用以下命令将 hello.php 的修改提交：

```bash
$ git commit -am '修改 hello.php 文件'
[master 760f74d] 修改 hello.php 文件
    1 file changed, 1 insertion(+)
$ git status
On branch master
nothing to commit, working directory clean
```

简而言之，执行 git reset HEAD 以取消之前 git add 添加，但不希望包含在下一提交快照中的缓存。

## Git与GitHub

​	GitHub是全球最大的代码托管平台，基于git，付费用户可以建立私人仓库，而一般用户只能使用公共仓库

​	使用GitHub作为远程仓库，进行代码的托管。



### 添加远程库

​	由于你的本地Git仓库和GitHub仓库之间的传输是通过SSH加密的，我们需要先配置验证信息

​	首先在本地创建SSH key：

```
$ ssh-keygen -t rsa -C "your_email@youremail.com"
```

​	**your_email@youremail.com**为你在Github上注册的邮箱，之后会要求确认路径和输入密码，统一回车跳过。

​	如果成功的话，会在提示的地址下生成.ssh文件。![image-20221030180133980](C:\Users\aesash\AppData\Roaming\Typora\typora-user-images\image-20221030180133980.png)

到.ssh文件内部，打开id_rsa.pub，复制里面的key。

回到 github 上，进入 Account => Settings（账户配置）。

![img](https://www.runoob.com/wp-content/uploads/2015/03/48840BF0-992F-4CCC-A388-15CB74819D88.jpg)

左边选择 **SSH and GPG keys**，然后点击 **New SSH key** 按钮,title 设置标题，可以随便填，粘贴在你电脑上生成的 key。

![img](https://www.runoob.com/wp-content/uploads/2015/03/B0589847-A498-4415-8700-252BDE1B20C0.jpg)

![img](https://www.runoob.com/wp-content/uploads/2015/03/106AD534-A38A-47F3-88A3-B7BE3F2FEEF1.jpg)

添加成功后界面如下所示



![img](https://www.runoob.com/wp-content/uploads/2015/03/EC8F8872-091A-4CAB-90F2-616F34F350A9.jpg)

为了验证是否成功，输入：

```bash
$ ssh -T git@github.com
```

若出现以下信息，就表示了我们成功链接到了GitHub上。

![image-20221030180447700](C:\Users\aesash\AppData\Roaming\Typora\typora-user-images\image-20221030180447700.png)

回到GitHub上，创建一个新的仓库。下面我们来介绍一下git remote命令。

#### git remote指令

**git remote** 命令用于在远程仓库的操作。

显示所有远程仓库：

```bash
git remote -v
```

添加远程版本库：

```bash
git remote add [shortname] [url]
```

shortname为本地的版本库的别名。

#### 如何将本地的代码提交到GitHub上

介绍一下git push命令

**git push** 命令用于从将本地的分支版本上传到远程并合并。

命令格式如下：

```
git push <远程主机名> <本地分支名>:<远程分支名>
```

如果本地分支名与远程分支名相同，则可以省略冒号：

```
git push <远程主机名> <本地分支名>
```

**实例**

以下命令将本地的 master 分支推送到 origin 主机的 master 分支。

```
$ git push origin master
```

相等于：

```
$ git push origin master:master
```

如果本地版本与远程版本有差异，但又要强制推送可以使用 --force 参数：

```
git push --force origin master
```

删除主机的分支可以使用 --delete 参数，以下命令表示删除 origin 主机的 master 分支：

```
git push origin --delete master
```

以我的 https://github.com/tianqixin/runoob-git-test 为例，本地添加文件：

```
$ touch runoob-test.txt      # 添加文件
$ git add runoob-test.txt 
$ git commit -m "添加到远程"
master 69e702d] 添加到远程
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 runoob-test.txt

$ git push origin master    # 推送到 Github
```

将本地的 master 分支推送到 origin 主机的 master 分支。

### 删除远程仓库

```bash
git remote rm [别名]
```





就此为第一版
