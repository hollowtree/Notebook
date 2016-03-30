# jQuery 基础笔记

1. 在jQuery库中，$是jQuery的一个简写形式

1. `$(document).ready();`其中的所有代码会在Dom加载后立即执行
```
window.onload = function(){        /*只能使用一次，页面所有内容都加载完毕后才能执行*/
    ...
};

$(document).ready(function(){      /*能使用多次*/
    ...
});

$(function(){                      /*简写*/
    ...
});
```

1. 在jQuery中无法使用DOM对象的任何方法，同样，DOM对象也不能使用jQuery里的方法。

1. 如果获取的对象是jQuery对象，那么可以在变量名之前加上$，以此与DOM对象区分

1. jQuery对象与DOM对象的相互转化
```
var $cr=$("#cr");                      //jQuery对象
var cr1=$cr[0];                        //DOM对象   [index]
var cr2=$cr.get(0);                    //DOM对象   get(index)

var dr=document.getElementById("dr");  //DOM对象
var $cr=$(dr);                         //jQuery对象
```
1. 一般用到的jQuery对象都是通过$()函数制造出来的

1. CSS选择器找到元素后是添加样式，而jQuery选择器找到元素后是添加行为。

1. jQuery选择器获取的是对象，即使网页上没有此元素。因此要用jQuery判断网页上某个内容是否存在是，不能使用`if($("#tt")){...}`，而应该根据获取到的元素的长度来判断`if($("#tt").length>0){...}`，或者转化为DOM对象来判断`if($("#tt")[0]){...}`

1. 
方法|意义
--------------------------|---------
$(".one").next("div");    |$(".one+div");
$(".one").nextAll("div"); |$(".one~div");
$(".one").sublings("div");|选择.one类元素的所有同级div


