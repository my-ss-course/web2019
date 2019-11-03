# HTML是什么
超文本标记语言（英语：HyperText Markup Language，简称：HTML）是一种用于创建网页的标准标记语言。
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <!--  CSS引用 -->
        <!--  必要的JS引用 -->
        <title>文档标题</title>
    </head>
    <body>
        <h1>一行文字</h1>
        <p>一个段落</p>
    </body>
    <!--  JS引用 -->
</html>
```

## HTML中的行内元素常用标签
###  **a**
* `<a>`标签定义超链接，用于从一张页面链接到另一张页面
*  href 属性指示链接的目标
*  示例：`<a href="路径">内容</a>`
* 绝对路径：
* 相对路径：
### img
### input 
### select 
### span 
### br 
### b 
### strong
### button

### 特点
* 和其他元素都在一行 
* 宽度只与内容有关，设宽度无效 
* 行内元素只能包含文本或其他行内元 素，不能包含块级元素


## HTML中的块级元素常用标签
### h 
### p 
### ul 
### ol 
### dl 
### p 
### div
### table
### form
### hr
### pre
### blockquote

### 特点
* 总是从新的一行开始
* 高度、宽度都是可控的 
* 宽度没有设置时，默认为100%
* 块级元素中可以包含块级元素和行内元素



# 实践内容
**任务要求：根据给定的PSD格式文件的界面原图，制作Web页面**

![](/images/Html/01_登录首页.jpg)

![](/images/Html/登录web效果图.png)
**需要了解Photoshop的以下操作
* 图层管理
* 切图操作
* 测量尺寸

## 实践过程
[psd原图下载](http://webdev.zhangqx.com/doc/01_登录首页.psd)
**1、创建目录结构及相应的文件**
*****
|--- css

|--- |--- style.css

|--- images

|--- index.html

*****
**2、编写index.html文件主体代码**
```
<html >
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>教学课件管理系统--北京大学软件与微电子学院</title>
</head>
<body>

</body>
</html>
```
**3、设置页面背景**
在Photoshop中，将界面的背景图截取出来。
![](/images/Html/登录背景01.png)
保存为jpg格式图片，文件名为“bj.jpg”，如下图所示，
![](/images/Html/登录首页背景.jpg)
将该文件保存到images文件夹内
*****
|--- css

|--- |--- style.css

|--- images

|--- |--- bj.jpg

|--- index.html

*****
在index.html的body中增加一个div，代码如下：
```
<div id="container">
<div class="login">
</div>
</div>
```
在html文件的head引入css样式文件。如下所示
`<link rel="stylesheet" type="text/css" href="css/style.css" />`
修改"style.css"文件，设置页面背景
```
/*-----------------------------全局样式-------------------------------------*/
*{margin:0;padding:0}
li{list-style:none}
img{vertical-align:top;border:none}
legend{display:none}
fieldset{border:none}
a{text-decoration:none}
a:hover,a:active{text-decoration:none}
.clear {clear: both; }

/*-----------------------------登录页面-------------------------------------*/
body{font:12px/1.5 Microsoft YaHei;position:relative;margin:0 auto;color:#000}
#container{
width:960px;
box-shadow: 0 0 15px #999999;
margin: 0 auto;
overflow-x: hidden;
position: relative;
}

