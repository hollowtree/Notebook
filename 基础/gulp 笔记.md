#gulp 笔记
###命令行
一些命令：
```
node -v
npm -v
cd
dir
mkdir
cls
```
###安装 gulp
安装命令：`npm install <name> [-g] [--save-dev]`
* <name>: node 插件名称。比如：`npm install gulp-less --save-dev`
* -g: 全局安装
* --save: 保存配置信息至package.json（nodejs项目配置文件）
* -dev: 保存至package.json的devDependencies节点，不指定-dev将保存至dependencies节点
卸载命令：`npm uninstall <name> [-g] [--save-dev]`
更新命令：`npm update <name> [-g] [--save-dev]`
       或 `npm update [--save-dev]`
查看帮助：`npm help`
查看已安装插件：`npm list`

###使用淘宝npm镜像
`npm install cnpm -g --registry=https://registry.npm.taobao.org`
###安装gulp
`cnpm install gulp -g`
###新建package.json文件
```
cnpm init
cnpm help package.json

{
  "name": "test",
  "version": "1.0.0",
  "description": "",
  "main": "gulpfile.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "hollowtree",
  "license": "ISC"
}
```
###安装插件
```
cnpm install --save-dev
cnpm install gulp-less --save-dev
cnpm install gulp-stylus --save-dev
cnpm install gulp --save-dev
```
###新建gulpfile.js文件
监视指定目录中的less、styl文件，一旦发生变化即时编译成css文件。
```
'use strict';

var gulp = require('gulp'),
    less = require('gulp-less'),
    styl=require('gulp-stylus');

gulp.task('buildLess',function(){
    gulp.src('src/less/*.less')
        .pipe(less())
        .pipe(gulp.dest('src/css'));
});

gulp.task('watchLess',function(){
    gulp.watch('src/less/*.less',['buildLess']);
});

gulp.task('buildStyl',function(){
    gulp.src('src/styl/*.styl')
        .pipe(styl())
        .pipe(gulp.dest('src/css'));
});

gulp.task('watchStyl',function(){
    gulp.watch('src/styl/*.styl',['buildStyl']);
});

gulp.task('default',['watchLess','watchStyl']);
```
###运行gulp任务
`gulp default`
