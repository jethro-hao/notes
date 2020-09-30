# GIT


## 基本命令
```
配置用户名：git config --global user.name "xxx" 
配置用户邮箱：git config --global user.email "xxx" 
查看配置：git config --list

创建初始化本地仓库： git init
克隆远程代码：git clone 仓库地址
拉取更新：git pull
推送：git push

查看状态：git status
查看文件修改内容：git diff 文件名
查看历史：git log --pretty=oneline

查看操作记录：git reflog
根据操作记录回退：git reset --hard 版本号

创建文件夹：mkdir
创建文件 touch
查看当前文件路径：pwd
```

## 合并到主分支
```
git checkout master
git pull
git merge 分支名 --allow-unrelated-histories
git add .
git commit -m "commit"
git push
```
## 上传到新建分支
```
新建分支：git branch 分支名
切换分支：git checkout 分支名
目录上传 
    git add .
    git commit -m "提交信息"
    git remote remove origin
    git remote add origin 远程仓库地址
    git push -u origin 分支名 

```
## 其他

```
查看本地分支：git branch
查看远程分支：git branch -r
查看所有分支：git branch -a

VsCode 同步 远程的分支：git fetch --prune

删除本地分支：git branch -d 分支名 
强制删除本地分支：git branch -D 分支名

删除远程分支：git push origin --delete 分支名

```