```css
git --version
git init
git status
git log
git relog
git branch
git branch -r
git branch -d
git branch master
git add .
git commit -m 'first commit'
git reset --hard HEAD^
git reset --hard 33d9d598d
git remote add origin https://....
git remote remove origin https://.
git push -u origin master
git push orgin master
git push
git clone https://.......
git switch master
git checkout master
git checkout -b dev
git merge dev
git pull origin master

https://github.com/cfg1573/test2302NB

```

Git是目前世界上最先进的分布式版本控制系统(没有之一)

Git有什么特点简单来说就是:高端大气上档次!

###  版本管理工具的分类

#### 1:svn(集中式)

集中式版本控制系统,版本库是集中存放在中央服务器的.而干活的时候,用的都是自己的电脑,所以要先从中央服务器取得最新的版本,然后开始干活,干完活了,再把自己的活推给中央服务器,中央服务器就好比是一个图书馆,你要改一本书,必须先从图书馆借出来,然后回到家自己改,改完了,再放回图书馆

#### 2:git(分布式)

分布式版本控制系统根本没有中央服务器,每个人的电脑上都是一个完整的版本库,这样,你工作的时候,就不需要联网了,因为版本库就在你自己的电脑上

和集中式版本控制系统相比,分布式版本控制系统的安全性要高很多,因为每个人的电脑里都有完整的版本库,某一个人的电脑坏掉了不要紧,随便从其他人那里复制一个就可以了,而集中式版本控制系统的中央服务器要是出了问题,所有人都没法干活了

在实际使用分布式版本控制系统的时候,奇石很少在两人之间的电脑上推送版本库的修改,因为可能你们俩不在一个局域网内,两台电脑互相访问不了,也可能今天你的同事病了,他的电脑压根开不了机,依次分布式版本控制系统通常也有一台充当服务器的电脑,但这个服务器的作用仅仅是用来方便交换大家的修改,没有他大家也一样干活,只是交换修改不方便而已

###### 控制台输入:git --version,显示安装的git版本号



### 1:创建本地版本库

Git操作



第一种创建git的方法

1:打开资源管理器,进入需要创建git仓库的目录下,在上方地址栏中输入cmd,打开命令提示符,输入git init	//初始化git,生成git可以管理的仓库

瞬间Git就把仓库建好了,而且告诉你是一个空的仓库(empty Git repository),当前目录下多了一个.git的目录,这个目录就是Git来跟踪管理版本库的,没事千万不要手动修改这个目录里面的文件.不然改乱了.就把Git仓库给破坏了,如果没有看见这个文件夹,因为.git文件夹是隐藏的文件夹,可以通过查看,勾选隐藏的项目勾选出来



第二种创建git的方法:

在需要创建git的版本库的文件夹下

按shift键后右键

点击 在此处打开Powershell窗口

输入git init命令,同样可以创建git版本库



第三种方法:

在vscode的文件下,右键,在集成终端中打开,输入git init即可



### 常规开发项目

创建项目,正常的代码

代码 一定要放到git仓库下,因为这是一个 Git仓库,放到其他地方Git再厉害也找不到这个文件

### 提交到本地仓库

第一步:git status	检查版本库的状态

第二步,用命令git add<file>告诉git,把文件添加到仓库

git add .	提交全部<注意!!!	git 空格 add 空格 点>

第三步:用命令git commit -m '提交说明'	告诉git,把文件提交到仓库

第四步:提交时,会提示配置用户

git config --global user.name 'username'	//username是你的git账号

git config --global user.email 'email'	//email是你的git邮箱

如果提示让输入用户名,接下来输入命令:

```css
git config --global user.name li_magisk				   //回车
git config --global user.email l1919202265@gmail.com	//回车
```

工作区有一个隐藏目录.git,这个不算工作区,而是Git的版本库

git的版本库里面存了很多东西,其中最重要的就是stage(或者叫index)的暂存区,还有Git为我们自动创建的第一个分支master,以及指向master的第一个指针叫HEAD

### 5:初始化一个Git仓库,使用git init命令

添加文件到Git仓库,分两步:

1:使用命令git add<file>,注意,可反复多次使用,添加多个文件;

2:使用命令git commit -m 'message'	完成

### 6:版本回退

金庸群侠传

存档

