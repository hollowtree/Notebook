## HTML & CSS Notes


* 父元素 子元素 祖先 后代

* [字符引用](http://elizabethcastro.com/html/extras/entities.html) 现在常用的是用utf-8对文件进行编码，不过有时候还是会使用字符引用（比如`&copy;`）即好记又好输入）

* 网页文件最好使用utf-8，no BOM 这种编码来进行保存。

* 文件名中单词之间使用短横线较好，与下划线相比搜索引擎更喜欢短横线。

* URL [模式]://[主机名]/[目录]/[文件名] 模式有http/https/mailto/ftp等，模式后面通常紧跟一个冒号和两个斜杠。mailto是个例外，后面只有一个冒号。

绝对URL、相对URl、根相对URL（即先跳到网站根目录再找目标文件）

* 网页常见结构
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="utf-8" />
        <title></title>
    </head>
    <body>
        <header role="banner">         <!--标记页眉-->
            <nav role="navigation">    <!--标记重要导航-->
                <ul>
                    <li></li>
                    <li></li>
                </ul>
            </nav>
        </header>

        <main role="main">             <!--标记页面的主要区域，一个页面仅使用一次-->
            <article>             <!--标记文章，表示文档、页面、应用或网站一个独立的容器，原则上是可分配或可再用的。-->
                <section>         <!--定义区块，代表文档或应用的一个一般的区块-->
                </section>
            </article>
        </main>

        <aside role="complementary">            <!--指定附注栏，在这里用作侧栏。如果放在页面主要内容内，则其中的内容应与其所在的内容密切相关-->
        </aside>

        <footer role="contentinfo">          <!--创建页脚，当其最近的祖先是body时，表示它是页脚。不是页脚的时候不要加role。-->
        </footer>         <!--footer还可以放在比如article标签内来创建附录、索引、版权页、许可协议等-->
    </body>
    </html>
    ```

* 网站创建分级标题时，最好不要从高级别(eg:h3)跳到低级别(eg:h5)。不过可以从低级别跳到高级别。

* 可以为标签添加title属性，屏幕阅读器可以为用户朗读title文本，从而提升无障碍访问功能。不过用的最多的是链接




<!---->