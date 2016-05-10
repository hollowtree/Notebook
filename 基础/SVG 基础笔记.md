## SVG 基础笔记

支持情况：IE 9+、Chrome 33.0+、Firefox 28.0+、Safari 7.0+

矢量图

使用方式：浏览器直接打开、使用<img>标签引用、使用SVG标签、作为CSS背景

* 基本图形：
    ```
    <rect>     矩形       x、y、width、height、rx、ry
    <circle>   圆         cx、cy、r
    <ellipse>  椭圆       cx、cy、rx、ry
    <line>     直线       x1、y1、x2、y2
    <polyline> 折线       x1、y1、x2、y2、x3、y3......
    <polygon>  多边形     x1、y1、x2、y2、x3、y3
    ```

* 基本属性：
    * fill `fill = #ffffff`
    * stroke `stroke = #eee`
    * stroke-width `strokeWidth = 10`
    * transform `transform = "rotate(30)"`

* 操作
    * 创建图形`document.createElementNS(ns, tagName);`
    * 添加图形`element.appendChild(childElement);`
    * 设置属性`element.setAttribute(name, value);`
    * 获取属性`element.getAttribute(name);`

## SVG 精髓
### 坐标系统
em：默认字体的大小，通常相当于文本行高。

ex：字母x的高度。

px：像素。

pt：点（1/72英寸）。

pc：点（1/6英寸）。

cm：厘米。

mm：毫米。

in：英寸。

对齐方式：preserveAspectRadio。取值：{[xMin / xMid / xMax] [yMin / yMid / yMax]}[meet / slice / none]

### 基本形状
[demo](hollowtree.github.io/demo/component/301/svg.html)
```
<!--stroke可能不支持的颜色：rgba()、hsl()、hsla()、transparent-->
<!--stroke-opcity，取值范围为0.0~1.0-->
<line x1="start-x" y1="start-y" x2="end-x" y2="end-y" stroke-width:3 stroke:red />
```

### 文档结构
内联样式、内部样式表、外部样式表、表现属性

表现属性位于优先级列表的最底部。任何来自内联样式、内部样式表、外部样式表的样式声明都会覆盖表现属性，但表现属性会覆盖继承的样式。

指定表现信息的首选应该是使用style属性或者样式表。

### 路径
M L H V Z

使用四条线和closepath是有区别的，closepath的首尾相交的点是连续的，而使用线段相交会产生缺口。
