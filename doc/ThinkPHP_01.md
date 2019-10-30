**开发环境说明**

- PHP 5.4
- MySQL 5.5
- ThinkPHP 5.0
- CentOS Linux 7.2
- Nginx 1.10.10
- 宝塔Linux主机管理软件 7.0.1
- phpMyAdmin 4.4


[TOC]



## 一、创建ThinkPHP站点

为了方便，使用宝塔工具创建ThinkPHP站点，并将域名demo1023.zhangqx.com解析到该服务器IP

---


![](/images/thinkphp/01@2x.png)

---

创建成功后的目录结构如下图所示

![](/images/thinkphp/02@2x.png)

---

ThinkPHP官网的帮助文档中的目录结构如下：


```

project 应用部署目录
├─application 应用目录（可设置）
│ ├─common 公共模块目录（可更改）
│ ├─index 模块目录(可更改)
│ │ ├─config.php 模块配置文件
│ │ ├─common.php 模块函数文件
│ │ ├─controller 控制器目录
│ │ ├─model 模型目录
│ │ ├─view 视图目录
│ │ └─ ... 更多类库目录
│ ├─command.php 命令行工具配置文件
│ ├─common.php 应用公共（函数）文件
│ ├─config.php 应用（公共）配置文件
│ ├─database.php 数据库配置文件
│ ├─tags.php 应用行为扩展定义文件
│ └─route.php 路由配置文件
├─extend 扩展类库目录（可定义）
├─public WEB 部署目录（对外访问目录）
│ ├─static 静态资源存放目录(css,js,image)
│ ├─index.php 应用入口文件
│ ├─router.php 快速测试文件
│ └─.htaccess 用于 apache 的重写
├─runtime 应用的运行时目录（可写，可设置）
├─vendor 第三方类库目录（Composer）
├─thinkphp 框架系统目录
│ ├─lang 语言包目录
│ ├─library 框架核心类库目录
│ │ ├─think Think 类库包目录
│ │ └─traits 系统 Traits 目录
│ ├─tpl 系统模板目录
│ ├─.htaccess 用于 apache 的重写
│ ├─.travis.yml CI 定义文件
│ ├─base.php 基础定义文件
│ ├─composer.json composer 定义文件
│ ├─console.php 控制台入口文件
│ ├─convention.php 惯例配置文件
│ ├─helper.php 助手函数文件（可选）
│ ├─LICENSE.txt 授权说明文件
│ ├─phpunit.xml 单元测试配置文件
│ ├─README.md README 文件
│ └─start.php 框架引导文件
├─build.php 自动生成定义文件（参考）
├─composer.json composer 定义文件
├─LICENSE.txt 授权说明文件
├─README.md README 文件
├─think 命令行入口文件

```


- linux环境下，确保runtime目录有可写权限
- 5.0的部署建议是public目录作为web目录访问内容


---


**将域名解析到服务器主机IP**

![](/images/thinkphp/03@2x.png)

**确保域名被正确的解析到主机IP,可在本地机器通过ping命令来测试**

![](/images/thinkphp/04@2x.png)

**通过浏览器打开站点**

![](/images/thinkphp/05@2x.png)

在application/index/controller目录下的index.php文件内容如下：


```
<?php
namespace app\index\controller;

class Index
{
    public function index()
    {
        return '<style type="text/css">*{ padding: 0; margin: 0; } .think_default_text{ padding: 4px 48px;} a{color:#2E5CD5;cursor: pointer;text-decoration: none} a:hover{text-decoration:underline; } body{ background: #fff; font-family: "Century Gothic","Microsoft yahei"; color: #333;font-size:18px} h1{ font-size: 100px; font-weight: normal; margin-bottom: 12px; } p{ line-height: 1.6em; font-size: 42px }</style><div style="padding: 24px 48px;"> <h1>:)</h1><p> ThinkPHP V5<br/><span style="font-size:30px">十年磨一剑 - 为API开发设计的高性能框架</span></p><span style="font-size:22px;">[ V5.0 版本由 <a href="http://www.qiniu.com" target="qiniu">七牛云</a> 独家赞助发布 ]</span></div><script type="text/javascript" src="https://tajs.qq.com/stats?sId=9347272" charset="UTF-8"></script><script type="text/javascript" src="https://e.topthink.com/Public/static/client.js"></script><think id="ad_bd568ce7058a1091"></think>';
    }
}

```
将该文件的内容修改如下：
```
<?php
namespace app\index\controller;

class Index
{
    public function index()
    {
        return 'Hello World';
    }
}

```

 http://demo1023.zhangqx.com/  显示效果如下：