你不断对文件进行修改，然后不断提交修改到版本库里，就好比玩RPG游戏时，每通过一关就会自动把游戏状态存盘，如果某一关没过去，你还可以选择读取前一关的状态。有些时候，在打Boss之前，你会手动存盘，以便万一打Boss失败了，可以从最近的地方重新开始。Git也是一样，每当你觉得文件修改到一定程度的时候，就可以“保存一个快照”，这个快照在Git中被称为commit。一旦你把文件改乱了，或者误删了文件，还可以从最近的一个commit恢复，然后继续工作，而不是把几个月的工作成果全部丢失。

当然了，在实际工作中，我们脑子里怎么可能记得一个几千行的文件每次都改了什么内容，不然要版本控制系统干什么。版本控制系统肯定有某个命令可以告诉我们历史记录，在Git中，我们用`git log`命令查看：

```css
git log		//git提交日志
git relog	//git每一次提交的日志信息
```



#### 在Git中,我们用git log命令查看,提交的历史记录

### 7:回退

现在我们启动时光穿梭机,准备把index.html回退到上一个版本,也就是第三次添加10个li标签的那个版本,怎么做呢?

首先,Git必须知道当前版本是哪个版本,在Git中,用HEAD表示当前版本,也就是最新的提交`6d20e733...`(注意我的提交的ID和你的肯定不一样的),上一个版本就是HEAD^,上上个版本就是HEAD^^,当然我们往上100个版本写100个^比较容易数不过来,所以些好吃呢个HEAD~100

现在,我们要把当前版本 第四次添加类名four的divb标签 回退到上一个版本 第三次添加10个li标签,就可以使用git reset命令

```css
git reset --hard HEAD^
```

代码也会跟着自动的更新,会回退到第三次状态时的代码

### 8:后悔药

会的版本过分了,后悔了,只要上面的命令行窗口还没有关掉,你就可以顺着往上找找,找到那个某个版本的commit id是33d9d598d123bb1327ba2abd9b73b725000abd9c,于是就可以指定回到未来的某个版本:

```css
git reset --hard 33d9d598d
```

版本号没必要写全,前几位就可以了,Git会自动去找,当然也不能只写前一两位,因为Git可能会找到多个版本号,就无法确定哪一个

如果命令行关闭了,怎么办呢?记不住版本号了把?

Git提供了一个命令git reflog用来记录你的每一次命令:

## 5远程仓库

Git是分布式版本控制系统,同一个Git仓库,可以分布到不同的机器上,在呢么分布呢,最早,肯定值有一台机器有一个原始版本库,此后,别的机器可以克隆这个原始版本库,而且每台机器的版本库其实都一样的,并没有主次之分

你肯定会想,至少需要两台机器才能玩下远程仓库不是?到那时我只有一台电脑,怎么玩?

实际情况往往是这样,找一台电脑充当服务器的角色,每天24小时开机,其他每个人都从这个歌服务器仓库克隆一份到自己的电脑上,并且各自把各自的提交推送到服务器仓库里,也从服务器仓库中拉取别人的提交

完全可以自己搭建一一台运行Git的服务器,不过现阶段,为了学Git先搭建个服务器绝对是大题小做,好在这个世界上有个叫GitHub的神奇网站,从名字就可以看出,这个网站就是提供Git仓库托管服务的,所以,只要注册一个GitHub账号,就可以免费获得GitHub远程仓库

##### 1:注册账号

自行注册GitHub账号

登录到Github

新建一个远程仓库

##### 2本地git仓库和github仓库之间的传输是通过SSH加密,查看秘钥

鼠标右击Git bash Here下查看

```css
ls -al ~/.ssh	//检查ssh keys是否存在
```

此命令窗口	不支持Ctrl+v粘贴	需要右击	点击paste

```css
ssh-keygen -t rsa -C '***'		//添加一个ssh
```

ssh-add ~/.ssh/id_res                        生成新的key
   -t = The type of the key to generate
    密钥的类型
    -C = comment to identify the key
    用于识别这个密钥的注释
    So the Comment is for you only and you can put anything inside.
    Many sites and software are using this comment as the key name.
    所以这个注释你可以输入任何内容，很多网站和软件用这个注释作为密钥的名字

#### 本地管理员目录会出现一个.ssh文件夹