.login{background:#0c7fc2 url(/images/Html/bg.jpg) no-repeat center top ;height:600px}
```
效果图如下所示
![](/images/Html/登录背景01_01.png)
**4、添加LOGO**

![](/images/Html/logo.png)
```
<div id="container">
<div class="login">
<div class="login_hd">
</div>
</div>
</div>
```

```
.login_hd{background:url(/images/Html/logo.png) no-repeat;float:left;margin:20px 20px 0;width:423px;height:57px;}
```

![](/images/Html/登录背景01_02.png)


**5、添加登录框背景**
![](/images/Html/banner.gif)
![](/images/Html/login_bg.png)
```
<div id="container">
<div class="login">
<div class="login_hd">
</div>
<div class="clear">
</div>
<div class="login_banner">
</div>
<div class="login_main">
</div>
</div>
</div>
```
```
.login_banner{background:url(/images/Html/banner.gif) no-repeat;float:left;margin:210px 80px 0;width:310px;height:53px;}
.login_main{position:relative; background:url(/images/Html/login_bg.png) no-repeat;float:right;margin:110px 50px 50px;width:390px;height:240px;}
```
![](/images/Html/登录背景01_03.png)

**6、添加表单**
![](/images/Html/login_btn.gif)
```
<div id="container">
<div class="login">
<div class="login_hd">
</div>
<div class="clear">
</div>
<div class="login_banner">
</div>
<div class="login_main">
<div class="login_help">
<a href="#">使用帮助</a>
</div>
<form action="#" method="post" class="login_form">
<fieldset>
<legend>登录表单</legend>
<div class="username"><input name="" type="text" placeholder=" 学院邮箱" /></div>
<div class="password"><input name="" type="password" placeholder=" 密码" /></div>
<div class="login_btn"><input name="" type="button" value="登录" /></div>
</fieldset>
</form>
</div>
</div>
</div>
```

```
.login_help{float:right;margin:6px -16px 10px;width:100px;height:30px;font-size:14px;color:#1e7bbd}
.login_help a{color:#0101ff}
.login_form{width:272px;height:170px;padding:27px 28px 0 26px;color:#000101;position:relative; }
.username{height:57px;margin:52px 90px 13px}
.password{height:57px;margin:-25px 90px 13px;}
.username input,.password input{width:176px;height:32px;border:0;color:#999;font-size:14px;line-height:32px}
.username input{position:absolute; top:87px; left:150px; }
.password input{position:absolute; top:134px; left:150px; }
.login_btn{text-align:center;height:42px;margin:0;position:absolute; top:170px; left:150px; }
.login_btn input{background:url(/images/Html/login_btn.gif) no-repeat;border:0;width:68px;height:42px;cursor:pointer;text-indent:-9999px;*text-indent:0;*line-height:9999px;overflow:hidden}
```

![](/images/Html/登录背景01_04.png)
**7、添加附件文字内容**

```
<div id="container">
<div class="login">
<div class="login_hd">
</div>
<div class="clear">
</div>
<div class="login_banner">
</div>
<div class="login_main">
<div class="login_help">
<a href="#">使用帮助</a>
</div>
<form action="#" method="post" class="login_form">
<fieldset>
<legend>登录表单</legend>
<div class="username"><input name="" type="text" placeholder=" 学院邮箱" /></div>
<div class="password"><input name="" type="password" placeholder=" 密码" /></div>
<div class="login_btn"><input name="" type="button" value="登录" /></div>
</fieldset>
</form>
<div class="guest">用户名或密码错误！</div>
<div class="forget"><a href="#">密码找回?</a></div>
<div class="first">首次登陆，请使用“密码找回”功能，初始化您的密码！</div>
</div>
</div>
</div>
```

```
.guest{float:left;margin:0px 20px 0;height:30px;font-size:14px;position:absolute; top:200px; left:0px; width:350px;text-align:center;color:#f00}
.guest a{color:#0101ff}
.forget{float:right;margin:0px 20px 0;height:30px;font-size:14px;position:absolute; top:175px; left:250px; }
.forget a{color:#ff0000}
.first{float:right;margin:10px 0px 0;width:350px;height:50px;color:#fff;position:absolute; top:230px; left:40px;}

```
![](/images/Html/登录背景01_05.png)

## 本实践项目完整代码
**index.html 文件**
```
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<title>教学课件管理系统--北京大学软件与微电子学院</title>
<link rel="stylesheet" type="text/css" href="css/style.css"/>
</head>
<body>
<div id="container">
<div class="login">
<div class="login_hd">
</div>
<div class="clear">
</div>
<div class="login_banner">
</div>
<div class="login_main">
<div class="login_help">
<a href="#">使用帮助</a>
</div>
<form action="#" method="post" class="login_form">
<fieldset>
<legend>登录表单</legend>
<div class="username"><input name="" type="text" placeholder=" 学院邮箱" /></div>
<div class="password"><input name="" type="password" placeholder=" 密码" /></div>
<div class="login_btn"><input name="" type="button" value="登录" /></div>
</fieldset>
</form>
<div class="guest">用户名或密码错误！</div>
<div class="forget"><a href="#">密码找回?</a></div>
<div class="first">首次登陆，请使用“密码找回”功能，初始化您的密码！</div>
</div>
</div>
</div>
</body>
</html>
```
*****
*****
**style.css 文件**
```

/*-----------------------------全局样式-------------------------------------*/

*{margin:0;padding:0}
li{list-style:none}
img{vertical-align:top;border:none}
legend{display:none}
fieldset{border:none}
a{text-decoration:none}
a:hover,a:active{text-decoration:none}
.clear {clear: both; }

/*-----------------------------登录页面-------------------------------------*/

body{font:12px/1.5 Microsoft YaHei;position:relative;margin:0 auto;color:#000}
#container{
width:960px;
box-shadow: 0 0 15px #999999;
margin: 0 auto;
overflow-x: hidden;
position: relative;
}

.login{background:#0c7fc2 url(/images/Html/bg.jpg) no-repeat center top ;height:600px}

.login_hd{background:url(/images/Html/logo.png) no-repeat;float:left;margin:20px 20px 0;width:423px;height:57px;}

.login_banner{background:url(/images/Html/banner.gif) no-repeat;float:left;margin:210px 80px 0;width:310px;height:53px;}
.login_main{position:relative; background:url(/images/Html/login_bg.png) no-repeat;float:right;margin:110px 50px 50px;width:390px;height:240px;}


.login_help{float:right;margin:6px -16px 10px;width:100px;height:30px;font-size:14px;color:#1e7bbd}
.login_help a{color:#0101ff}
.login_form{width:272px;height:170px;padding:27px 28px 0 26px;color:#000101;position:relative; }
.username{height:57px;margin:52px 90px 13px}
.password{height:57px;margin:-25px 90px 13px;}
.username input,.password input{width:176px;height:32px;border:0;color:#999;font-size:14px;line-height:32px}
.username input{position:absolute; top:87px; left:150px; }
.password input{position:absolute; top:134px; left:150px; }
.login_btn{text-align:center;height:42px;margin:0;position:absolute; top:170px; left:150px; }
.login_btn input{background:url(/images/Html/login_btn.gif) no-repeat;border:0;width:68px;height:42px;cursor:pointer;text-indent:-9999px;*text-indent:0;*line-height:9999px;overflow:hidden}


.guest{float:left;margin:0px 20px 0;height:30px;font-size:14px;position:absolute; top:200px; left:0px; width:350px;text-align:center;color:#f00}
.guest a{color:#0101ff}
.forget{float:right;margin:0px 20px 0;height:30px;font-size:14px;position:absolute; top:175px; left:250px; }
.forget a{color:#ff0000}
.first{float:right;margin:10px 0px 0;width:350px;height:50px;color:#fff;position:absolute; top:230px; left:40px;}
```

[项目示例代码下载](http://webdev.zhangqx.com/doc/web01.zip)

## 课后练手任务
自行到网络上下载免费或收费的用户登录界面PSD格式文件。并制作成Web格式页面。
![](/images/Html/后台用户登录psd文件.png)


