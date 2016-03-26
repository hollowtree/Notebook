## HTML & CSS Notes


* 父元素 子元素 祖先 后代

* [字符引用](http://elizabethcastro.com/html/extras/entities.html) 现在常用的是用utf-8对文件进行编码，不过有时候还是会使用字符引用（比如`&copy;`）即好记又好输入）

* 网页文件最好使用utf-8，no BOM 这种编码来进行保存。

* 文件名中单词之间使用短横线较好，与下划线相比搜索引擎更喜欢短横线。

* URL [模式]://[主机名]/[目录]/[文件名] 模式有http/https/mailto/ftp等，模式后面通常紧跟一个冒号和两个斜杠。mailto是个例外，后面只有一个冒号。

绝对URL、相对URl、根相对URL（即先跳到网站根目录再找目标文件）

* 网页常见结构
* 网页文件最好使用utf-8，no BOM 这种编码来进行保存。

* 网页基本结构

    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="utf-8" />
        <title></title>
    </head>
    <body>
        <!--标记页眉 还有群组元素hgroup-->
        <header role="banner">
            <!--标记重要导航-->
            <nav role="navigation">
                <ul>
                    <li></li>
                    <li></li>
                </ul>
            </nav>
        </header>

        <!--标记页面的主要区域，一个页面仅使用一次-->
        <main role="main">
            <!--标记文章，表示文档、页面、应用或网站一个独立的容器，原则上是可分配或可再用的。-->
            <article>
                <!--定义区块，代表文档或应用的一个一般的区块-->
                <section>
                </section>
            </article>
        </main>

        <!--指定附注栏，在这里用作侧栏。如果放在页面主要内容内，则其中的内容应与其所在的内容密切相关-->
        <aside role="complementary">
        </aside>

        <!--创建页脚，当其最近的祖先是body时，表示它是页脚。不是页脚的时候不要加role。-->
        <!--footer还可以放在比如article标签内来创建附录、索引、版权页、许可协议等-->
        <footer role="contentinfo">          
        </footer>         
    </body>
    </html>
    ```

* 网站创建分级标题时，最好不要从高级别(eg:h3)跳到低级别(eg:h5)。不过可以从低级别跳到高级别。

* 可以为标签添加title属性，屏幕阅读器可以为用户朗读title文本，从而提升无障碍访问功能。不过用的最多的是链接





链接大多数情况下不建议使用target属性

锚链接 1）在目标元素的开始标签里添加id 2）在链接中使用`<a href="#anchor-name">`，其中anchor-name是目标的id属性值。如果锚位于另一个文档，就使用`<a href="page.html#anchor-name">`。如果锚位于另一台服务器的页面，则需输入`<a href="http://www.site.com/directory/page.html#anchor-name">`。

JPEG|不支持透明度
GIF|支持索引色透明
PNG|支持索引色透明，支持alpha透明，PS不支持alpha透明的PNG-8，但支持PNG-32。

HTML图像映射

RGBA alpha的值越接近0，颜色就越透明，0表示完全透明，1表示完全不透明。IE8不支持。
HSL color:hsl(282,100%,25%);  色相，饱和度，亮度
IE8及其以前的版本不支持alpha透明度。兼容性css如下，其中IE8只能理解第一行，而现代浏览器两行都可以理解，则IE8应用第一行的样式，现代浏览器应用第二行的样式。当然也可以单独为旧浏览器定义备选的纯色。
```
p{
    background-color:#3c8f00;           /* for IE before IE9 */
    background-color:hsl(95,100%,28%);
    ...
}
```
hsl有时候更易使用。“选择一个0到360之间的色相，并将饱和度设为100，亮度设为50，就会得到这种颜色最纯的形式。降低饱和度，颜色就会向灰色变化。增加亮度，颜色就会向白色变化；减少亮度，颜色就会向黑色变化。——Brandon Mathis”
<!---->
alt rel title

https://www.w3.org/TR/CSS21/propidx.html

[会被继承的CSS属性](http://stackoverflow.com/questions/5612302/which-css-properties-are-inherited)