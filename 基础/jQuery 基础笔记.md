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

1. 过滤选择器
    * 基本过滤选择器
    选择器         |描述                          |返回    |示例
    ---------------|------------------------------|--------|----
    :first         |选取第1个元素                 |单个元素|$("div:first")
    :last          |选取最后一个元素              |单个元素|$("div:last")
    :not(selecttor)|去除所有与给定选择器匹配的元素|集合元素|$("input:not(.myClass)") 选取class不是myClass的所有元素，前提是这个元素有class
    :even          |选取索引是偶数的所有元素      |集合元素|$("input:even")
    :odd           |选取索引是奇数的所有元素      |集合元素|$("input:odd")
    :eq(index)     |选取索引等于index的元素       |单个元素|$("input:eq(1)")
    :gt(index)     |选取索引大于index的元素       |集合元素|$("input:gt(1)")
    :lt(index)     |选取索引小于index的元素       |集合元素|$("input:lt(1)")
    :header        |选取所有的标题元素            |集合元素|$(":header") 选取网页中所有h1,h2,h3等等
    :animated      |选取当前正在执行动画的所有元素|集合元素|$("div:animated")
    :focus         |选取当前获取焦点的元素        |集合元素|$(":focus")
    * 内容过滤选择器
    选择器         |描述                          |返回    |示例
    ---------------|------------------------------|--------|----
    :contains(text)|选取含有文本内容为“text”的元素|集合元素|$("div:contains('我')")
    :empty         |选取不包含子元素或文本的空元素|集合元素|$("div:empty")
    :has(selector) |选取含有选择器匹配的元素的元素|集合元素|$("div:has(p)")
    :parent        |选取含有子元素或文本的元素    |集合元素|$("div:parent")
    * 可见性过滤选择器
    选择器         |描述                          |返回    |示例
    ---------------|------------------------------|--------|----
    :hidden        |选取所有不可见的元素          |集合元素|$(":hidden")
    :visible       |选取所有可见的元素            |集合元素|$("div:visible")
    * 属性过滤选择器
    选择器                |描述    |返回    |示例
    ----------------------|--------|--------|----
    [attribute]           |        |集合元素|$("div[id]")
    [attribute  = value]  |        |集合元素|$("div[title=test]")
    *[attribute != value]*|        |集合元素|
    [attribute ^= value]  |        |集合元素|
    [attribute $= value]  |        |集合元素|
    [attribute *= value]  |        |集合元素|
    [attribute \|= value] |        |集合元素|
    [attribute ~= value]  |        |集合元素|
    [attribute1]...       |        |集合元素|$("div[id][title$=test)")



    
    
    
