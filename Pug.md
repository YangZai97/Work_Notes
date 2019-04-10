# Pug (Jade)  
### 介绍
- Pug(Jade) —— 源于 Node.js 的 HTML 模板引擎
### 安装
#### Pug 可以通过 npm 获得:    
- ` $ npm install pug `
- 安装pug命令行工具`pug-cli`
     * 注意:一定要全局安装`pug-cli`，否则无法正常编译
     * `npm install  pug-cli -g`

### 入门文档 
- [Github文档](https://github.com/pugjs/pug)
- [官方中文文档](https://pug.bootcss.com/api/getting-started.html)

### 转换
#### 这里有一个传统html和Pug可相互转换的工具：     
- [转换工具](https://html2jade.org/)

### 基础编译例子
```js
// pug
doctype html
html(lang='en')
  head
    title Jade
    script(type='text/javascript').
      const foo = true;
      let bar = function() {};
      if (foo) {
      bar(1 + 5)
      }
  body
    h1 Jade - node template engine
    ul
      li Item A
      li Item B
      li Item C
    #container.col
      p You are amazing
      p
        | Jade is a terse and simple
        | templating language with a
        | strong focus on performancej
        | and powerful features.

```
```js 
// html
<!DOCTYPE html>
<html lang="en">

<head>
  <title>Jade</title>
  <script type="text/javascript">
    const foo = true;
    let bar = function() {};
    if (foo) {
      bar(1 + 5)
    }
  </script>
</head>

<body>
  <h1>Jade - node template engine</h1>
  <ul>
    <li>Item A</li>
    <li>Item B</li>
    <li>Item C</li>
  </ul>
  <div class="col" id="container">
    <p>You are amazing</p>
    <p>
      Jade is a terse and simple
      templating language with a
      strong focus on performance
      and powerful features.
    </p>
  </div>
</body>

</html>
```