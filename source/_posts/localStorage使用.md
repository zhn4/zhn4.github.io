---
title: localStorage使用
date: 2016-09-01 18:19:28
tags:
---
### localStorage使用

使用localStorage储存数据，储存的数据是字符串string，需要把字符串转换成json数据方便读取

参考
- https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify#JSON.stringify用作_JavaScript

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <h3>localStorage使用</h3>
  <div class="list">
    <div class="value value" data-id="1">黑名单</div>
    <div class="value value" data-id="2">怪奇物语</div>
    <div class="value value" data-id="3">行尸走肉</div>
  </div>

  <a href="javascript:;" id="clean">清除localStorage数据</a>

  <style>
    .list {
      border: 1px solid skyblue;
      padding: 0 10px;
    }
    .value {
      border: 1px solid tomato;
      margin: 20px 0;
      background-color: tomato;
    }
  </style>

</body>
</html>
```

```javascript
document.getElementById('clean').addEventListener('click', function() {
  console.log('清除localStorage数据');
  localStorage.clear(); //清除localStroage
});

var value = document.getElementsByClassName('value');
var movies = {
  movie: []
};

for(var i = 0; i < value.length; i++) {
  value[i].addEventListener('click', function() {
    console.log(this.dataset['id']);
    console.log(this.innerHTML);
    movies.movie.push({
      id: this.dataset['id'],
      name: this.innerHTML
    })
    localStorage.setItem('movies', JSON.stringify(movies));// 使用JSON.stringify()字符串化数据
  })
}

console.log(localStorage);// 原始localStroage数据
console.log('----');
console.log(JSON.parse(localStorage.getItem('movies')));// 使用JSON.parse()解析成json数据
```
