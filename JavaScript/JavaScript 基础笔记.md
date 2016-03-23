#Javascript 基础笔记


### 碎
* 使用parseInt()函数可解析一个字符串,并返回一个整数。

###数组赋值
第一种方法：var myarray = new Array(66,80,90,77,59);//创建数组同时赋值 

	Ps:对于
	var myarr=new Array(66);
	document.write(myarr.length+" ");
	document.write(myarr[1]);
	输出“66 undefined”
第二种方法：var myarray = [66,80,90,77,59];//直接输入一个数组（称 “字面量数组”）

###事件
* 事件 - 说明
* onclick - 鼠标单击事件 - onclick=" "
* onmouseover - 鼠标经过事件 - onmouseover=" "
* onmouseout - 鼠标移开事件 - onmouseout=" "
* onchange - 文本框内容改变事件 - onchange=" "
* onselect - 文本框内容被选中事件 - onselect=" "
* onfocus - 光标聚集 - onfocus=" "
* onblur - 光标离开 - onblur=" "
* onload - 网页导入 - onload=" " - 加载页面时，触发onload事件，事件写在<body>标签内
* onunload - 关闭网页 - window.onunload = onunload_message; - onunload_message()是一个函数

###对象
* Date日期对象(get/set)
	* dateObject.<get/set><FullYear/Year/Month/Date/Hours/Minutes/Seconds/Time/Day>();
* String 字符串对象
	* stringObject.length; 返回字符串的长度
	* stringObject.toUpperCase(); 转换字符串为大写
	* stringObject.toLowerCase(); 转换字符串为小写
	* stringObject.charAt(index); 返回字符串指定位置的字符
	* stringObject.indexOf(substring, startpos); 返回指定的字符串(substring)首次出现的位置,其中可选参数startpos是起始检测位置
	* stringObject.split(separator,limit); 将字符串分割为字符串数组，并返回此**数组**； separator指定分割的字符，可选参数limit指定分割的次数
	* stringObject.substring(starPos,stopPos); 用于提取字符串中介于两个指定下标之间的字符;返回的内容是从 start开始(包含start位置的字符)到 stop-1 处的所有字符，其长度为 stop 减start;如果参数 start 与 stop 相等，那么该方法返回的就是一个空串（即长度为 0 的字符串）;如果 start 比 stop 大，那么该方法在提取子串之前会先交换这两个参数。
	* stringObject.substr(startPos,length); 字符串中提取从 startPos位置开始的指定数目的字符串
* Math对象
	* 对象属性：E/LN2/LN10/LOG2E/LOG10E/PI/SQRT1_2/SQRT2 
	* 对象方法：abs(x);exp(x);log(x);ceil(x);floor(x);max(x,y);min(x,y);pow(x,y);random();round(x);toSource();valueOf();等
* Array 数组对象
	* 对象方法：concat();join();pop();push();reverse();shift();slice();sort();splice();toSource();toString();toLocalString();unshift();valueOf();
	* arrayObject.concat(array1,array2,...,arrayN); 用于连接两个或多个数组。此方法返回一个新数组，不改变原来的数组。
	* arrayObject.join(分隔符); 用于把数组中的所有元素放入一个字符串。元素是通过指定的分隔符进行分隔的，分隔符可选
	* arrayObject.reverse(); 用于颠倒数组中元素的顺序
	* arrayObject.slice(start,end); 该方法并不会修改数组，而是返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。
	* arrayObject.sort(方法函数); 使数组中的元素按照一定的顺序排列。
* window对象
	* alert()          显示带有一段消息和一个确认按钮的警告框
	* prompt()         显示可提示用户输入的对话框
	* confirm()        显示带有一段消息以及确认按钮和取消按钮的对话框
	* open()           打开一个新的浏览器窗囗或查找一个已命名的窗囗
	* close()          关闭浏览器窗囗
	* print()          打印当前窗囗的内容
	* focus()          把键盘焦点给予一个窗囗
	* blur()           把键盘点从顶层窗囗移开
	* moveBy()         可相对窗囗的当前坐标把它移动指定的像素
	* moveTo()         把窗囗的左上角移动到一个指定的坐标
	* resizeBy()       按照指定的像素调整窗囗的大小
	* resizeTo()       把窗囗的大小调整到指定的宽度和高度
	* scrollBy()       按照指定的像素值来滚动内容
	* scrollTo()       把内容滚动到指定的坐标
	* setInterval()    每隔指定的时间执行代码; setInterval("clock()",100)或setInterval(clock,100), clock()是一个示例函数
	* setTimeout()     在指定的延迟时间之后来执行代码
	* clearInterval()  取消setlnterval()的设置; var i=setInterval(clock,100);clearInterval(i); clock()是一个示例函数
	* clearTimeout()   取消setTimeout()的设置
* History对象 
	* 语法：window.history.[属性|方法]
	* 对象属性：length 返回浏览器历史列表中的URL数量
	* 对象方法：back();forward();go() 
* Location对象
	* 语法: location.[属性|方法]
	* 对象属性：hash/host/hostname/href/pathname/port/protocol/search
	* 对象方法：assign(); reload(); replace();
* Navigator对象
	* 语法: navigator.[属性]
	* 对象属性：appCodeName/appName/appVersion/platform/userAgent
* Screen对象
	* 语法：window.screen.[属性]
	* 对象属性：availHeight/availWidth/colorDepth/pixelDepth/height/width