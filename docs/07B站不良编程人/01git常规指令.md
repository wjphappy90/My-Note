```cmd
git init初始化

git status查看状态

git add . 将所有文件添加到暂存区进行跟踪

git commit -m "add two files" 提交文件到本地缓存区并进行提交日志登记，暂未提交到远程仓库

git remote add origin https://gitee.com/happy104314787/git_shine.git

git remote -v 

git push origin master   上传文件到远程仓库master分支

git pull origin master   录取最新的代码到本地，适合拉去别人的最新代码

下面是分支
git branch 查看当前使用的分支并且未使用的分支

git branch dev   创建dev分支

git checkout dev 切换分支

git log --oneline  查看提交记录，可以查看各个分支一系列的提交记录

git log

git merge   dev  在master分支下，将dev分支的内容合并到master分支。通俗说：将dev分支的内容复制到master分支

git checkout master 切换分支

git log --oneline --graph   分支的走势，冲突查看

gitee码云有个坑，如果换了gitee账号，你又拿新的账号去push等操作，会提示你没有权限。解决方法：windows10 - 开始
--凭据管理器  ，将关于码云的账号信息删掉，重新去操作就可以了。
```

