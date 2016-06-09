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
}
app();
//1
```
