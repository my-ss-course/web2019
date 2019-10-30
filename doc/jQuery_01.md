
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


## jQuery

示例1：

```
$( "button.continue" ).html( "Next Step..." )
```


示例2：
```
var hiddenBox = $( "#banner-message" );
$( "#button-container button" ).on( "click", function( event ) {
  hiddenBox.show();
});
```

示例3：

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





