* 使用与媒体相关的样式表。eg：`<link rel="stylesheet" href="style.css" media="screen" />`其中media的值有media、print、all等。
另外一种方法是把样式表放在`@media print{ }`中。

* 如果要定位的元素有多个类名，可以在选择器中将它们连在一起。就像`.a.b{color:red;}`这样。任何.a或.b选择器的规则仍会应用于该元素，但.a.b的规则的特殊性更高。注意类名之间没有空格。

* 在CSS3中，`:first-line`的语法为`::first-line`,`:first-letter`的语法为`::first-letter`。注意，它们用两个冒号代替了单个冒号。
这样修改的目的是将伪元素（有四个，包括`::first-line`、`::first-letter`、`::before`和`::after`）与伪类（如`:first-child`、`:link`、`:hover`等）区分开。*伪元素(pseudo-element)*是HTML中并不存在的元素，它们是另一个元素的部分内容。*伪类(pseudo-class)*则应用于一组HTML元素，而你无需在HTML代码中用类标记它们。Ps：IE9之前的IE版本均不支持双冒号。

* 选择器
    1. 按名称选择
        ```
        p{ }
        ```
    1. 按类或ID选择元素
        ```
        .a{ }
        #b{ }
        ```
    1. 按上下文选择元素
        * 按祖先元素选择要格式化的元素
            ```
            article p{ }
            ```
        * 按父元素选择要格式化的元素
            eg：仅选择 article 标签元素的子元素（而非子子元素、子子子元素等）的p元素，包含于其它任何元素的p元素均不会被选中。
            ```
            article>p{ }
            ```
        * 按相邻同胞元素选择要格式化的元素
            article 是两个p元素的父元素，两个p元素相邻
            ```
            article p+p{ }
            ```
        * 按普通同胞元素选择要格式化的元素
            ```
            article p~p{ }
            ```
    1. 选择第一个或最后一个子元素
        ```
        li:first-child{ }         /*IE8支持*/
        li:last-child{ }          /*IE8不支持*/
        ```
    1. 选择元素的第一个字母或者第一行
        ```
        p:first-letter{ }      /*段首字母大写*/
        p:first-line{ }
        ```
    1. 按状态选择链接元素（LVFHA或LVHFA）
        * 也可以对其它类型的元素使用 :active 和 :hover 伪类。eg：`p:hover{ }`
        ```
        a:link{ }
        a:visted{ }      /*激活后*/
        a:focus{ }       /*通过键盘（如通过Tab键）选择并准备好激活的*/
        a:hover{ }       /*鼠标悬停*/
        a:active{ }      /*激活时*/
        ```
    1. 按属性选择元素

        ABCD | EFGH | IGKL
        -----|------|----
        a    | b    | c
        d    | e    | f
        g    | h    | i
        ```
        p[class]{ };     /*所有具有class属性的段落*/
        ABCD | EFGH | IGKL
-----|------|----
a    | b    | c
d    | e    | f
g    | h    | i
        ```
    1. 
        ``````
    1. 
        ``````
    1. 
        ``````