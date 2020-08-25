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

# Vue
## methods 和 computed区别
computed是基于响应式依赖进行缓存的。何为响应式依赖呢？例如声明在data中的变量既有响应式的性质，用通俗一点的话讲就是，计算属性的触发条件是他的依赖变化了才会重新执行。例如上面的列子一样，只有data中定义的message发生变化了，计算属性才会执行，而且最终返回的事一个结果。<br>
而methods就像我们写的普通函数一样，需要我们主动去调用才会执行。而不是依赖数据的变换，并且也不需要返回一个结果，可以仅仅执行一个过程。当我们在获取一个数据时需要对一个大的数组进行大量循环才能获取时，那我们选择计算属性，基于依赖进行缓存那将会节省大量的性能消耗。而不是像methods一样每次调用都执行。

## @click
1. @click="fn"		// 普通
2. @click.stop="fn"		// 阻止事件冒泡
3. @click.prevent="fn"		// 阻止事件的默认行为

# Vue Router
## 路径参数
1. 在路由中设置参数
```js
{
    path: '/detail/:id/',
    name: 'detail',
    component: detail,
    meta: {
        title: '详情'
    }
}
```
2. 使用传参
```html
<router-link to="/detail/2"></router-link>
```
3. 获取参数
```js
// 第一种
const User = {
  template: '<div>User {{ $route.params.id }}</div>'
}
// 第二种
let id = this.$route.params.id
console.log(id) // 2
```

## 跳转路由并传参
不用改变路由配置，直接执行 js 语句即可。<br><br>
地址栏不会显示传递的参数<br>

```js
// 路由配置

{
    path: 'register',
    name: '访客预约',
    component: () =>
    import('@/views/axiom/visitor/register'),
},

// 点击后跳转路由并传参(任意类型参数)

toRegister() {
    this.$router.push({
    name: "访客预约",
    params: { msg: "duan", msg2: "123" },
    }); // 只能用 name
},

// js接收

let msg = this.$route.params.msg

// html接收 

{{ $route.params.msg }}
```

