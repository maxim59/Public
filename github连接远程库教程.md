# github连接远程库教程

方案一：

​		第一步：在Github上创建一个Git仓库

​	    第二步：克隆远程仓库到本地并且进入到仓库

​		第三步：按照远程仓库的提示进行

```
echo "# dongqing" >> 
README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:maxim59/dongqing.git
git push -u origin master
```

​		第四步：或者直接使用git push 进行提交





方案二：

​			第一步：现在GitHub上新建一个远程仓库，同时在本地上见一个与之对应的目录（仓库名最好相同）

​			第二步：进入目录并将其初始化，

```
		cd 	目录名
		git init   初始化
```

​			第三步：将文件添加到暂存区

​									git add  文件名(加后缀)

​			第四步：将文件提交到仓库

​									git  commit -m "提交说明"

​			第五步：将本地仓库和远程仓库进行关联

​								git remote add origin git@github.com:michaelliao/learngit.git

​									git@github.com:michaelliao/learngit.git为远程仓库的密钥

​									michaeliao  Github 用户名

​									learngit	远程仓库名，后必须根 `.git`

​			第六步：把本地库的内容推送到远程库上

​								git push -u origin master  或者 git push

​									