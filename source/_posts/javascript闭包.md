---
title: javascript闭包
date: 2016-11-08 04:19:06
tags:
---
### javascript闭包
- 函数内部包含另一个函数及调用
- 函数被调用，内部的局部声明依然存在

```javascript
function a(num) {
  var b = 123 + Number(num);
  return function() {
    console.log('b is ' + b);
    console.log('call this function');
  }
}

var a2 = a(2);
a2();//125
var a3 = a(3);
a3();//126
```
