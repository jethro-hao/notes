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
## 提交脚本
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