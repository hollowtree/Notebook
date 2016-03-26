* 使用与媒体相关的样式表。eg：`<link rel="stylesheet" href="style.css" media="screen" />`其中media的值有screen、print、all等。
另外一种方法是把样式表放在`@media print{ }`中。

* 如果要定位的元素有多个类名，可以在选择器中将它们连在一起。就像`.a.b{color:red;}`这样。任何.a或.b选择器的规则仍会应用于该元素，但.a.b的规则的特殊性更高。注意类名之间没有空格。

* 在CSS3中，`:first-line`的语法为`::first-line`,`:first-letter`的语法为`::first-letter`。注意，它们用两个冒号代替了单个冒号。这样修改的目的是将伪元素（有四个，包括`::first-line`、`::first-letter`、`::before`和`::after`）与伪类（如`:first-child`、`:link`、`:hover`等）区分开。*伪元素(pseudo-element)*是HTML中并不存在的元素，它们是另一个元素的部分内容。*伪类(pseudo-class)*则应用于一组HTML元素，而你无需在HTML代码中用类标记它们。Ps：IE9之前的IE版本均不支持双冒号。

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
        选择器               | 属性值
        ---------------------|------
        [attribute]          | 匹配指定属性，不论具体值是什么
        [attribute="value"]  | 完全匹配指定属性值
        [attribute~="value"] | 属性值是以空格分隔的多个单词，其中有一个完全匹配指定值
        [attribute|="value"] | 属性值以 value- 打头
        [attribute^="value"] | 属性值以 value 开头，value为完整的单词或单词的一部分
        [attribute$="value"] | 属性值以 value 结尾，value为完整的单词或单词的一部分
        [attribute*="value"] | 属性值为指定值的子字符串
        ```
        p[class]{ };     /*所有具有class属性的段落*/
        ```
    1. 指定元素组
        ```
        h1, h2, h3, h4, h5, h6{ }
        ```
    1. 组合使用选择器
        ```
        article p{ }
        ```

* 文本样式
    * 字体
        * font-family是继承的，但有几个元素不会继承父元素的字体设置，其中有表单的select、textarea和input元素。不过，可以强制它们继承父元素的字体设置，代码为`input, select, textarea{font-family: inherit;}`
    * 指定替代字体
        * 字体类属：serif、sans-serif、cursive、fantasy、monospace（有衬线字体、无衬线字体、手写字体、装饰字体、等宽字体）。
        * 字体栈 `font-family: arial, helvetica, sans-serif;`
    * 斜体（真斜体、假斜体、倾斜版本）
        * 创建斜体：`font-style:italic;`或`font-style:oblique;`。分别是创建斜体文本和创建倾斜文本，区别极小，绝大部分情况下都使用前者。
        * 取消斜体：`font-style:normal;`
    * 粗体
        * `font-weight:bold` 或者输入数值，400代表正常粗细，700代表粗体，这样可以使用具有多种粗细版本的字体。
        * 别的属性值：bolder（更粗）、lighter（更细）、normal（正常，取消粗体）
    * 字体大小
        * `font-size:30px` 不过使用相对单位em更有助于在各种设备都能显示良好的页面。
        * rem （root em）的简称，总是以根元素(html元素)为参照系设置其它元素的字体大小，而不是父元素。注意，IE8及以下不支持。
        * pt 磅，用作打印样式表的单位
        * em 根据父元素设置字体大小，用百分数也行
        ```
        body{font-size:100%;}    /*默认字体大小，一般为16px*/
        p{font-size:1.125em;}    /*18px*/
        ```
    * 行高
        * `line-height:1.5;`
        * 一般使用数字设置行高，子元素会继承。比如设置行高为1.5，子元素行高 = 子元素字体大小 * 1.5
        * 如果使用百分数或者em设置行高，子元素只会继承产生的行高。比如父元素字体大小是16px，行高为150%，则该元素的行高是24px，且所有子元素的行高都是24px。
    * 简写
        * 至少应该包含字体大小和字体系列属性。斜体、粗体、小型大写字母的顺序可以调换。
        * normal、italic、oblique
        * normal、bold、bolder、lighter 或 100的倍数
        * normal、small-caps
        * font-size
        * /line-height
        * 字体系列，字体以逗号分隔
    * 颜色
        * `color:red;`
        * rgb(r, g, b);        0~255
        * rgb(r%, g%, b%);     百分数
        * hsl(h, s%, l%);      0~360，百分数，百分数
        * rgba(r, g, b, a);    0~255, 0~255, 0~255, 0~1
        * hsla(h, s%, l%, a);
        * #rrggbb;
        * IE8不支持HSL和alpha透明度
    * 背景
        ```
        background-color                       /*默认值transparent透明*/
        background-image:url(bg-pattern.png);  /*默认值none*/
        background-repeat:repeat;              /*repeat、repeat-x、repeat-y、no-repeat。重复、横向重复、纵向重复、不重复。默认重复*/
        background-attachment:fixed;           /*fixed、scroll、local。local的浏览器支持不太好，默认scroll*/
        background-position:left bottom;       /*还可以使用px，水平属性值，竖直属性值。可以是负数。默认值0 0，左上角*/
        background                             /*所有属性值都可以使用，排列顺序没有要求*/
        background-clip                        /**/
        background-origin                      /**/
        background-size                        /**/
        ```
    * 间距(可以使用负数，单位px，如果使用em，那么只有计算出来的结果会被继承)
        * word-space
        * letter-space
        * 恢复默认值，可以使用normal或0
    * 缩进(可以使用负数，单位px，如果使用em或百分数，那么只有计算出来的结果会被继承)
        * text-indent
        * 对内联元素无用，强制使用需要设置为`display:block;`或`display:inline-block;`
        * 使用负数会产生悬挂缩进，使用悬挂缩进时，要让容器有容纳伸到外面的文本的空间。
        * 恢复默认值，使用0
    * 对齐文本
        * text-align               /*left、center、right、justify 左、中、右、两端对齐*/
        * 适用于盒模型的元素，如h1~h6、p等
    * 修改文本的大小写
        * text-transform
        ```
        text-transform:capitalize;            /*每个单词的首字母大写*/
        text-transform:uppercase;             /*所有字母大写*/
        text-transform:lowercase;             /*所有字母小写*/
        text-transform:none;                  /*保持原样、取消继承的值*/
        ```
    * 小型大写字母
        * `font-variant:small-caps;`          /*设置*/
        * `font-variant:none;`                /*取消*/
