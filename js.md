## filter、map、forEach
```js
var arr = [0,1,2,3];

var newArr = arr.filter(val => val > 0);

var newArr2 = arr.map(val => val > 0);

var newArr3 = arr.forEach(val => val > 0);

console.log(newArr);//[1,2,3]

console.log(newArr2);//false,true,true,true

console.log(newArr3);//undefined

```
共同点：都会遍历数组<br>
不同点：
1. filter，按照条件过滤，得到一个新数组。
2. map，将调用函数返回的布尔值结果存到一个新数组里边。
3. forEach，只是遍历，不会影响原数组，也不会得到新的数组。