##笔记
[基本概念](#3)

### <a id="3">基本概念</a>
####语法
严格模式 `"use strict;"`

#### 数据类型
undefined / null / boolean / number / string / object
```
var flag;                             //undefined
typeof(flag)                          //"undefined"
typeof(true);                         //"boolean"
typeof("hui");                        //"string"
typeof(1)                             //"number"
flag=null; typeof(flag);              //"object"
flag=new Object(); typeof(flag);      //"object"
flag=function(){}; typeof(flag);      //"function"
```

```
var flag;        //undefined
alert(flag);     //undefined
typeof(flag);    //"undefined"
alert(temp);     //Uncaught ReferenceError: temp is not defined(…)
typeof(temp);    //"undefined"   //对未声明过的变量，只能执行typeof一项操作
```

```
var flag=Boolean(9);      //转型函数
Boolean(9);               //true
Boolean(null);            //false
Boolean(NaN);             //false
Boolean(undefined);       //false
Boolean("");              //false
```

浮点数值的最高精度是17位
```
parseInt("ff");           //NaN
parseInt("0xff");         //255
parseInt("ff",16);        //255
parseInt("yu67");         //NaN
parseInt("67yu");         //67

parseFloat("3.14");       //3.14
parseFloat("3.14.15");    //3.14
parseFloat("3.14e3");     //3140
```

字符字面值：\n 换行   \t 制表   \b 退格   \r 回车
```
"hilujlio".length;        //8

var flag=1024;            //undefined
flag.toString();          //"1024"
flag.toString(2);         //"10000000000"
flag.toString(8);         //"2000"
flag.toString(16);        //"400"

var flag1;                //undefined
flag1.toString();         //Uncaught TypeError: Cannot read property 'toString' of undefined(…)
String(flag1);            //"undefined"
flag1=null; String(flag1);//"null"
```

#### 操作符
一个数的相反数等于它的反码加1。
按位非操作符（~）返回数值的反码。
位操作符也有对应的复合赋值操作符：<<= / >>= / >>>=
逻辑与和逻辑或都属于短路操作。
不能在逻辑与操作中使用未定义的值。
```
~10+1           //-10

1<<2;           //4
1<<10;          //1024
1<<30;          //1073741824
1<<31;          //-2147483648
1<<32;          //1
1<<33;          //2
```

#### 函数
在函数体内部可以通过 arguments 对象来访问这个参数数组，从而获取传递给函数的每一个参数。
通过 arguments.length 获取函数接收参数的个数从而让函数分别实现适当的功能，虽然这个特性算不上完美的重载，但也足够弥补 ECMAScript 的这一缺憾了。
arguments对象的长度是由传入的参数个数决定的，不是由定义函数时的参数的个数决定的。
ECMAScript 函数没有传统意义的重载，如果定义了两个名字相同的函数，则该名字只属于后定义的函数。
实际上，未指定返回值的函数返回的是一个特殊的 undefined 值。


### <a id="4">变量、作用域和内存问题</a>

### <a id="8">BOM</a>
