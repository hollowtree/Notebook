```
@charset "utf-8";
//变量
@test_width:300px;
.box{
    width:@test_width;
    height: @test_width;
    background-color: yellow;

    .border;
}
//混合
.border{
    border:solid 5px blue;
}

//混合 - 可带参数
.border-02(@border-width){
    border:solid black @border-width;
}

.test-border{
    .border-02(20px);
}

//混合 - 参数、值
.border-03(@border-width:10px){
    border:solid green @border-width;
}
.test-border-03{
    .border-03();
}

//匹配模式
.triangle(top,@w:5px,@c:#ccc){
    border-width:@w;
    border-color: @c transparent transparent transparent;
    border-style: solid dashed dashed dashed;
}
.triangle(@_;@w:5px;@c:#ccc){
    width: 0;
    height: 0;
    overflow: hidden;
}
.sanjiao{
    .triangle(top,100px);
}

.pos(r){
    position: relative;
}
.book{
    .pos(r);
}

//运算
.book{
    width: @test_width+20;
}

//嵌套
//<ul>
//    <li><a href="#"><span>..</span></a></li>
//</ul>
li{
    width: 200px;
    a{
        text-decoration: none;
        // & 代表上一层选择器
        &:hover{
            color: #ccc;
        }
    }
    span{
        font-size: 20px;
    }
}

//arguments
.border-04(@w:30px,@c:red,@s:solid){
    border:@arguments;
}
.test-border-04{
    .border-04();
}

//避免编译
.box{
    width: ~'calc(100%-30px)';
}

//important
.test-important{
    .border-04() !important;
}

```
```
@charset "utf-8";
.box {
  width: 300px;
  height: 300px;
  background-color: yellow;
  border: solid 5px blue;
}
.border {
  border: solid 5px blue;
}
.test-border {
  border: solid #000000 20px;
}
.test-border-03 {
  border: solid #008000 10px;
}
.sanjiao {
  border-width: 100px;
  border-color: #cccccc transparent transparent transparent;
  border-style: solid dashed dashed dashed;
  width: 0;
  height: 0;
  overflow: hidden;
}
.book {
  position: relative;
}
.book {
  width: 320px;
}
li {
  width: 200px;
}
li a {
  text-decoration: none;
}
li a:hover {
  color: #ccc;
}
li span {
  font-size: 20px;
}
.test-border-04 {
  border: 30px #ff0000 solid;
}
.box {
  width: calc(100%-30px);
}
.test-important {
  border: 30px #ff0000 solid !important;
}

```
