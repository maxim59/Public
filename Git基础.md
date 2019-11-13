# Git 基础  

## 安装Git

​		打开终端，输入git,看系统是否已安装Git

​		如果出现以下提示，则说明系统上没有安装Git

```
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
```

​		你可以通过sudo apt-get install git安装Git

## 创建版本库

​		版本库又名仓库，英文名`repository` ,可以理解为一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能够跟踪到，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

​		首先，选择一个合适的地方，创建一个目录：

​				`$ mkdir  文件名`

​				`$ cd  文件名`

​				`$ pwd`  此命令用于显示当前目录

​		通过`git init` 命令把这个目录变成Git可以管理的仓库：

​				`$ get init` 

​				输入此命令后，瞬间Git就把仓库建好了，而且还会告诉你这是一个空的仓库，你还会发现当前目录下多了一个.git 的目录，这个目录是Git来跟踪管理版本库的，千万别手动修改这个目录里面的文件，不然就把Git仓库个破坏了	

​					如果你没有看到.git 目录，那是因为这个目录默认是隐藏的，  用 ls -ah命令就可以看见了

## 把文件添加到版本库

​			编写一个文件，并将其放到使用`mkdir 文件名`创建的目录下，

​			`$ git add 文件名.后缀名` 

​			用命令`git commit` 告诉Git，把文件提交到仓库：

​					

```
$ git commit -m "wrote a Git file"
[master (root - commit) eaadf4e] wrote a Git file
1 file changed, 2 insertions(+)
create node 100644 Git.md

//-m 后面输入的是本次提交的说明，可以输入随意内容
	1 file changed:1个文件被改动
	2 insertions:插入了两行内容
```

​			因为commit可以一次性提交多个文件，所以可以多次add不同的文件

​			例如：`$ git add file1.txt`

​						`$ git add file2.txt file3.txt`

​						`$ git commit -m "add 3 files."`

## 修改文件内容

+++

​			1.运行`git status` 	查看当前状态：

​			2.查看具体修改内容：git diff <file>

​			3.提交修改，第一步：`git add`	

​										第二步：`git commit -m "add distributed"`

## 版本回退

​			不断对文件进行修改，然后不断提交到版本库里，如果不小心把文件改乱了，或者误删了文件，还可以从最近的一个commit恢复，（commit相当于快照），然后继续工作，而从头再来。

​			`git log`  查看历史记录，显示从最近到最远的提交日志

​			如果输出信息太多，看的眼花缭乱的，可以试着加上 --pretty=oneline参数

​			开始回退：首先必须知道当前版本，在Git中，用HEAD表示当前版本，上一个版本就是HEAD^,上上个版本就是HEAD^^,还可以使用HEAD~number来表示

​			`git reset -- hard HEAD^`

​			如果想返回最新修改的版本，可以继续使用 `git reset -- hard 版本号`	（版本号只需要输入前几位就可以了，Git会自动去找）

​			`git reflog` 记录每一次命令，可以在其中寻找你需要的版本号

## 工作区、暂存区和版本库

​			工作区：即在电脑里可以看得到的目录

​			版本库：工作区有一个隐藏目录`.git` 这个不算工作区，而是Git的版本库。

​			Git的版本库里存有很多东西，其中最重要的就是叫state（或者是index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针HEAD。

![image-20191111115811309](/home/maxim/.config/Typora/typora-user-images/image-20191111115811309.png)

​				前面讲到我们把文件往Git版本库里添加的时候，是分两步执行的：

​			第一步是用`git  add `	把文件添加进去，实际上就是把文件修改添加到暂存区

​			第二步是用`git  commit` 提交更改，实际上就是把暂存区的所有内容提交到当前分支

​			因为我们创建Git版本库是，Git自动为我们创建了唯一一个`master` 分支，所以，，现在，`git  commit` 就是往`master ` 分支上提交更改。

​			当然，你也可以理解为需要提交的文件修改童童放到暂存区，然后，一次性提交暂存区的所有修改。

工作区暂时有两个文件，分别是readme和LICENSE,使用`git add` 将它们添加到暂存区：

![git-stage](https://www.liaoxuefeng.com/files/attachments/919020074026336/0)添加到暂存区后，通过`git  commit` 一次性把暂存区的所有修改提交到分支

![git-stage-after-commit](https://www.liaoxuefeng.com/files/attachments/919020100829536/0)

## 管理修改

​			`Git 跟踪并管理的是修改，而并非是文件` 

​			第一步：对readme.txt	做一个修改

​			第二步：git add readme.txt

​			第三步：再次修改readme.txt

​			第四步：提交readme.txt 文件

​			第五步：git status 查看状态

​			这时我们会发现，在工作区的第二次修改并没有放入到暂存区，所以，`git  commit` 只负责把暂存区的修改提交。

​		如果不用`git add` 添加到暂存区，那就不会加入到`commit `中。

## 撤销修改

​			当你修改一份文件完毕准备提交时，忽然发现中间有个错误，之前的修改的东西全都白写了，这时你可以手动删除，把文件恢复到最初的状态。也可以使用`git  checkout --file`  丢弃工作区的修改。

​		`git checkout  --file` 可以把文件在工作区的修改全部撤销，这里有两种情况：一种是文件自修改后还没有放到暂存区，现在撤销修改的话就会回到和版本库一模一样的状态；另一种是文件已经添加到暂存区后，又作了修改，现在撤销修改的话就会回到添加到暂存区后的状态，总的来说就是让该文件回到最近一次`git	commit` 或 `git  add` 时的状态。

如果	`git checkout -- file`中的`--` 没有了，就变成了“切换到另一个分支”的命令。

如果文件修改后已经添加到了暂存区，但是需要撤销修改需要用到命令`git  reset  HEAD  <file> ` ,该命令可以把暂存区的修改撤销掉，重新放回到工作区。

## 删除文件

​			一般情况，直接在文件管理器中把没用的文件删了就好，或者用rm命令删除即可。

​			确定要从版本库中删除文件，那就用命令`git  rm` 删掉，并且`git  commit` ,如果是误删，可以使用`git  checkout  -- <file>` 把误删的文件恢复到最新版本，注意：从来没有被添加到版本库就被删除的文件是无法恢复的。

​			