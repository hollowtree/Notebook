## 笔记

###VS code debug
```
//.vscode/launch.json
{
    "version": "0.2.0",
    "configurations": [{
        "name": "Launch",
        "type": "node",
        "request": "launch",
        "program": "${workspaceRoot}/app.js",
        "stopOnEntry": false,
        "args": [],
        "cwd": "${workspaceRoot}",
        "preLaunchTask": null,
        "runtimeExecutable": null,
        "runtimeArgs": [
            "--nolazy"
        ],
        "env": {
            "NODE_ENV": "development"
        },
        "externalConsole": false,
        "sourceMaps": false,
        "outDir": null
    }, {
        "name": "Attach",
        "type": "node",
        "request": "attach",
        "port": 5858,
        "address": "localhost",
        "restart": false,
        "sourceMaps": false,
        "outDir": null,
        "localRoot": "${workspaceRoot}",
        "remoteRoot": null
    }]
}
```
```
//jsconfig.json
{
    // See https://go.microsoft.com/fwlink/?LinkId=759670
    // for the documentation about the jsconfig.json format
    "compilerOptions": {
        "target": "es6",
        "module": "commonjs",
        "allowSyntheticDefaultImports": true
    },
    "exclude": [
        "node_modules",
        "bower_components",
        "jspm_packages",
        "tmp",
        "temp"
    ]
}

```
###code
```
var arr = {};
for (var i = 0; i < 5; i++) {
    arr[i] = i;
}
console.log(arr)
for (key in arr) {
    console.log(arr[key])
}
//{ key0: 0, key1: 1, key2: 2, key3: 3, key4: 4 }
//0
//1
//2
//3
//4
```
```
//函数声明会做代码提升
function app() {
    console.log(a);
}
app();
//Uncaught ReferenceError: a is not defined

function app() {
    console.log(a);
    var a = 1;
}
app();
//undefined

function app() {
    var a = 1;
    console.log(a);
}2
app();
//1
```
```
//闭包使得函数可以维持其创建时所在的作用域
var arr = [];
function app() {
    for (var i = 0; i < 20; i++) {
        arr.push(i);
    }
    console.log(arr);
}
console.log(arr);
app();
//[]
//[ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 ]
//想想两个数组分别是哪个语句log出来的

var arr = [];
for (var i = 0; i < 10; i++) {
    arr.push(function() {
        return i;
    });
}
console.log(arr[1]);
console.log(arr[1]());
console.log(arr[2]());
//[Function]
//10
//10

var arr = [];
for (var i = 0; i < 10; i++) {
    (function() {
        var i2 = i;
        arr.push(function() {
            return i2;
        });
    })();
}
console.log(arr[1]);
console.log(arr[1]());
console.log(arr[2]());
//[Function]
//1
//2
```
