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
# 小功能
## 随机字符串
1. 数字+字母
```js
randomstring(L) {
    // 使用方法
    // randomstring(6)
    var s = "";
    var randomchar = function () {
        var n = Math.floor(Math.random() * 62);
        if (n < 10) return n; //1-10
        if (n < 36) return String.fromCharCode(n + 55); //A-Z
        return String.fromCharCode(n + 61); //a-z
    };
    while (s.length < L) s += randomchar();
    return s;
},
```
2. 支持自定义
```js
randomString(len, charSet) {
    // 使用方法
    // randomString(5);
    // randomString(5, 'PICKCHARSFROMTHISSET');
    charSet =
    charSet ||
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
    var randomString = "";
    for (var i = 0; i < len; i++) {
        var randomPoz = Math.floor(Math.random() * charSet.length);
        randomString += charSet.substring(randomPoz, randomPoz + 1);
    }
    return randomString;
},
```
## UUID
vue 中使用UUID
1. 安装
```
npm install uuid
```
2. 导入
```
import { v4 as uuidv4 } from 'uuid';
```
3. 使用
```
uuidv4(); // ⇨ '9b1deb4d-3b7d-4bad-9bdd-2b0d7b3dcb6d'
```
4. 使用 CommonJS 语法：
```
const { v4: uuidv4 } = require('uuid');

uuidv4(); // ⇨ '1b9d6bcd-bbfd-4b2d-9b5d-ab8dfbbd4bed'
```

## 取整、取余、保留两位小数
### 取整
1. 取整
```
//丢弃小数部分，保留整数
parseInt(5/2)        //2
```
2. 向上取整
```
//向上取整
Math.ceil(5/2)          //3
```
3. 向下取整
```
//向下取整
Math.floor(5/2)              //2
```
4. 四舍五入
```
//四舍五入
Math.round(5/2)         //3
```
### 取余
```
//取余
6%4                   //2
```
### 保留两位小数
1. 四舍五入
```
var num = 3.145592653;
num = num.toFixed(2);             //3.15
```
2. 不四舍五入
```
Math.floor(15.7784514000 * 100) / 100               //输出结果为 15.77
```
## 格式化日期
```js
/**
* 日期格式化
*/
function dateFormat(date) {
    let format = 'yyyy-MM-dd hh:mm:ss'
    if (date !== 'Invalid Date') {
        var o = {
            'M+': date.getMonth() + 1, // month
            'd+': date.getDate(), // day
            'h+': date.getHours(), // hour
            'm+': date.getMinutes(), // minute
            's+': date.getSeconds(), // second
            'q+': Math.floor((date.getMonth() + 3) / 3), // quarter
            'S': date.getMilliseconds() // millisecond
        }
        if (/(y+)/.test(format)) {
            format = format.replace(RegExp.$1,
                                    (date.getFullYear() + '').substr(4 - RegExp.$1.length))
        }
        for (var k in o) {
            if (new RegExp('(' + k + ')').test(format)) {
                format = format.replace(RegExp.$1,
                                        RegExp.$1.length === 1 ? o[k] :
                                        ('00' + o[k]).substr(('' + o[k]).length))
            }
        }
        return format
    }
    return ''
}
console.log(dateFormat(new Date()))
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