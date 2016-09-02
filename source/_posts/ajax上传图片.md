---
title: ajax上传图片
date: 2016-07-25 14:47:42
tags:
---
### ajax上传图片
接到一个用户反馈的页面，其中要求用户能够上传图片且多图，不使用多图上传的插件情况下思路如下：
* 监听input[type="file"]的change事件上传图片，图片上传成功后返回图片的转存地址，再生产预览图
* 用户提交表单反馈时候遍历预览图中的图片转存地址，用','作拼接符（后台要求）

之前没接触过ajax独立上传图片，记录一下方法

Demo：http://jsbin.com/kupaquhalu/edit?html,js,console,output

```html
<form action="#">
  <input type="file" id="image">
  <input type="submit">
</form>
```

```javascript
var image = document.getElementById('image');
image.addEventListener('change', function() {
  var image_file = this.files[0]; // 获取图片文件对象
  var image_data = new FormData(); // 新建表单数据
  image_data.append('image', image_file); // 使用append方法添加字段
  $.ajax({
    url: 'api/upload_address',
    method: 'post',
    dataType: 'json',
    cache: false, // 上传文件不需要缓存。
    processData: false, // 因为data值是FormData对象，不需要对数据做处理。
    contentType: false, // 因为是由<form>表单构造的FormData对象，且已经声明了属性enctype="multipart/form-data"，所以这里设置为false。
    data: image_data,
    success: function(data) {
      console.log('success');
      console.log(data);
    },
    error: function(data) {
      console.log('error');
      console.log(data);
    }
  });
});
```