里面有id_rsa和id_rsa.pub两个文件

这两个就是SSH Key的秘钥对

id_rsa			//私钥

id_rsa.pub	 //公钥

登陆GitHub，打开“Account settings”，“SSH Keys”页面：

点击new SSH key

然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容：

ssh -T git@github.com   检测是否建立连接成功

如果不成功

```http
    https://blog.csdn.net/nightwishh/article/details/99647545
```



```
Host github.com
User 473203063@qq.com
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443
```

按shift

输入:wq 保存退出

为什么GitHub需要SSH Key呢？因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。
当然，GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。
最后友情提示，在GitHub上免费托管的Git仓库，任何人都可以看到喔（但只有你自己才能改）。所以，不要把敏感信息放进去。

如果你不想让别人看到Git库，有两个办法，一个是交点保护费，让GitHub把公开的仓库变成私有的，这样别人就看不见了（不可读更不可写）。另一个办法是自己动手，搭一个Git服务器，因为是你自己的Git服务器，所以别人也是看不见的。这个方法我们后面会讲到的，相当简单，公司内部开发必备。

#### 2、添加到远程仓库

1.创建远程仓库
2.本地仓库添加到远程仓库

点击要提交的远程仓库：

把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

从现在起，只要本地作了提交，就可以通过命令：

```css
/*关联远程仓库*/ 
git remote add origin https://github.com/l1919202265/01webtest.git
/*断开连接*/
git remote remove origin
/*发送  推向到远程仓库*/
git push -u origin master
git push origin master
```



# 6、克隆远程仓库



上面，我们讲了先有本地库，后有远程库的时候，如何关联远程库。
现在，假设我们从零开发，那么最好的方式是先创建远程库，然后，从远程库克隆。
首先，登陆GitHub，创建一个新的仓库，名字叫xxx：
现在，远程库已经准备好了，下一步是用命令git clone克隆一个本地库：

登陆gitHub,点进项目，选择code,选择ssh,复制地址，当前地址就是我们克隆项目的地址

> git@github.com:cfg1573/test_QY133.git

> git@github.com:cfg1573/QY135Nb666.git

如果有多个人协作开发，那么每个人各自从远程克隆一份就可以了。

1、新建文件夹，输入cmd

2、输入命令：

```css
git clone git@github.com:cfg1573/test_QY133.git
```

回车 克隆完成

克隆完成，文件下载至本地

小结
要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
Git支持多种协议，包括https，但ssh协议速度最快。

# 6、分支的概念

分支就是科幻电影里面的平行宇宙，当你正在电脑前努力学习Git的时候，另一个你正在另一个平行宇宙里努力学习SVN。
如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，结果，你既学会了Git又学会了SVN！

分支在实际中有什么用呢？假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。

现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。

> 注意，从远程仓库克隆下项目后，我们需要在分支上进行代码编写，不能直接在主分支上进行修改

# 7、分支操作

#### 1、gitHub新建一个远程仓库，在本地克隆

克隆成功：

#### 2、在克隆成功的项目下，查看分支：



##### 查看分支：git branch

*在哪个分支前,就表示当前在哪个分支

##### 创建分支：git branch 分支名

git branch de 创建了一个dev分支，dev是devlop的缩写，表示开发分支

我们接下来的程序会写在dev分支上，写完以后再合并到主分支中

##### 切换分支：

```css
git switch name或者git checkout name  /*name表示分支名*/
git switch dev	/*切换到dev分支*/
```

##### 创建并切换分支

```css
git switch -c name或者git checkout -b name
```

#### 合并某分支到当前分支：

如果要把dev分支合并到master 需要先切换到master分支，因为合并是要把分支合并到当前分支

```css
git merge dev
```

例：

在dev分支下新建index.html,index.css，

添加，提交

然后切换到主分支，此时主分支中没有新提交的index.html文件

合并分支， git merge dev ,这样就把dev分支的内容提交到了主分支下面

#### 删除分支：git branch -d name

我们用过以后的分支，如果不想用了可以删掉

#### 3、解决冲突

当多个分支同时修改同一处代码时（同一个文件时），合并时就会出现冲突的情况

如：

在dev分支中修改index.html,修改，提交;

切换到master分支，继续修改index.html，修改，提交

