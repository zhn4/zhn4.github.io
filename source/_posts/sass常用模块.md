---
title: sass常用模块
date: 2016-07-26 16:08:03
tags:
---
### sass常用模块
图片适配retina屏幕
```sass
@mixin image_2x($image, $type) {
  background-image: url($image + "." + $type);
  @media (min--moz-device-pixel-ratio: 1.3),
  (-o-min-device-pixel-ratio: 2.6/2),
  (-webkit-min-device-pixel-ratio: 1.3),
  (min-device-pixel-ratio: 1.3),
  (min-resolution: 1.3dppx) {
    /* on retina, use image that's scaled by 2 */
    background-image: url($image + "@2x." + $type);
  }
}
```
