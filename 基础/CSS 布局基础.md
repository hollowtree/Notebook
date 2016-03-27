* 在旧版浏览器中为HTML5元素添加样式
    1. 在主样式表中添加样式（或者使用CSS重置或normalize.css）
    ```
    article, aside, figcaption, figure, footer, header, main, nav, section{display: block;}
    ```
    1. 在head标签内添加一个js文件
        * if less than ie 9, 注意，是LT而不是IT
    ```
    <!--[if lt IE 9]>
    <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
    <![endif]-->
    ```

* 对默认样式进行充值或标准化
    * http://meyerweb.com/eric/tools/css/reset/
    * http://necolas.github.io/normalize.css/

* 盒模型
    * content、padding、border、margin
    * 显示宽高等于width、height的值。`box-sizing:border-box;`

* 控制元素的显示类型和可见性
    * display
    ```
    display:block;
    display:list-item;                /*li元素默认的*/
    display:inline;                   /**/
    display:inline-block;
    display:none;

    visibility:hidden;     /*不可见，但是保留其所占的空间*/
    visibility:visible;    /*可见*/
    visibility:collapse;   /*用于table元素的部分内容*/
    ```
    * 设置为`display:inline;`的元素不接受padding的设置，但padding-top和padding-bottom会越界进入相邻元素的区域，而不是局限于该元素本身的空间。

* 设置元素的高度和宽度
    * width          px、em、父元素的百分数，默认值是auto
    * height         px、em，默认值是auto
    * min-width、min-height、max-width、max-height    设置最小和最大尺寸
    * 除非确定元素的内容不会变得更高，不然最好避免在样式表中指定高度。

* 在元素周围添加内边距
    * padding

* 设置边框
    * border-style   /*none、dotted点线、dashed虚线、solid实线、double双线、groove槽线、ridge脊线、inset凹边、outset凸边*/
    * border-width   /*需要单位 px*/
    * border-color

* 设置元素周围的外边距
    * margin
    * 如果对内边距和外边距使用百分数，通常不会将它们用于上下边距的值，因为这样的值是基于其包含块的宽度的。

* 使元素浮动
    * float
    * left right none（默认值）。
    * 清除浮动
    ```
    .clearfix:before,
    .clearfix:after {
        content:" ";
        display:table;
    }
    .clearfix:after{
        clear:both;
    }
    .clearfix{
        *zoom:1;
    }
    ```
    * 浮动元素的display属性会变成`display:block;`，哪怕将其设置为`display:inline;`（无论是浏览器的默认样式还是手动显式设置，该属性值依然是block。
    * 可以对浮动元素的父元素使用overflow属性以代替clearfix方法
    ```
    overflow:hidden;    /*可能会截断内容*/
    overflow:auto;      /*可能会产生滚动条*/
    ```

* 定位
    * static、relative、absolute、fixed
    * 使用相对定位、绝对定位或固定定位时，对于相互重叠的元素，可以用z-index属性指定它们的叠放次序。

* 处理溢出
    * overflow
    ```
    overflow:visible;     /*让元素盒子里的所有内容可见，默认项*/
    overflow:hidden;      /*隐藏元素盒子里容纳不了的内容*/
    overflow:scroll;      /*无论元素是否需要，都在元素上添加滚动条*/
    overflow:auto;        /*让滚动条仅在访问者访问溢出内容是出现*/
    ```

* 垂直对齐元素
    * vertical-align
    ```
    vertical-align:baseline;              /*使元素的基准线对齐父元素的基准线*/
    vertical-align:middle;                /*使元素位于父元素中央*/
    vertical-align:sub;                   /*使元素成为父元素的下标*/
    vertical-align:super;                 /*使元素成为父元素的上标*/
    vertical-align:text-top;              /*使元素的顶部对齐父元素的顶部*/
    vertical-align:text-bottom;           /*使元素的底部对齐父元素的底部*/
    vertical-align:top;                   /*使元素的顶部对齐当前行里最高元素的顶部*/
    vertical-align:bottom;                /*使元素的底部对齐当前行里最低元素的底部*/
    vertical-align:输入元素行高的百分比;  /*可以是正数，可以是负数*/
    vertical-align:输入某个值;            /*正负均可，单位为px或em，分别按照特定的值向上或向下移动元素*/
    ```

* 修改鼠标指针
    * cursor
    ```
cursor:default;
cursor:pointer;
cursor:crosshair;
cursor:move;
cursor:wait;
cursor:help;
cursor:text;
cursor:progress;
cursor:auto;
cursor:x-resize;    /*x的取值为n（北）、nw（西北）、e（东）等*/
    ```