合并dev分支到main分支中，此时就会出现冲突

两个分支同时修改一个文件，git不知道要使用哪一次提交

发生冲突时Git会显示标记更改的内容

```html
<<<<<<<HEAD(当前的更改)
<h1>当前更改的内容</h1>
=======
<h1>传入的更改</h2>
>>>>>>>dev(传入的更改)
```



解决方法，手动更改

如：点击保留双方更改

点击后再次添加、提交

#### 4、查看分支情况



**git log也可以看到分支的	情况**

**git log --graph命令可以看到分支合并图**

# 8、分支策略

在实际开发中，我们应该按照几个基本原则进行分支管理：

首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。
所以，团队合作的分支看起来就像这样：

# 9、多人协作

管理员先在远程仓库创建好仓库，并建立好相关分支，比如master分支，dev分支

建A,B两个文件夹，代表另个程序员进行克隆

要查看远程库的信息，用 git remote
用 git remote -v 显示更详细的信息

当团队成员从远程仓库克隆时，实际上Git自动把本地的master分支和远程的master分支对应起来了，并且，远程仓库的默认名称是origin。

> git push -u origin master //向远程仓库origin 的master 分支提交代码
>
> git pull origin master //拉取远程仓库origin 的master 分支的代码

要查看远程库的信息，用 git remote
用 git remote -v 显示更详细的信息

当你的小伙伴从远程库clone时，默认情况下，你的小伙伴只能看到本地的master分支。不信可以用git branch命令看看

现在，你的小伙伴要在dev分支上开发，就必须创建远程origin的dev分支到本地，于是他用这个命令创建本地dev分支和远程仓库的分支连接起来：

> git checkout -b dev origin/dev
> //等同于一下多个命令合并使用 创建一个dev分支并切换到dev分支下，同时和远程仓库的dev关联起来
>
> git branch dev //新建分支
> git checkout dev //切换分支
> //没有把本地的dev分支与远程的dev分支关联起来，此时是没有拉去数据的

现在，他就可以在dev上继续修改，然后，时不时地把dev分支push到远程：

在dev分支新建一个index.html.，添加 提交

多人协作时，大家都会往master和dev分支上推送各自的修改。但是一般master是稳定的只是用来发布新版本分支，工作干活的分支是dev分支，一般团队成员只会提交dev分支。

# 10、推送分支

推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：

> git push origin master



如果要推送其他分支，比如dev，就改成：

> git push origin dev



但是，并不是一定要把本地分支往远程推送，那么，哪些分支需要推送，哪些不需要呢？

- master分支是主分支，因此要时刻与远程同步；
  - dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
- bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
- feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。



你的小伙伴已经向origin/dev分支推送了他的提交，而碰巧你也对同样的文件作了修改，并试图推送：

**b同学也来进行提交，出现冲突**



解决办法也很简单，Git已经提示我们，先用git pull把最新的提交从origin/dev抓下来，然后，在本地合并，解决冲突，再推送：

> git pull origin dev



冲突的文件：



手动解决冲突：再次提交

git pull成功，但是合并有冲突，需要手动解决，解决的方法和分支管理中的解决冲突完全一样。解决后，提交，再push

dev分支有内容：

main分支下什么也没有，因为没有合并：

使用github解决远程仓库合并：

git branch --set-upstream-to=origin/dev dev

**因此，多人协作的工作模式通常是这样：**



>1. 从远程克隆仓库到本地
>2. 拉取建立本地开发dev分支并常规开发
>3. 用git push origin <branch-name>推送自己的修改；
>4. 如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
>5. 如果合并有冲突，则解决冲突，并在本地提交；
>6. 没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！
>7. 如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。

<hr>

# 11、添加成员

#### 邀请方：

#### 被邀请者：

点击邀请者发送的链接

此时被邀请者可以看到一个正常的仓库界面

接下来点击仓库的远程地址

>如果不想配置秘钥，可直接使用https的链接地址
>
>git  clone https的地址，就可以完成克隆了
>
>剩下的就是正常的推送

```css
/*使用 --allow-unrelated-histories 参数强制合并历史记录*/
git pull origin master --allow-unrelated-histories
```