![](/images/thinkphp/06@2x.png)

ThinkPHP5.0在没有启用路由的情况下典型的URL访问规则是：


```
http://serverName/index.php（或者其它应用入口文件）/模块/控制器/操作/[参数名/参数值...]
```

![](/images/thinkphp/07@2x.png)

因此，http://demo1023.zhangqx.com/  与  http://demo1023.zhangqx.com/index.php/index/index/index/  是等价的


在Index控制器中增加一个login方法，代码如下：

```
<?php
namespace app\index\controller;

class Index
{
    public function index()
    {
        return 'Hello World';
    }
    
    public function login()
    {
        return 'Login';
    }
}
```
通过URL  http://demo1023.zhangqx.com/index.php/index/index/login/ 访问结果如下
![](/images/thinkphp/08@2x.png)


## 二、设计登录静态页面

每个模块的模板文件是独立的，为了对模板文件更加有效的管理，ThinkPHP对模板文件进行目录划分，默认的模板文件定义规则是：

```
视图目录/控制器名（小写）/操作名（小写）+模板后缀
```
默认的视图目录是模块的view目录，框架的默认视图文件后缀是.html。


创建模块视图目录view，原目录结构如下

```
application/
├── command.php
├── common.php
├── config.php
├── database.php
├── extra
│   └── queue.php
├── index
│   └── controller
│       └── Index.php
├── route.php
└── tags.php
```

在application目录下index目录（模块）下创建view目录（视图）,再创建index目录（控制器名），并新建login.html文件（方法名）。结果如下：

```
application/
├── command.php
├── common.php
├── config.php
├── database.php
├── extra
│   └── queue.php
├── index
│   ├── controller
│   │   └── Index.php
│   └── view
│       └── index
│           └── login.html
├── route.php
└── tags.php
```


login.html文件代码如下


```
<!DOCTYPE html>
<head>  
    <meta charset="UTF-8">  
    <title>登录示例</title>  
</head>  
<body>  
        <h1>用户登录</h1>  
        <form method="post">  
            <input type="text" required="required" placeholder="用户名" name="user_name"></input>  
            <input type="password" required="required" placeholder="密码" name="user_pwd"></input> 
            <button class="but" type="submit">登录</button>  
        </form>  
</body>  
</html>
```



在login方法中，调用fetch方法。代码如下


```
<?php
namespace app\index\controller;
use think\View;
use think\Controller;
class Index extends Controller
{
    public function index()
    {
        return 'Hello World';
    }
    
    public function login()
    {
        $view = new View();
    	return $view->fetch();
    }
}

```


访问http://demo1023.zhangqx.com/index.php/index/index/login/ 显示结果如下：
![](/images/thinkphp/10@2x.png)

## 三、配置数据库连接并创建表
在创建站点时，已经创建了数据库。先在Thinkphp的配置文件中配置数据库连接地址
修改application目录下的database.php文件


```
return [
    // 数据库类型
    'type'            => 'mysql',
    // 服务器地址
    'hostname'        => '127.0.0.1',
    // 数据库名
    'database'        => 'demo1023_zhangq',
    // 用户名
    'username'        => 'demo1023_zhangq',
    // 密码
    'password'        => '填写真实密码',
    // 端口
    'hostport'        => '',
    // 连接dsn
    'dsn'             => '',
    // 数据库连接参数
    'params'          => [],
    // 数据库编码默认采用utf8
    'charset'         => 'utf8',
    // 数据库表前缀
    'prefix'          => '',
    // 数据库调试模式
    'debug'           => true,
    // 数据库部署方式:0 集中式(单一服务器),1 分布式(主从服务器)
    'deploy'          => 0,
```



打开phpMyAdmin控制面板，在数据库中创建用户表。SQL语句如下：


```
DROP TABLE IF EXISTS `users`;

CREATE TABLE `users` (

`id` int(11) NOT NULL AUTO_INCREMENT COMMENT '用户id编号',

`user_name` varchar(155) NOT NULL COMMENT '用户名',

`user_pwd` varchar(50) NOT NULL COMMENT '用户密码（MD5处理后）',

PRIMARY KEY (`id`)

) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```

![](/images/thinkphp/11@2x.png)

![](/images/thinkphp/12.png)
同样的操作方式添加一个用户信息，用户名admin，密码admin（密码需要MD5加密）

```
insert into users(`user_name`,`user_pwd`) value('admin','21232f297a57a5a743894a0e4a801fc3');
```
![](/images/thinkphp/13.png)
![](/images/thinkphp/14.png)
![](/images/thinkphp/15.png)

## 四、实现登录功能

