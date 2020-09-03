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
# Vue
## style
Vue组件中，在style设置为scoped的时候，里面在写样式对子组件是不生效的，如果想让某些样式对所以子组件都生效，可以使用 /deep/ 深度选择器，只给父类加即可。
Firfox中失效

```css
/deep/ .class1{
	font-size:14px;
}
```
## methods 、 computed、watch区别
computed是基于响应式依赖进行缓存的。何为响应式依赖呢？例如声明在data中的变量既有响应式的性质，用通俗一点的话讲就是，计算属性的触发条件是他的依赖变化了才会重新执行。例如上面的列子一样，只有data中定义的message发生变化了，计算属性才会执行，而且最终返回的事一个结果。<br> <br>
而methods就像我们写的普通函数一样，需要我们主动去调用才会执行。而不是依赖数据的变换，并且也不需要返回一个结果，可以仅仅执行一个过程。当我们在获取一个数据时需要对一个大的数组进行大量循环才能获取时，那我们选择计算属性，基于依赖进行缓存那将会节省大量的性能消耗。而不是像methods一样每次调用都执行。<br><br>
watch适合处理的场景是，侦听一个数的变化，当该数据变化，来处理其他与之相关数据的变化（该数据影响别的多个数据）<br><br>
computed适合处理的场景是，获得一个值或者结果，该结果受其他的依赖的影响。（一个数据受多个数据影响）<br><br>
methods用的是也是最多的，一般的事件绑定，普通函数，请求数据方法都是在methods中处理。然后vue的生命周期函数就是在相应的或者合适的时机调用这些定义好的函数

## 监听-watch
```js
// 下拉选择菜单的props是status
  data(){
      return {
          addObj:{
          	status:0,
          }
      }
  }
  // 监听下拉选择菜单值的改变
  watch: {
    "addObj.status": {
      handler(val) {
        if (val === 0) {
          this.addObj.status = "审核";
        }
        if (val === 1) {
          this.addObj.status = "待审核";
        }
        if (val === 2) {
          this.addObj.status = "黑名单";
        }
        if (val === 3) {
          this.addObj.status = "注销";
        }
      },
    },
    immediate: true,
    deep: true,
  },
```
## @click
```
1. @click="fn"		// 普通
2. @click.stop="fn"		// 阻止事件冒泡
3. @click.prevent="fn"		// 阻止事件的默认行为
```
## Vue中动态生成二维码
### 安装引入
```
npm install qrcodejs2 --save
import QRCode from 'qrcodejs2';
```
### 使用

HTML代码：

```vue
<div class="Qrcode_wrap">
    <el-popover ref="popover" placement="bottom" width="200" trigger="click">
        <div>
            <p>二维码信息</p>
            <p>code:abcdefghijklmnopqrstuvwxyz</p>
            <div id="qrcode"></div>
        </div>
    </el-popover>
    <el-tag v-popover:popover @click.stop="handleQrcode('abcdefghijklmnopqrstuvwxyz')">二维码信息</el-tag>
</div>
```

JS代码：

