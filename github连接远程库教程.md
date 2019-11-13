# github连接远程库教程

​		第一步：首先在本地创建一个版本库

​						具体步骤：1> 创建一个空目录 mkdir  <filename>											   2>进入该目录 cd <filename>											   3>pwd  显示当前目录

​		第二步：把目录变成git可以管理的仓库 ---------> git init

​		第三步：编写一个文件并放到所创建的目录下面

​		第四步：在Github上创建一个Git仓库

​		第五步：使用	`git  add`  把文件添加到仓库

​	    第六步：克隆远程仓库到本地仓库并且进入到远程仓库

​		第七步：使用	`git commit` 把文件提交到仓库

​		第八步：本地仓库与远程仓库进行关联----------> git remote add origin `git@github.com:username(自己github的用户名)/learngit.git` (远程仓库的密钥)

​		第九步：把本地库的所有内容推送到远程库上-------->git push -u origin master