```css
/*如果你想要强制覆盖推送到远程仓库，可以使用 --force 参数来执行 git push 命令。请确保在执行此操作之前，你已经备份了重要的代码和数据，因为强制覆盖推送会永久地替换远程仓库中的代码。*/
git push --force origin master

```





> ——横线之前是命令
>
> ——横线之后是解释说明



1.新建文件夹，上方文件地址栏输入cmd，打开命令行
2.git init——初始化一个本地仓库
3.git remote add origin git项目地址——本地仓库关联远程仓库（用http方式就行，ssh的话提前配置密钥）
4.git fetch origin master——强制关联远程master分支
5.git branch -r——查看远程仓库的所有分支

> 以上项目代码就已经克隆下来了，并且关联了远程仓库，同步了所有分支，下面创建我们自己的分支



6.git branch——查看本地的所有分支，绿色的字代表自己现在所在的分支
7.git checkout master——切换到master分支上
8.git checkout -b xxx——创建并切换到xxx分支上（xxx是你自定义的分支名）
9.git push -u origin xxx——将自己的xxx分支推至远程仓库（第一次推加-u参数，后续再推就不用加了，推的时候自己要在当前的xxx分           支上）
10.git status——查看当前状态，在哪个分支上，更改了那些文件
11.git add .——将更改的文件内容添加到暂存区（注意不要少打这个.）
12.git commit -m '备注更改内容'——提交到本地仓库
13.git push origin xxx——推送至远程的xxx分支（第一次提交加-u参数）

> 以上创建了自己的分支，更改内容，并提交到了远程仓库，下面同步测试分支



14.git checkout master----切换至master分支
15.git checkout -b dev origin/dev——创建并切换到dev分支，并且同步远程的dev分支
16.git pull origin dev——合并之前，现将远程的dev拉下来一下，以免有其他人推送过新功能
17.git merge xxx——合并xxx分支代码（注意：要往哪个分支上合并，就先切换到哪个分支上）
18.git push origin dev——推送到远程的dev分支

> 同理：推送到master分支



19.git checkout master——切换至master分支
20.git pull origin master——拉下远程master分支的新代码
21.git merge xxx——将自己的xxx分支合并到master
22.git push origin master——推送至远程master

> 拉取别人分支
> 如果要拉取别人的分支，但git branch -r 发现远程并没有别人的这个分支



23.git remote update origin --prune——同步远程仓库的所有分支，这样可以拉别人的分支一起开发



> 最后：删除自己的本地分支和删除远程仓库的分支（要删除哪个分支，当前就不能在这个分支上）

git branch -d xxx——删除本地的xxx分支,该分支没有任何未提交的内容
git branch -D xxx——删除本地的xxx分支,该分支存在未提交的内容，强制删除
git push origin --delete xxx——删除远程仓库的xxx分支



可能存在的问题
```css
1:$ git push origin master
Username for 'https://github.com': li_magisk
Password for 'https://li_magisk@github.com':
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/l1919202265/Mynotes.git/'



此问题由于GitHub 在2021年8月13日删除了对密码身份验证的支持，并建议采用其他身份验证方式。这意味着你不能再使用密码直接进行对远程仓库的推送。

为了解决这个问题，你可以考虑以下两种方法来完成身份验证：

使用 SSH 密钥身份验证：使用 SSH 密钥进行身份验证是一个更安全和推荐的方式。首先，确保你已经生成了 SSH 密钥对，并将公钥添加到你的 GitHub 帐户中。然后，修改你的远程仓库的 URL，将其替换为 SSH URL。可以使用以下命令来修改 URL：

git remote set-url origin git@github.com:l1919202265/Mynotes.git
 
这将把远程仓库的 URL 修改为使用 SSH 协议进行身份验证。

使用访问令牌（Personal Access Token）进行身份验证：如果你不打算使用 SSH 密钥进行身份验证，你可以生成一个访问令牌并将其用作密码。访问令牌是一个用于访问 GitHub API 的身份验证凭证。你可以在你的 GitHub 帐户的设置中生成一个访问令牌。生成令牌后，在执行  git push  命令时，使用生成的令牌替代密码即可。

Username for 'https://github.com': li_magisk
Password for 'https://li_magisk@github.com':
 
这些输入提示是等待你输入 GitHub 的用户名和密码。因为现在不再支持直接使用密码进行身份验证，所以你需要使用其他方法进行身份验证。
```