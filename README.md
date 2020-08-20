# GIT
## 初次使用git

* 配置用户名：git config --global user.name "xxx" 
* 配置用户邮箱：git config --global user.email "xxx" 
* 查看配置：git config --list
* 新建分支：git branch 分支名
* 切换分支：git checkout 分支名
* 目录上传 
    git add .
    git commit -m "提交信息"
    git remote remove origin
    git remote add origin 远程仓库地址
    git push -u origin 分支名 
* 查看操作记录：git reflog
* 根据操作记录回退：git reset --hard 版本号

## 基本命令
* 克隆远程代码：git clone 仓库地址
* 拉取更新：git pull
* 推送：git push
* 创建初始化本地仓库： git init
* 查看状态：git status
* 查看文件修改内容：git diff 文件名
* 查看历史：git log --pretty=oneline
* 历史回退：git reset --hard HEAD
* 查看 操作记录的 版本号：git reflog
* 根据 操作记录 版本号 回退：git reset --hard 版本号
* 创建分支：git branch 分支名称
* 切换分支：git checkout 分支名称
* 创建文件夹：mkdir
* 创建文件 touch
* 查看当前文件路径：pwd
## 合并分支
* git checkout master
* git pull
* git merge 分支名 --allow-unrelated-histories
* git add .
* git commit -m "commit"
* git push

# MySQL

## 查询
SELECT * FROM 表名 <br> <br>
SELECT * FROM 表名 WHERE 字段名="某值"	<br> <br>
SELECT * FROM 表名 WHERE 字段名="某值" AND 字段名="某值"<br> <br>
SELECT * FROM 表名 WHERE 字段名="某值" OR 字段名="某值"<br> <br>
SELECT * FROM 表名  WHERE 字段名 LIKE '%关键字%' 	<br>
(关键字左右两边任意个字符) <br> <br>
SELECT * FROM 表名  WHERE 字段名 LIKE '\_关键字\__' 	<br>
(关键字左边一个字符，右边两个字符)<br> <br>

注意：\* 为返回全部数据，\* 可以换成字段名<br>

## 删除
DELETE FROM 表名 WHERE 字段名="某值"<br> <br>
## 插入
INSERT INTO 表名 VALUES (值1,值2,值3.....)<br> <br>
INSERT INTO 表名 (列1, 列2,...) VALUES (值1, 值2,....)<br> <br>

## 修改
UPDATE 表名称 SET 列名称=新值 WHERE 列名称 = 某值<br> <br>
UPDATE 表名称 SET 列名称=新值,列名称=新值,列名称=新值.... WHERE 列名称 = 某值<br> <br>