# <a id="menu">笔记</a>
[基本概念](#3)
[引用类型](#5)
[BOM](#8)

### <a id="3">基本概念</a>
[menu](#menu)
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

位操作符也有对应的复合赋值操作符：`<<=` / `>>=` / `>>>=`

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


### <a id="5">引用类型</a>
[menu](#menu)
#### Object 类型
访问对象属性可以使用点表示法，也可以使用方括号表示法来访问对象的属性。使用方括号语法时，应该将要访问的属性以字符串的形式放在方括号中。从功能上看，这两种访问对象属性的方法没有任何区别。但方括号语法的主要优点是可以**通过变量**来访问属性。属性名包含非字母非数字时，使用方括号来访问。一般优先使用点表示法。

#### Array 类型
创建数组时如果给构造函数只传递一个值也可以创建数组。如果传递的是数值，则会按照该数值创建包含给定项数的数组；而如果传递的是其它类型的参数，则会创建包含那个值的只有一项的数组。

不要在数组字面量的最后一项添加逗号。

数组的 length 属性不是只读的。
```
var flag=new Array(5); flag.length;     //5
var flag=new Array("5"); flag.length;   //1
```

**检测数组**
```
Array.isArray(["2","3"]);               //true
```

**转换数组**
```
["red","blue","green"].toString();      //"red,blue,green"
["red","blue","green"].valueOf();       //["red", "blue", "green"]
["red","blue","green"].join();          //"red,blue,green"
["red","blue","green"].join("-");       //"red-blue-green"
["red","blue","green"].join(" / ");     //"red / blue / green"
```

**栈方法**

push()返回修改后数组的长度，pop()返回移除的数组的最后一项
```
var arr=[1,3,0,9,5];                    //undefined
arr.push(2,8);                          //7
arr                                     //[1, 3, 0, 9, 5, 2, 8]
arr.pop();                              //8
```

**队列方法**

unshift()返回修改后数组的长度，shift()返回移除的数组的第一项
```
var arr=[1,3,0,9,5];                    //undefined
arr.unshift(7,9);                       //7
arr                                     //[7, 9, 1, 3, 0, 9, 5]
arr.shift();                            //7
```

**重排序方法**
```
[1,3,10,9,5].reverse();                       //[5, 9, 10, 3, 1]
[1,3,10,9,5].sort();                          //[1, 10, 3, 5, 9]
[1,3,10,9,5].sort(function(a,b){return a-b}); //[1, 3, 5, 9, 10]
[1,3,10,9,5].sort(function(a,b){return b-a}); //[10, 9, 5, 3, 1]
```

**操作方法**
```
//concat() 与 slice() 不会影响原始数组
var arr=[2,6,8,0];                   //undefined
arr.concat([3,7]);                   //[2, 6, 8, 0, 3, 7]
arr;                                 //[2, 6, 8, 0]
arr.slice(1);                        //[6, 8, 0]
arr;                                 //[2, 6, 8, 0]
arr.slice(1,3);                      //[6, 8]
arr.slice(-4,-2);                    //[2, 6]
arr.slice(0,-2);                     //[2, 6]
arr.slice(3,1);                      //[]

var arr1=[2,6,8,0,5,7,4,9,1];        //undefined
//删除
arr1.splice(2,2);                    //[8, 0]
arr1;                                //[2, 6, 5, 7, 4, 9, 1]
//插入
arr1.splice(2,0,45,23,78);           //[]
arr1;                                //[2, 6, 45, 23, 78, 5, 7, 4, 9, 1]
//替换
arr1.splice(2,1,11,12,13,14);        //[45]
arr1;                                //[2, 6, 11, 12, 13, 14, 23, 78, 5, 7, 4, 9, 1]
```

**位置方法**  IE9+、Firefox 2+、Safari 3+、Opera 9.5+、Chrome
```
[1,2,3,4,5,6,5,4,3,2,1].indexOf(3);         //2
[1,2,3,4,5,6,5,4,3,2,1].lastIndexOf(3);     //8
[1,2,3,4,5,6,5,4,3,2,1].indexOf(3,5);       //8
[1,2,3,4,5,6,5,4,3,2,1].lastIndexOf(3,4);   //2
[1,2,3,4,5,6,5,4,3,2,1].lastIndexOf(9);     //-1
```

**迭代方法**  IE9+、Firefox 2+、Safari 3+、Opera 9.5+、Chrome
```
var numbers=[1,2,3,4,5,4,3,2,1];            //undefined

//every() 如果指定函数对每一项都返回true，则返回true
var everyResult = numbers.every(
    function(item, index, array){
        return (item > 2);
    }
);                                          //undefined
everyResult                                 //false

//some() 如果指定函数对任一项返回true，则返回true
var someResult = numbers.some(
    function(item, index, array){
        return (item > 2);
    }
);                                          //undefined
someResult                                  //true

//filter() 返回指定函数会返回 true 的项组成的数组
var filterResult = numbers.filter(
    function(item, index, array){
        return (item > 2);
    }
);                                          //undefined
filterResult                                //[3, 4, 5, 4, 3]

//forEach() 对数组中的每一项运行传入的函数，没有返回值，本质上与使用for循环迭代数组一样
//可以使其改变数组自身
numbers.forEach(
    function(item, index, array){
        array[index] = item * 2;
    }
);                                          //undefined
numbers;                                    //[2, 4, 6, 8, 10, 8, 6, 4, 2]

//map() 返回每次指定函数调用的结果组成的数组
var mapResult = numbers.map(
    function(item, index, array){
        return item*item;
    }
);                                          //undefined
mapResult;                                  //[4, 16, 36, 64, 100, 64, 36, 16, 4]
```

**归并方法**  IE9+、Firefox 3+、Safari 4+、Opera 10.5+、Chrome
```
var values = [1,2,3,4,5];                   //undefined
var sum = values.reduce(
    function(prev,cur,index,array){
        return prev + cur;
    }
);                                          //undefined
sum;                                        //15

var sum1 = values.reduce(
    function(prev,cur,index,array){
        return prev + cur;
    }
,100);                                      //undefined
sum1;                                       //115

var arr=["L","o","v","e"];                  //undefined
var sum2 = arr.reduce(
    function(prev,cur,index,array){
        return prev+cur;
    }
);                                          //undefined
sum2;                                       //"Love"

var sum3 = arr.reduceRight(
    function(prev,cur,index,array){
        return prev+cur;
    }
);                                          //undefined
sum3;                                       //"evoL"
```

#### Date 类型
```
var someDate = new Date(Date.parse("6/24/2016"));            //undefined
someDate                                                     //Fri Jun 24 2016 00:00:00 GMT+0800 (China Standard Time)
var someDate = new Date(Date.parse("2016-01-02"));           //undefined
someDate                                                     //Sat Jan 02 2016 00:00:00 GMT+0800 (China Standard Time)
var someDate = new Date(Date.parse("2016-11-12T12:23:56"));  //undefined
someDate                                                     //Sat Nov 12 2016 20:23:56 GMT+0800 (China Standard Time)
```

#### RegExp 类型
g全局 i不区分大小写 m多行模式
元字符 ` ( ) [ ] { } \ ^ $ | ? * + . `
RegExp 构造函数的两个参数都是字符串，所以在某些情况下要对字符进行双重转义。
```
//实例属性
var pattern = new RegExp("[bc]at", "i");   //undefined
pattern.global;                            //false
pattern.ignoreCase;                        //true
pattern.multiline;                         //false
pattern.lastIndex;                         //0
pattern.source;                            //"[bc]at"

//实例方法
var arr = "12131415";                      //undefined
var pattern1=/12(13(14(15)?)?)?/gi;        //undefined
var match1=pattern1.exec(arr);             //undefined
match1.index;                              //0
match1.input;                              //"12131415"
match1[0];                                 //"12131415"
match1[1];                                 //"131415"
match1[2];                                 //"1415"
match1[3];                                 //"15"

var text = "cat, aat, bat, dat, cat, bat"; //undefined
var pattern2 = /[bc]at/i;                  //undefined
var match2 = pattern2.exec(text);          //undefined
match2;                                    //["cat"]
match2 = pattern2.exec(text);              //["cat"]
match2 = pattern2.exec(text);              //["cat"]

var pattern3 = /[bc]at/g;                  //undefined
var match3 = pattern3.exec(text);          //undefined
match3;                                    //["cat"]
match3 = pattern3.exec(text);              //["bat"]
match3 = pattern3.exec(text);              //["cat"]
match3 = pattern3.exec(text);              //["bat"]
match3 = pattern3.exec(text);              //null
```

#### Function 对象
函数名仅仅是指向函数的指针。
解析器会对函数声明进行“函数声明提升”，而不会对函数表达式这样做。
**函数内部属性**
在函数内部，有两个特殊的对象：arguments 和 this。arguments 的主要用途是保存函数参数，但这个对象还有一个名叫 callee 的属性，该属性是一个指针，指向拥有这个 arguments 对象的函数。
```
function factorial(num){
    if(num<1){
        return 1;
    }else{
        return num * arguments.callee(num - 1);
        //return num * factorial(num - 1);
    }
}
```
this 属性、caller属性
```
function outer(){inner();}
function inner(){console.log(inner.caller);}
outer();    //会在控制台打出函数outer的源代码
```
**函数属性和方法**
每个函数都包含两个非继承而来的方法：apply() 和 call()。这两个方法的用途都是在特定的作用域中调用函数。
ES5还定义了一个方法：bind()。这个方法会创建一个函数的实例，其this值会被绑定到传给bind()函数的值。

#### 基本包装类型
**Boolean 类型**
布尔表达式中的所有对象都会被转化为true，包括使用Boolean构造函数创建的对象。
最好不要使用布尔对象。
**Number 类型**
```
var num = 34;          //undefined
num.toFixed(3);        //"34.000"
var num1=23.4586;      //undefined
num1.toFixed(2);       //"23.46"

var num2=23;           //undefined
num2.toExponential(1); //"2.3e+1"

var num3=87;           //undefined
num3.toPrecision(1);   //"9e+1"
num3.toPrecision(2);   //"87"
num3.toPrecision(3);   //"87.0"
num3.toPrecision(4);   //"87.00"
```

### <a id="8">BOM</a>
[menu](#menu)
#### window 对象
**窗口位置**
`screenLeft` / `screenTop` / `screenX` / `screenY` / `moveTo()` / `moveBy()`
```
//IE11 最大化窗口时
screenLeft;       //0
screenTop;        //55
screenX;          //-8
screenY;          //-8

//Chrome Version 50.0.2661.87 m 最大化窗口时
screenLeft;       //0
screenTop;        //0
screenX;          //0
screenY;          //0

//Firefox 最大化窗口时
screenLeft;       //ReferenceError: screenLeft is not defined
screenTop;        //ReferenceError: screenTop is not defined
screenX;          //-8
screenY;          //-8

//Edge 最大化窗口时
screenLeft;       //0
screenTop;        //77
screenX;          //0
screenY;          //0

//Opera 36.0.2130.65 最大化窗口时
screenLeft;       //0
screenTop;        //0
screenX;          //0
screenY;          //0
```

**窗口大小**
`innerWidth` / `innerHeight`
`outerWidth` / `outerHeight`
`document.body.clientWidth` / `document.body.clientHeight`
`document.documentElement.clientWidth` / `document.documentElement.clientWidth`
`resizeTo()` / `resizeBy()`

**导航和打开窗口**
```
window.open("http://www.google.com","_blank","height=400,width=600,top=20,left=50,menubar=yes,status=yes,toolbar=yes");
window.close();
```

**间歇调用和超时调用**
```
setTimeout() / clearTimeout() / setInterval() / clearInterval()

var timeoutId=setTimeout(function(){},1000);
clearTimeout(timeoutId);
```

**系统对话框**
`alert("");` / `confirm("")` / `prompt("What's your name?", "Tom")`

#### location 对象
`location.href`

#### navigator 对象

#### screen 对象

#### history 对象
`history.go(-1)` / `history.back()` / `history.forward()`
