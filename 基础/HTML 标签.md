* p 段落

* a 链接
    * rel="external" 外部链接最好加上

* small 免责声明、注解、署名等

* strong 表示内容的重要性，在HTML5中，strong表示的是重要程度，而不是表示强调

* em 表示内容的着重点，在HTML5中，em是表示强调的唯一元素

* figure 图 `<figure><figcaption>[...]</figcaption></figure>`

* img 添加图像
    * src 提供了将要插入的图像的名称
    * alt 提供了在图像无法获取时应该显示的文本

* cite 表示对某内容源的引用或参考。例如，戏剧或书本的标题，歌曲、照片或电影的名称，规范、报纸或法律文件等。

* blockquote q 引述文本（块级、行内），可以使用可选的cite属性，提供引述内容来源的URL。

* time 指定时间 有可选的datetime属性，格式 YYYY-MM-DDThh:mm:ss

* abbr 解释缩写词，添加可选的title属性来提供缩写词的全称

* dfn 首次定义术语的时候进行标记，后续再使用的时候无须对其进行定义。dfn元素及其定义必须挨在一起，否则便是错误的用法。可以添加可选的title属性。

* sub 创建下标，适用于化学分子式

* sup 创建上标，一种用法是表示脚注编号。上标下标会扰乱行高，去除其影响的css[链接](https://gist.github.com/unruthless/413930)

* address 定义与页面有关的作者、相关人士或组织的联系信息。

* ins 代表添加内容

* del 代表删除内容

* s 标注不在准确或不再相关的内容（一般不用于标注编辑）

* code 标记代码

* pre 使用预格式化的文本，如果很宽会产生横向滚动条，可以使用`pre{white-space:pre-warp;}`来打开自动换行。

* mark 突出显示文本

* br 创建换行

* wbr 标记可换行处，对一个较长的无间断短语进行标记，表示在此处必要时可以换行。

* u 非文本注解

* ruby/rp/rt 标记旁注元素，比如拼音

* meter 表示分数的值或已知范围的测量结果

* progress 表示任务的完成进度，有三个属性：max、value和form
