---
title: gulp使用
date: 2016-08-22 15:50:30
tags:
---
### gulp使用
- 配置
```javascript
// 'use strict';
// 引入 gulp
var gulp = require('gulp');
// 引入组件
var jshint = require('gulp-jshint'),
    sass = require('gulp-sass'),
    minifycss = require('gulp-minify-css'),
    concat = require('gulp-concat'),
    uglify = require('gulp-uglify'),
    rename = require('gulp-rename'),
    clean = require('gulp-clean'),
    livereload = require('gulp-livereload'),
    imagemin = require('gulp-imagemin'),
    cache = require('gulp-cache'),
    notify = require('gulp-notify'),
    plumber = require('gulp-plumber');

// 检查脚本
gulp.task('lint', function() {
  gulp.src('./src/scripts/*.js')
  .pipe(jshint())
  .pipe(jshint.reporter('default'));
});

// 编译Sass
gulp.task('styles', function() {
  gulp.src('./src/styles/layout.scss')
  .pipe(plumber({errorHandler: notify.onError('Error: <%= error.message %>')}))
  .pipe(sass())
  .pipe(gulp.dest('./dist/styles'))
  .pipe(rename({ suffix: '.min' }))
  .pipe(minifycss())
  .pipe(gulp.dest('dist/styles'));
});
// 监听sass文件变化
gulp.task('sass:watch', function () {
  gulp.watch('./src/styles/layout.scss', ['sass']);
});

// 合并，压缩文件
gulp.task('scripts', function() {
  gulp.src('./src/scripts/**/*.js')
  .pipe(plumber({errorHandler: notify.onError('Error: <%= error.message %>')}))
  .pipe(concat('all.js'))
  .pipe(gulp.dest('./dist/scripts'))
  .pipe(rename('all.min.js'))
  .pipe(uglify())
  .pipe(gulp.dest('./dist/scripts'));
});

// 图片
gulp.task('images', function() {
  return gulp.src('./src/images/**/*.{png,jpg,gif,ico}')
  .pipe(cache(imagemin({
    optimizationLevel: 3,
    progressive: true,
    interlaced: true
  })))
  .pipe(gulp.dest('dist/images'));
});

// 清理
gulp.task('clean', function() {
  return gulp.src(['dist/styles', 'dist/scripts', 'dist/images'], {read: false})
  .pipe(clean());
});

// 预设任务
gulp.task('default', ['clean'], function() {
  gulp.start('styles', 'scripts', 'images');
});

// 看守
gulp.task('watch', function() {
  livereload.listen();// 建立即时重整伺服器
  gulp.watch('src/styles/**/*.scss', ['styles']);// 看守所有.scss档
  gulp.watch('src/scripts/**/*.js', ['scripts']);// 看守所有.js档
  gulp.watch('src/images/**/*.{png,jpg,gif,ico}', ['images']);// 看守所有图片档
  gulp.watch(['dist/**']).on('change', function(file) {// 看守所有位在 dist/ 目录下的档案，一旦有更动，便进行重整
    livereload.changed(file.path);
  });
});
```
