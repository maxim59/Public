# github连接远程库教程

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

​		第四步：如果git push -u origin master	提交不了，可以试一下 git push