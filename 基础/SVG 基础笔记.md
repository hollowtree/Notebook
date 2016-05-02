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