```js
handleQrcode(codeText) {
      document.getElementById("qrcode").innerHTML = "";
      new QRCode(document.getElementById("qrcode"), {
        text: codeText,
        width: 128,
        height: 128,
        colorDark: "#000000",
        colorLight: "#ffffff",
        correctLevel: QRCode.CorrectLevel.H,
      });
    },
```
## 表格的导入导出
依赖安装
```
cnpm install -S file-saver xlsx
cnpm install -D script-loader
```
新建文件夹,需要依赖两个js文件
```
src
	vendor
		Blob.js
		Export2Excel.js
```
### 导入表格
HTML部分
```html
 <!-- 导入 dialog -->
 <el-button
 class="export_export_btn light_btn menu_btn menu_btn_2"
 size="small"
 plain
 @click.stop="importExcel"
>导入</el-button>
        <div class="import_excel_wrap">
          <el-dialog
            title="导入访客数据"
            :visible.sync="dialogVisible"
            width="500px"
            :before-close="handleClose"
          >
            <el-upload
              action
              :on-change="handleChange"
              :show-file-list="true"
              :on-remove="handleRemove"
              :file-list="fileListUpload"
              :limit="limitUpload"
              accept=".csv, application/vnd.openxmlformats-officedocument.spreadsheetml.sheet, application/vnd.ms-excel"
              :auto-upload="false"
            >
              <div class="content_item select_btn">
                <i class="el-icon-plus"></i>
              </div>
            </el-upload>
            <div class="content_item content_item2">
              <el-checkbox v-model="checked">是否更新已经存在的访客数据</el-checkbox>
              <el-button class="upload_demo_btn" size="mini">下载模板</el-button>
            </div>
            <div class="tip_text content_item">提示：仅允许导入"xls"或"xlsx"格式文件!</div>
            <span slot="footer" class="dialog-footer">
              <el-button class="footer_btn" type="primary" @click="dialogVisible = false">确 定</el-button>
              <el-button class="footer_btn" @click="dialogVisible = false">取 消</el-button>
            </span>
          </el-dialog>
        </div>
```
js部分
```js
data(){
    return {
    fileListUpload: [],
        limitUpload: 1,
        disabled: false,
        accountList: [],
        checked: false, //导入模块
        dialogVisible: false,
    }
}

// 表格导入-menu
    importExcel() {
      this.dialogVisible = true;
    },
    // excel表上传
    handleChange(file, fileList) {
      this.fileTemp = file.raw;
      let fileName = file.raw.name;
      let fileType = fileName.substring(fileName.lastIndexOf(".") + 1);
      // 判断上传文件格式
      if (this.fileTemp) {
        if (fileType == "xlsx" || fileType == "xls") {
          this.importf(this.fileTemp);
        } else {
          this.$message({
            type: "warning",
            message: "附件格式错误，请删除后重新上传！",
          });
        }
      } else {
        this.$message({
          type: "warning",
          message: "请上传附件！",
        });
      }
    },
    //导入的方法
    importf(obj) {
      this.dialogVisible = true;
      let _this = this;
      let inputDOM = this.$refs.inputer; // 通过DOM取文件数据
      this.file = event.currentTarget.files[0];
      var rABS = false; //是否将文件读取为二进制字符串
      var f = this.file;
      var reader = new FileReader();
      //if (!FileReader.prototype.readAsBinaryString) {
      FileReader.prototype.readAsBinaryString = function (f) {
        var binary = "";
        var rABS = false; //是否将文件读取为二进制字符串
        var pt = this;
        var wb; //读取完成的数据
        var outdata;
        var reader = new FileReader();
        reader.onload = function (e) {
          var bytes = new Uint8Array(reader.result);
          var length = bytes.byteLength;
          for (var i = 0; i < length; i++) {
            binary += String.fromCharCode(bytes[i]);
          }
          var XLSX = require("xlsx");
          if (rABS) {
            wb = XLSX.read(btoa(fixdata(binary)), {
              //手动转化
              type: "base64",
            });
          } else {
            wb = XLSX.read(binary, {
              type: "binary",
            });
          }
          // outdata就是 excel导入的数据
          outdata = XLSX.utils.sheet_to_json(wb.Sheets[wb.SheetNames[0]]);
          console.log(outdata);
          // excel 数据再处理
          let arr = [];
          outdata.map((v) => {
            // let jsonString = JSON.stringify(v).replace(/\*/g, '').replace(/\s/ig,'');
            let jsonString = JSON.stringify(v)
              .replace(/\//g, "")
              .replace(/\s/gi, "");
            // debugger;
            console.log(jsonString);
            v = JSON.parse(jsonString);
            let obj = {};
            //xxx代表列名
            obj.riskType = v.xxx;
            obj.riskDescription = v.xxx;
            obj.typeAccident = v.xxx;
            obj.riskLevel = v.xxx;
            obj.controlMeasures = v.xxx;
            obj.hierarchyManage = v.xxx;
            obj.orgLiableDict = v.xxx;
            obj.personLiableDict = v.xxx;
            // obj.id = v.id
            arr.push(obj);
          });
          _this.accountList = [...arr];
        };
        reader.readAsArrayBuffer(f);
      };
      if (rABS) {
        reader.readAsArrayBuffer(f);
      } else {
        reader.readAsBinaryString(f);
      }
    },
    handleClose(done) {
    	this.dialogVisible = false;
    },
    // 移除excel表
    handleRemove(file, fileList) {
   		this.fileTemp = null;
    },
```
### 导出表格
HTML部分
```html
<el-button
class="export_export_btn light_btn menu_btn menu_btn_2"
size="small"
plain
@click.stop="exportToExcel"
>导出2</el-button>
```
JS部分
```js
formatJson(filterVal, jsonData) {
	return jsonData.map((v) => filterVal.map((j) => v[j]));
},
//点击导出按钮
exportToExcel() {
    let tHeaderArr = [];
    let filterValArr = [];
    this.tableOption.column.map((v, index) => {
        if (!v.editDisabled) {
            tHeaderArr.push(v.label);
            filterValArr.push(v.prop);
        }
    });
    require.ensure([], () => {
        const { export_json_to_excel } = require("@/vendor/Export2Excel");
        const tHeader = tHeaderArr;
        const filterVal = filterValArr;
        const list = this.tableData;
        const data = this.formatJson(filterVal, list);
        export_json_to_excel(tHeader, data, "访客信息");
    });
},
```
### 下载模板
```js
    // 下载Excel模板
    outExe() {
      let tHeaderArr = [];
      this.tableOption.column.map((v, index) => {
        if (!v.editDisabled) {
          tHeaderArr.push(v.label);
        }
      });
      require.ensure([], () => {
        const { export_json_to_excel } = require("@/vendor/Export2Excel"); //引入文件
        const tHeader = tHeaderArr; //将对应的属性名转换成中文
        const data = [];
        export_json_to_excel(tHeader, data, "访客信息模板");
      });
    },
```

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
注意：页面刷新后，传递的参数会失效。

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