# CSS3 基础笔记

* 浏览器厂商前缀
    * -webkit-    Safari、Chrome
    * -moz-       Firefox
    * -ms-        Internet Explorer
    * -o-         Opera
    * 现在，在多数情况下，一般只需要-webkit前缀
    * 并非所有的CSS3属性都需要使用为浏览器准备的前缀，比如text-shadow和opacity

* 创建圆角
    * 需要厂商前缀
    * border-radius
    ```
    border-radius:r;             /*圆角的半径大小*/
    border-top-left-radius:r;    /*左上方圆角的半径大小*/
    border-radius:x/y;           /*水平、垂直方向上的半径大小*/
    border-radius:r;             /*元素的半径大小*/
    ```
    * 有时候元素的背景会透过其圆角。为了避免这一情况，可以在元素的border-radius声明后增加一条样式规则：`background-clip:padding-box;`

* 文本阴影
    * `text-shadow:x-offset y-offset blur-radius color;`      水平偏移量 垂直偏移量 模糊半径 颜色
    * 多重阴影，各组值之间用英文逗号隔开。
    * 模糊半径可选
    * 恢复默认值 `text-shadow:none;`
    * 不需要厂商前缀

* 为其它元素添加阴影
    * box-shadow:x-offset y-offset blur-radius spread color inset;
    * 6个值，水平偏移量、垂直偏移量、可选的模糊半径、可选的spread值、颜色值、可选的inset关键字
    * 负的spread值会让阴影在元素内进行收缩
    * 恢复默认值 `box-shadow:none;`

* 应用多重背景
    * background
    ```
    div{
        background-color:navy;    /*备用背景颜色*/
        background-image:
            url(image1.png),url(image2.png),
            url(image3.png),url(image4.png);
        background-position:
            50% 102%, 100% -150px,
            0 -150px, 50% 100%;
        background-repeat:
            no-repeat, no-repeat,
            no-repeat, repeat-x,
    }
    ```
    ```
    div{
        background:navy url(image1.png) no-repeat center bottom;
        background:
            url(image1.png) no-repeat 50% 102%,
            url(image2.png) no-repeat 100% -150px,
            url(image3.png) no-repeat 0 -150px,
            url(image4.png) repeat-x 50% 100%;
    }
    ```

* 使用渐变背景
    * 线性渐变
    ```
    background:linear-gradient(silver, black);            /*默认从上到下渐变的*/
    background:linear-gradient(to top, silver, black);
    background:linear-gradient(to right, silver, black);
    background:linear-gradient(to left, silver, black);
    background:linear-gradient(to bottom right, silver, black);
    background:linear-gradient(290deg, silver, black);
    ```
    * 径向渐变
    ```
    background:radial-gradient(yellow, red);
    background:radial-gradient(at top, yellow, red);
    background:radial-gradient(100px 50px, yellow, red);
    background:radial-gradient(70% 90% at bottom left, yellow, red);
    background:radial-gradient(closest-side at 70px 60px, yellow, lime, red);
    background:radial-gradient(30px 30px at 65% 70%,yellow, lime 70%, red);
    ```

* 设置不透明度
    * opacity:0.5;  /*0完全透明，1完全不透明*/
    * opacity属性与使用RGBA或HSLA设置的alpha透明背景色是两个容易混淆的概念。opacity影响的是整个元素（包括其内容），而background-color:rgba(128,0,64,0.6); 这样的设置仅影响背景的透明度。

* 生成内容的效果

* 使用sprite拼合图像

* 其它
    * [微格式](http://microformats.org/)
