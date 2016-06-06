#webpack笔记
###笔记Ⅰ
目标：

* 使页面标题为Hello World!

* 使页面内容为Hello World!

```
//文件结构  tree "catalog" /f >file.name
// package.json 和 webpack.config.js是配置文件，src为源文件目录，bulid为编译后生成的文件目录，node_modules为node包
C:\USERS\XXXXXX\WEBPACK
│  package.json
│  webpack.config.js
├─bulid
│      bundle.js
│      index.html
├─src
│      index.js
└─node_modules
       [...]
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
    //在本地启动一个web服务器
    devServer:{
        historyApiFallback:true,
        hot:true,
        inline:true,
        progress:true
    },
    plugins: [
        //给输出的文件头部添加注释信息
        new webpack.BannerPlugin('hellowtree'),
        //生成一个html文件来加载编译后的代码
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


###笔记Ⅱ
目标：

* 引入js文件

```
//文件结构，省略了node_modules文件夹
C:\USERS\XXXXXX\WEBPACK
│  package.json
│  webpack.config.js
├─bulid
│      bundle.js
│      index.html
└─src
       helloworld.js
       index.js
```
```
package.json 和 webpack.config.js文件内容不变
```
```
//helloworld.js
module.exports = function () {                //+
    var el = document.createElement("h1");    //+
    el.innerHTML = "Hello World!";            //+
    return el;                                //+
}                                             //+
```
```
//index.js
document.write("Hello World!");
var helloworld = require('./helloworld.js');  //+
document.body.appendChild(helloworld());      //+
```

###笔记Ⅲ
目标：

* 引入css文件

```
//文件结构，省略了node_modules文件夹
C:\USERS\XXXXXX\WEBPACK
│  package.json
│  webpack.config.js
├─bulid
│      bundle.js
│      index.html
└─src
       helloworld.css
       helloworld.js
       index.js
```
```
//package.json 增加的部分
"devDependencies": {
    "css-loader": "^0.23.1",
    "html-webpack-plugin": "^2.19.0",
    "style-loader": "^0.13.1",
    "webpack": "^1.13.1",
    "webpack-dev-server": "^1.14.1"
  }
```
```
//webpack.config.js 增加的部分
module:{
        loaders:[
            {
                test:/\.css$/,
                loaders:['style','css']
            }
        ]
    },
```
```
//helloworld.css
h1{
    color: red;
}
```
```
//helloworld.js 不变
```
```
//index.js 增加的部分
require('./helloworld.css');
```
