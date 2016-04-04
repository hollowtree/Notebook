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

1. 转义字符
<div id="id#b"></div>    $("#id\\#b");

1. 
示例|意义
--------------------------|---------
$(".one").next("div");    |$(".one+div");
$(".one").nextAll("div"); |$(".one~div");
$(".one").sublings("div");|选择.one类元素的所有同辈div

1. 过滤选择器（选择器都以冒号开头）
    1. 基本过滤选择器

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

    1. 内容过滤选择器

    选择器         |描述                          |返回    |示例
    ---------------|------------------------------|--------|----
    :contains(text)|选取含有文本内容为“text”的元素|集合元素|$("div:contains('我')")
    :empty         |选取不包含子元素或文本的空元素|集合元素|$("div:empty")
    :has(selector) |选取含有选择器匹配的元素的元素|集合元素|$("div:has(p)")
    :parent        |选取含有子元素或文本的元素    |集合元素|$("div:parent")

    1. 可见性过滤选择器

    选择器         |描述                          |返回    |示例
    ---------------|------------------------------|--------|----
    :hidden        |选取所有不可见的元素          |集合元素|$(":hidden")
    :visible       |选取所有可见的元素            |集合元素|$("div:visible")

    1. 属性过滤选择器

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

    1. 子元素过滤选择器

    选择器                              |描述                               |返回    |示例
    ------------------------------------|-----------------------------------|--------|----
    :nth-child(index/even/odd/equation) |index从1算起                       |集合元素|
    :first-child                        |选取每个父元素的第一个子元素       |集合元素|$("ul li:first-child")
    :last-child                         |选取每个父元素的最后一个子元素     |集合元素|$("ul li:last-child")
    :only-child                         |如果一个元素没有同辈元素，则被匹配 |集合元素|$("ul li:only-child")
        * :eq(index)只匹配一个元素，而:nth-child将为每个父元素匹配子元素，并且:nth-child(index)的index是从1开始的，而:eq(index)是从0算起的
        * :first-child、:last-child返回集合元素，:first、:last返回单个元素
        * :nth-child()选择器很常用
            1. :nth-child(even) 选取每个父元素下的索引值是偶数的元素
            1. :nth-child(odd)  选取每个父元素下的索引值是奇数的元素
            1. :nth-child(2)    选取每个父元素下的索引值等于2的元素
            1. :nth-child(3n)   选取每个父元素下的索引值是3的倍数的元素（n从1开始）
            1. :nth-child(3n+1) 选取每个父元素下的索引值是(3n+1)的元素（n从1开始）
    
    1.表单对象属性过滤选择器

    选择器         |描述                                  |返回    |示例
    ---------------|--------------------------------------|--------|----
    :enabled       |选取所有可用元素                      |集合元素|
    :disabled      |选取所有不可用元素                    |集合元素|
    :checked       |选取所有被选中的元素（单选框，复选框）|集合元素|
    :selected      |选取所有被选中的选项元素（下拉列表）  |集合元素|

* 表单选择器

选择器      |描述                                       |返回    |示例
------------|-------------------------------------------|--------|------------
:input      |选取所有input、textarea、select、button元素|集合元素|$(":input")
:text       |选取所有单行文本框                         |集合元素|$(":text")
:password   |选取所有的密码框                           |集合元素|$(":password")
:radio      |选取所有的单选框                           |集合元素|$(":radio")
:checkbox   |选取所有的多选框                           |集合元素|$(":checkbox")
:submit     |选取所有的提交按钮                         |集合元素|$(":submit")
:image      |选取所偶的图像按钮                         |集合元素|$(":image")
:reset      |选取所有的重置按钮                         |集合元素|$(":reset")
:button     |选取所有的按钮                             |集合元素|$(":button")
:file       |选取所有的上传域                           |集合元素|$(":file")
:hidden     |选取所有的不可见元素                       |集合元素|$(":hidden")

1. 几个jQuery方法
    * show();
    * css(name,value);
    * text(string);
    * fiter(expr);
    * addClass(class);


