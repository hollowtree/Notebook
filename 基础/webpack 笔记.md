#webpack笔记
###笔记Ⅰ
目标：
1. 使页面标题为Hello World!
1. 使页面内容为Hello World!
```
//文件结构  tree "catalog" /f >file.name
// package.json 和 webpack.config.js是配置文件，src为源文件目录，bulid为编译后生成的文件目录
C:\USERS\XXXXXX\WEBPACK
│  package.json
│  webpack.config.js
│
├─bulid
│      bundle.js
│      index.html
│
└─src
       index.js
```
```
//package.json
{
  "name": "test",
  "version": "1.0.0",
  "description": "",
  "main": "webpack.config.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "webpack-dev-server --hot --inline"
  },
  "author": "hollowtree",
  "license": "ISC",
  "devDependencies": {
    "html-webpack-plugin": "^2.19.0",
    "webpack": "^1.13.1",
    "webpack-dev-server": "^1.14.1"
  }
}
```
```
//webpack.config.js
'use strict';
var webpack = require('webpack');
var HtmlWebpackPlugin = require('html-webpack-plugin');
module.exports = {
    entry: './src/index.js',
    output: {
        path: './bulid',
        filename:'bundle.js'
    },
    devServer:{
        historyApiFallback:true,
        hot:true,
        inline:true,
        progress:true
    },
    plugins: [
        //给输出的文件头部添加注释信息
        new webpack.BannerPlugin('wjs'),
        new HtmlWebpackPlugin({
            title:'Hello world!'
        })
    ]
}
```
```
//index.js
document.write("Hello World!");
```
配置完成后输入`webpack`、`cnpm start`后，即可在`http://localhost:8080/`查看到页面了
