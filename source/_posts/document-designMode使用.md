---
title: document.designMode使用
date: 2016-10-16 21:00:53
tags:
---
### document.designMode使用
参考
《HTML5》实战 第三章 P77
contentDocument http://www.w3school.com.cn/jsref/prop_frame_contentdocument.asp
designMode https://developer.mozilla.org/en-US/docs/Web/API/Document/designMode
write() https://developer.mozilla.org/en-US/docs/Web/API/Document/write
demo http://jsbin.com/seholiqofu/edit?html,css,js,output

```html
<div id="test-one">
  <iframe id="show" frameborder="0"></iframe>
</div>

<div id="test-two">
  <textarea id="edit" cols="30" rows="10"></textarea>
</div>
```

```javascript
var show = document.getElementById('show'),
    edit = document.getElementById('edit'),
    showDoc = show.contentDocument;

showDoc.dsignMode = 'on';// 开启designMode

var update = function(content) {
  showDoc.open();
  showDoc.write(content);
  showDoc.close();
}

edit.addEventListener('keyup', function() {
  update(edit.value)
}, false)
```
