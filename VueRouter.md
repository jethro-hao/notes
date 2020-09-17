# Vue Router
## 路径参数1
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
2. 传参
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

## 路径参数2
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