## HTML & CSS Notes


* 父元素 子元素 祖先 后代

* [字符引用](http://elizabethcastro.com/html/extras/entities.html) 现在常用的是用utf-8对文件进行编码，不过有时候还是会使用字符引用（比如`&copy;`）即好记又好输入）

* 文件名中单词之间使用短横线较好，与下划线相比搜索引擎更喜欢短横线。

* URL [模式]://[主机名]/[目录]/[文件名] 模式有http/https/mailto/ftp等，模式后面通常紧跟一个冒号和两个斜杠。mailto是个例外，后面只有一个冒号。

绝对URL、相对URl、根相对URL（即先跳到网站根目录再找目标文件）

* 网页文件最好使用utf-8，no BOM 这种编码来进行保存。

* 网页基本结构
    <pre><code>
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="utf-8" />
        <title></title>
    </head>
    <body>

    </body>
    </html>
    </code></pre>