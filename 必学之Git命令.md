
### git 教程



```bash
$ mkdir learngit
$ cd learngit
$ pwd
/Users/michael/learngit
```

`pwd`命令用于显示当前目录。在我的Mac上，这个仓库位于`/Users/michael/learngit`。



第二步，通过`git init`命令把这个目录变成Git可以管理的仓库：

```
$ git init
Initialized empty Git repository in /Users/michael/learngit/.git/
```

瞬间Git就把仓库建好了，而且告诉你是一个空的仓库（empty Git repository），细心的读者可以发现当前目录下多了一个`.git`的目录，这个目录是Git来跟踪管理版本库的，没事千万不要手动修改这个目录里面的文件，不然改乱了，就把Git仓库给破坏了。

如果你没有看到`.git`目录，那是因为这个目录默认是隐藏的，用`ls -ah`命令就可以看见。



现在我们编写一个`readme.txt`文件，内容如下：

```
Git is a version control system.
Git is free software.
```

一定要放到`learngit`目录下（子目录也行），因为这是一个Git仓库，放到其他地方Git再厉害也找不到这个文件。

和把大象放到冰箱需要3步相比，把一个文件放到Git仓库只需要两步。

第一步，用命令`git add`告诉Git，把文件添加到仓库：

```
$ git add readme.txt
```

执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

第二步，用命令`git commit`告诉Git，把文件提交到仓库：

```
$ git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

简单解释一下`git commit`命令，`-m`后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。

嫌麻烦不想输入`-m "xxx"`行不行？确实有办法可以这么干，但是强烈不建议你这么干，因为输入说明对自己对别人阅读都很重要。实在不想输入说明的童鞋请自行Google，我不告诉你这个参数。

`git commit`命令执行成功后会告诉你，`1 file changed`：1个文件被改动（我们新添加的readme.txt文件）；`2 insertions`：插入了两行内容（readme.txt有两行内容）。







> 所谓实用主义，就是掌握了以下知识就可以玩转 `Git`，轻松应对90%以上的需求。以下是实用主义型的Git命令列表，先大致看一下



- `git clone`
- `git config`
- `git branch`
- `git checkout`
- `git status`
- `git add`
- `git commit`
- `git push`
- `git pull`
- `git log`
- `git tag`



**工作区（*Working Directory*）**



![](D:\B00-picture\python\python study 04.png)



**本地版本库（*Local Repository*）**

> 工作区有一个隐藏目录 `.git`，这个不算工作区，而是 `Git` 的版本库。

**暂存区（*stage*）**

> 本地版本库里存了很多东西，其中最重要的就是称为 `stage`（或者叫index）的暂存区，还有`Git` 为我们自动创建的第一个分支 `master`，以及指向 `master` 的一个指针叫 `HEAD`。

![python study 05](D:\B00-picture\python\python study 05.png)



**远程版本库（*Remote Repository*）**

> 一般指的是 `Git` 服务器上所对应的仓库，本文的示例所在的`github`仓库就是一个远程版本库

![python study 06](D:\B00-picture\python\python study 06.png)



**以上概念之间的关系**

> `工作区`、`暂存区`、`本地版本库`、`远程版本库`之间几个常用的 `Git` 操作流程如下图所示：

![python study 07](D:\B00-picture\python\python study 07.png)



**分支（*Branch*）**

> 分支是为了将修改记录的整个流程分开存储，让分开的分支不受其它分支的影响，所以在同一个数据库里可以同时进行多个不同的修改



![python study 08](D:\B00-picture\python\python study 08.png)



**主分支（*Master*）**

> 前面提到过 `master` 是 `Git` 为我们自动创建的第一个分支，也叫主分支，其它分支开发完成后都要合并到 `master`

**标签（*Tag*）**

> 标签是用于标记特定的点或提交的历史，通常会用来标记发布版本的名称或版本号（如：`publish/0.0.1`），虽然标签看起来有点像分支，但打上标签的提交是固定的，不能随意的改动，参见上图中的`1.0` / `2.0` / `3.0`



![python study 09](D:\B00-picture\python\python study 09.png)



**HEAD**

> `HEAD` 指向的就是当前分支的最新提交

![](D:\B00-picture\python\python study 10.png)





【笔记】

> **如何用GitHub记录自己的学习过程**

> 你可以在本地建立一个分支（branch），例如，取名为 `study`：

```bash
git branch study
git checkout study
```

> 如此这般之后，你在本地工作目录中所做的任何修改，都可以提交到 `study` 这个分支之中。





创建本地分支：git branch dev

报错：fatal: Not a valid object name: 'master'.

原因：

 问题描述-一个非法的master,原因：本地还没有创建master，你可以执行以下git branch，会发现没有看到本地分支列表

解决方案：

 如果本地没有文件，添加一个文件

![](D:\B00-picture\python\python study 02.png)



此时本地仓库主干master 创建成功，使用git branch 查看本地分支列表，会查看到如下图所示

![](D:\B00-picture\python\python study 03.png)

可以创建本地分支：

 git branch dev





（为了便于理解，在桌面上演示）

```bash
cd Desktop
mkdir study
cd study
```

以上代码，在桌面创建了一个study的版本库，并将路径指向了study。

![](D:\B00-picture\python\python study 01.png)





查看当前分支、创建/转换分支

```bash
git branch
git branch study
git checkout study
```

关联远程仓库：

```bash
git remote add origin git@github.com:XXX（GitHub账号名）/XXX（GitHub远程仓库分支名）.git
git push -u origin XXX
```





【参考文献】

1. git 下载安装及设置详细教程：https://blog.csdn.net/sanxd/article/details/82624127

2. 廖雪峰git 教程：https://www.liaoxuefeng.com/wiki/896043488029600
