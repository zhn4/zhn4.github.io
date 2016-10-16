---
title: FileReader使用
date: 2016-09-01 10:10:08
tags:
---
### FileReader使用
读取上传图片，返回预览图

监听input[type="filt"]的change事件，使用FileReader接口，readAsDataURL()方法读取图片信息

参考
- http://www.javascripture.com/FileReader
- https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader#readAsDataURL()

Demo
- http://jsbin.com/xukinisege/edit?html,js,console,output

```html
<form action="#">
  <input type="file" id="file-image">
</form>

<img src="" alt="" id="show-image" />
```

```javascript
var file_image = document.getElementById('file-image');
file_image.addEventListener('change', function() {
  console.log('listening');
  var file_reader = new FileReader();
  file_reader.addEventListener('load', function() {
    console.log(this.result);
    var show_image = document.getElementById('show-image');
    show_image.src = this.result;
  });
  file_reader.readAsDataURL(this.files[0]);
});
```
