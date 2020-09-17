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
VsCode 同步 远程的分支
```
git fetch --prune
```

# MySQL

## 查询
```
SELECT * FROM 表名 
SELECT * FROM 表名 WHERE 字段名="某值"	
SELECT * FROM 表名 WHERE 字段名="某值" AND 字段名="某值"
SELECT * FROM 表名 WHERE 字段名="某值" OR 字段名="某值"
SELECT * FROM 表名 WHERE 字段名 LIKE '%关键字%' 		//关键字左右两边任意个字符
SELECT * FROM 表名 WHERE 字段名 LIKE '\_关键字\__' 	//关键字左边一个字符，右边两个字符
注意：\* 为返回全部数据，\* 可以换成字段名
```
## 删除
```
DELETE FROM 表名 WHERE 字段名="某值"
```
## 插入
```
INSERT INTO 表名 VALUES (值1,值2,值3.....)
INSERT INTO 表名 (列1, 列2,...) VALUES (值1, 值2,....)
```
## 修改
```
UPDATE 表名称 SET 列名称=新值 WHERE 列名称 = 某值
UPDATE 表名称 SET 列名称=新值,列名称=新值,列名称=新值.... WHERE 列名称 = 某值
```
# ES6
### Object.keys()
Object.keys() 方法会返回一个由一个给定对象的自身可枚举属性组成的数组，数组中属性名的排列顺序和正常循环遍历该对象时返回的顺序一致 。
```js
let person = {
  name: "tom",
  sex: "1",
  age: 18,
};
const obj = Object.keys(person);
console.log(obj);//["name", "sex", "age"]
```
### export import
```js
//全部导入
import people from './example'

//有一种特殊情况，即允许你将整个模块当作单一对象进行导入
//该模块的所有导出都会作为对象的属性存在
import * as example from "./example.js"
console.log(example.name)
console.log(example.age)
console.log(example.getName())

//导入部分
import {name, age} from './example'

// 导出默认, 有且只有一个默认
export default App

// 部分导出
export class App extend Component {};
```
大括号
```js
1.当用export default people导出时，就用 import people 导入（不带大括号）

2.一个文件里，有且只能有一个export default。但可以有多个export。

3.当用export name 时，就用import { name }导入（记得带上大括号）

4.当一个文件里，既有一个export default people, 又有多个export name 或者 export age时，导入就用 import people, { name, age } 

5.当一个文件里出现n多个 export 导出很多模块，导入时除了一个一个导入，也可以用import * as example
```



# 脚本
git 提交命令脚本，文件后缀 .sh
```
cd /e/code/notes
unset msg
read -p "请输入commit提交的描述: " msg
git add -A
git commit -m $msg
git push
git status
```

# swiper
## 安装引入
### 1. 安装
```
npm install swiper vue-awesome-swiper --save
```
### 2. 引入
```js
//swiper
import VueAwesomeSwiper from 'vue-awesome-swiper'
// If you use Swiper 6.0.0 or higher
import 'swiper/swiper-bundle.css'
import Swiper2, {
  Navigation, //前进后退
  Pagination, //分页器
  Autoplay, //自动切换
} from 'swiper'
Swiper2.use([Navigation, Pagination, Autoplay])
Vue.use(VueAwesomeSwiper, /* { default options with global component } */ )
```
### 3. 使用
HTML部分
```html
<template>
  <div class="wrap wrap_login">
    <swiper ref="mySwiper" :options="swiperOptions">
      <swiper-slide class="bac1">Slide 1</swiper-slide>
      <swiper-slide class="bac2">Slide 2</swiper-slide>
      <swiper-slide class="bac3">Slide 3</swiper-slide>
      <swiper-slide class="bac4">Slide 4</swiper-slide>
      <swiper-slide class="bac5">Slide 5</swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
  </div>
</template>
```
js部分
```js
//data里边
swiperOptions: {
    pagination: {
        el: ".swiper-pagination",
        clickable: true,
    },
    navigation: {
        nextEl: ".swiper-button-next",
        prevEl: ".swiper-button-prev",
    },
    loop: true,
    autoplay: {
        delay: 3000,
        stopOnLastSlide: false,
        disableOnInteraction: true,
    },
},
```