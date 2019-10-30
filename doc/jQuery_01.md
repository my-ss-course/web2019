# jQuery基础

## jQuery是什么

- jQuery是一个快速、简洁的JavaScript框架.
- jQuery设计的宗旨是“write Less，Do More”，即倡导写更少的代码，做更多的事情。它封装JavaScript常用的功能代码，提供一种简便的JavaScript设计模式，优化HTML文档操作、事件处理、动画设计和Ajax交互。
- jQuery的核心特性可以总结为：具有独特的链式语法和短小清晰的多功能接口；具有高效灵活的css选择器，并且可对CSS选择器进行扩展；拥有便捷的插件扩展机制和丰富的插件。jQuery兼容各种主流浏览器，如IE 6.0+、FF 1.5+、Safari 2.0+、Opera 9.0+等。
- jQuery官网地址  https://jquery.com/

## DOM

- DOM 是 Document Object Model（文档对象模型）的缩写。
- DOM 是 W3C（万维网联盟）的标准接口规范，是一种处理HTML和XML文件的标准API。
- HTML DOM - 针对 HTML 文档的标准模型，是关于如何获取、修改、添加或删除 HTML 元素的标准。
- DOM树结构精确地描述了HTML文档中标签间的相互关联性。将HTML文档转化为DOM树的过程称为解析(parse)。
- HTML文档被解析后，转化为DOM树，因此对HTML文档的处理可以通过对DOM树的操作实现。

## jQuery文件说明
jQuery文件的文件名通常为jquery.min.js 或 jquery.js
- jquery.min.js（Production version） - 用于实际上线的Web系统，是精简和压缩的版本。
- jquery.js（Development version） - 用于测试和开发的系统中使用，是未压缩，可读性好的版本。

## jQuery使用方式

### 下载jquery.js文件到本地
```
<head>
<script src="jquery.min.js"></script>
</head>
```
### 可以通过CDN（内容分发网络）引用

```
<script src="http://libs.baidu.com/jquery/2.0.0/jquery.min.js"></script>
```

## jQuery 选择器
- jQuery 选择器是如何准确地选取DOM树中的元素。
- jQuery 元素选择器和属性选择器允许通过标签名、属性名或内容对 HTML 元素进行选择。
- jQuery 元素选择器使用 CSS 选择器来选取 HTML 元素
- jQuery 属性选择器使用 XPath 表达式来选择带有给定属性的元素
- jQuery CSS 选择器可用于改变 HTML 元素的 CSS 属性

```
$("p") 选取 <p> 元素。
$("p.intro") 选取所有 class="intro" 的 <p> 元素。
$("p#demo") 选取所有 id="demo" 的 <p> 元素。
$("[href]") 选取所有带有 href 属性的元素。
$("[href='#']") 选取所有带有 href 值等于 "#" 的元素。
$("[href!='#']") 选取所有带有 href 值不等于 "#" 的元素。
$("[href$='.jpg']") 选取所有 href 值以 ".jpg" 结尾的元素。
$("p").css("background-color","red") 把所有 p 元素的背景颜色更改为红色
```



## jQuery示例

示例1：Get the <button> element with the class 'continue' and change its HTML to 'Next Step...'

```
$( "button.continue" ).html( "Next Step..." )
```


示例2：Show the #banner-message element that is hidden with display:none in its CSS when any button in #button-container is clicked.

```
var hiddenBox = $( "#banner-message" );
$( "#button-container button" ).on( "click", function( event ) {
hiddenBox.show();
});
```

示例3：Call a local script on the server /api/getWeather with the query parameter zipcode=97201 and replace the element #weather-temp's html with the returned text.

```
$.ajax({
url: "/api/getWeather",
data: {
zipcode: 97201
},
success: function( result ) {
$( "#weather-temp" ).html( "<strong>" + result + "</strong> degrees" );
}
});
```
## AJAX
- AJAX = 异步 JavaScript 和 XML。
- AJAX 是一种用于创建快速动态网页的技术。
- 通过在后台与服务器进行少量数据交换，AJAX 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。
- 传统的网页（不使用 AJAX）如果需要更新内容，必需重载整个网页面。
- XMLHttpRequest 是 AJAX 的基础，所有现代浏览器（IE7+、Firefox、Chrome、Safari 以及 Opera）均内建 XMLHttpRequest 对象。
- XMLHttpRequest 用于与服务器交换数据。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。
- 通过 jQuery AJAX 方法，能够使用 HTTP Get 和 HTTP Post 从远程服务器上请求文本、HTML、XML 或 JSON - 同时能够把这些外部数据直接载入网页的被选元素中。

## jQuery中的AJAX方法

load() 方法从服务器加载数据，并把返回的数据放入被选元素中。
$.get() 方法通过 HTTP GET 请求从服务器上请求数据。
$.post() 方法通过 HTTP POST 请求从服务器上请求数据。
$.ajax() 返回其创建的 XMLHttpRequest 对象。该方法是 jQuery 底层 AJAX 实现。


# jQuery验证用户名和密码实践



login.html文件代码如下


```
<!DOCTYPE html>
<head>  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />  
    <title>登录示例</title>  
</head>  
<body>  
    <h1>用户登录</h1>     
    <input type="text" required="required" placeholder="用户名" name="user_name"></input>  
    <input type="password" required="required" placeholder="密码" name="user_pwd"></input> 
    <div id="errormessage"></div>
    <button id="login_button" type="button">登录</button>     
</body>  
</html>
```

添加ajax代码如下


```

$("#login_button").click(function(){
    $.post("login.php",
        {
            "name":$("#username").val(),
            "password":$("#password").val()
        },
        //回调函数
        function(data){
            var json=data[0];
            if(json.success == 0){
                $("#errormessage").text("用户名或密码错误");
            }
            else if(json.success== 1){
                window.location.href="success.html";
            }
        }
    )
})

```







