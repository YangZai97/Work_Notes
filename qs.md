# QS
#### `qs.parse()`将URL解析成对象的形式
```js
const Qs = require('qs');
let url = 'method=data_name&projectId=59&appToken=123456789qs-cs-dn';
let obj = Qs.parse(url)
console.log(obj)
// 控制台打印 obj
{
    method:'data_name',
    projectId:'59',
    appToken:'123456789qs-cs-dn'
}
```
#### `qs.stringify()`将对象 序列化成URL的形式，以&进行拼接
```js
const Qs = require('qs');
let obj = {
    method:'data_name',
    projectId:'59',
    appToken:'123456789qs-cs-dn'
}
let str = Qs.stringify(obj);
console.log(str)
// 控制台打印 str 
 method=data_name&projectId=59&appToken=123456789qs-cs-dn
```
#### 在这里需要注意的是，`JSON`中同样存在`stringify`方法，但是两者之间的区别是很明显的，如下所示：
```js
  JSON.stringify(param)
// {"uid":"cs11","pwd":"000000als","username":"cs11","password":"000000als"}
  Qs.stringify(param)
// uid=cs11&pwd=000000als&username=cs11&password=000000als
```