将登录页面的表单提交地址设置为index/dologin（index模块下的dologin方法）


```
<form method="post" action="{:url('index/dologin')}"> 
```


完整代码如下：


```
<!DOCTYPE html>
<head>  
    <meta charset="UTF-8">  
    <title>登录示例</title>  
</head>  
<body>  
        <h1>用户登录</h1>  
        <form method="post" action="{:url('index/dologin')}">  
        
            <input type="text" required="required" placeholder="用户名" name="user_name"></input>  
            <input type="password" required="required" placeholder="密码" name="user_pwd"></input>  
            <button class="but" type="submit">登录</button>  
        </form>  
</body>  
</html>
```

在index模块下，新建dologin方法



```
    public function doLogin()
	{
		$param = input('post.');
		if(empty($param['user_name'])){
			$this->error('用户名不能为空');
		}
		if(empty($param['user_pwd'])){
			$this->error('密码不能为空');
		}

		//验证用户名
		$has = db('users')->where('user_name',$param['user_name'])->find();
		if(empty($has)){	
			$this->error('用户名或密码错误');
		}

		// 验证密码
		if($has['user_pwd'] != md5($param['user_pwd'])){
			$this->error('用户名或密码错误');
		}

		// 记录用户登录信息
		cookie('user_id',$has['id'],3600); // 一个小时有效期
		cookie('user_name',$has['user_name'],3600);
		$this->redirect(url('index/index'));
		
	}
```



## 五、引入css样式
在Thinkphp中有一些全局常亮可以直接在view中使用。在index方法的view中可以打印出常量的具体值



```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
__ROOT__<br>
__STATIC__<br>
__JS__<br>
__CSS__<br>
</body>
</html>
```

修改index方法

```
public function index()
    {
        $view = new View();
    	return $view->fetch();
    }
```

页面显示效果
![](/images/thinkphp/16.png)
因此可以将css文件文件放到/public/static/css目录下，命名为login.css，代码如下


```
html{   
    width: 100%;   
    height: 100%;   
    overflow: hidden;   
    font-style: sans-serif;   
}   

body{   
    width: 100%;   
    height: 100%;   
    font-family: 'Open Sans',sans-serif;   
    margin: 0;   
    background-color: #4A374A;   
}   

#login{   
    position: absolute;   
    top: 50%;   
    left:50%;   
    margin: -150px 0 0 -150px;   
    width: 300px;   
    height: 300px;   
}   

#login h1{   
    color: #fff;   
    text-shadow:0 0 10px;   
    letter-spacing: 1px;   
    text-align: center;   
}   

h1{   
    font-size: 2em;   
    margin: 0.67em 0;   
}   

input{   
    width: 278px;   
    height: 18px;   
    margin-bottom: 10px;   
    outline: none;   
    padding: 10px;   
    font-size: 13px;   
    color: #fff;   
    text-shadow:1px 1px 1px;   
    border-top: 1px solid #312E3D;   
    border-left: 1px solid #312E3D;   
    border-right: 1px solid #312E3D;   
    border-bottom: 1px solid #56536A;   
    border-radius: 4px;   
    background-color: #2D2D3F;   
}   

.but{   
    width: 300px;   
    min-height: 20px;   
    display: block;   
    background-color: #4a77d4;   
    border: 1px solid #3762bc;   
    color: #fff;   
    padding: 9px 14px;   
    font-size: 15px;   
    line-height: normal;   
    border-radius: 5px;   
    margin: 0;   
}
```

在login.html中加入


```
<link rel="stylesheet" type="text/css" href="__CSS__/login.css"/> 
```


完整代码如下：

```
<!DOCTYPE html>
<head>  
    <meta charset="UTF-8">  
    <link rel="stylesheet" type="text/css" href="__CSS__/login.css"/> 
    <title>登录示例</title>  
</head>  
<body>  
	<div id="login">
        <h1>用户登录</h1>  
        <form method="post" action="{:url('index/dologin')}">  
            <input type="text" required="required" placeholder="用户名" name="user_name"></input>  
            <input type="password" required="required" placeholder="密码" name="user_pwd"></input>  
            <button class="but" type="submit">登录</button>  
        </form>
    </div>
</body>  
</html>
```

界面展示效果如下

![](/images/thinkphp/17@2x.png)

## 六、获取cookie值

在前端可以获取到cookie中的值
![](/images/thinkphp/19@2x.png)

```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
__ROOT__<br>
__STATIC__<br>
__JS__<br>
__CSS__<br>

{$Think.cookie.user_name} ，欢迎你！
</body>
</html>
```

![](/images/thinkphp/18.png)

