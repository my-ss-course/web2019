**开发环境说明**

- PHP 5.4
- MySQL 5.5
- ThinkPHP 5.0
- CentOS Linux 7.2
- Nginx 1.10.10
- 宝塔Linux主机管理软件 7.0.1
- phpMyAdmin 4.4


## 一、创建ThinkPHP站点

为了方便，使用宝塔工具创建ThinkPHP站点，并将域名demo1023.zhangqx.com解析到该服务器IP

![](/images/thinkphp/01@2x.png)


创建成功后的目录结构如下图所示

![](/images/thinkphp/02@2x.png)

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


## 二、设计登录静态页面







## 三、创建数据库

## 四、实现登录功能

## 五、显示用户列表








