---
title: javascript数组去重
date: 2016-11-15 22:18:24
tags:
---
### javascript数组去重
关于数组去重问题

参考：https://github.com/lifesinger/blog/issues/113
demo：http://jsbin.com/diwifareya/edit?html,js,console,output
indexOf：http://www.w3school.com.cn/jsref/jsref_indexOf.asp

```javascript
function test(a) {
  var arr = [];//建立空数组，去重后的容器
  for(var i = 0; i < a.length; i++) {
    if(arr.indexOf(num[i]) === -1) {//利用indexOf判断arr数组是否重复
      arr.push(num[i]);//推入arr数组
    }
  }
  console.log(arr);
}

test(num)
```
