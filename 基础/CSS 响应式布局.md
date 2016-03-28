# 构建响应式网站

* 制作可伸缩的图像
给图像添加样式`max-width:100%;`，这样图像会自动伸缩，且不会比本来的宽度更宽。
还可以使用`video,embed,object{max-width:100%;}`让HTML视频及其它媒体变成可伸缩的。

* 媒体查询
```
<link rel="stylesheet" media="screen and ( min-width: 720px ) and ( max-width: 1280px )" href="style-720-1280.css"
@media screen and ( min-width: 720px ) and ( max-width: 1280px ){...}
@media only/not screen and (min-width:480px){...}
```
width                 宽度
height                高度
device-width          设备宽度
device-height         设备高度
orientation           方向
aspect-ratio          高宽比
device-aspect-ratio   设备高宽比
color                 颜色
color-index           颜色数
monochrome            单色
resolution            分辨率
scan                  扫描
grid                  栅格
除了 orientation、scan、grid 以外，上述属性均可添加 min- 和 max- 前缀

```
$(document).ready(function(){
    if (window.screen.width < 600){
        $.getScript("http://jquery.mobile.js")
}
});
```

* 在HTML页面的head元素中，输入`<meta name="viewport" content="width=device-width" />`或`<meta name="viewport" content="width=device-width, initial-scale=1" />`，使视觉宽度与设备宽度的值相等


* 兼容旧版IE（条件注释）
```
<head>
    ...
    <!--[if gt IE 8]><!-->
    <link rel="stylesheet" href="style.css" />
    <!--<![endif]-->

    <!--[if lt IE 9]><!-->
    <link rel="stylesheet" href="old-ie.css" />
    <!--<![endif]-->
</head>
```
```
<head>
    ...
    <link rel="stylesheet" href="style.css" />

    <!--[if lt IE 9]><!-->
    <script src="respond.min.js"></script>
    <!--<![endif]-->
</head>
```
[所需的js文件](https://github.com/scottjehl/Respond)
[条件注释](https://zh.wikipedia.org/wiki/%E6%9D%A1%E4%BB%B6%E6%B3%A8%E9%87%8A)