# NodeJS基础
## NodeJS是什么
- Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。
- Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型。
- Node 是一个让 JavaScript 运行在服务端的开发平台，它让 JavaScript 成为与PHP、Python、Perl、Ruby 等服务端语言平起平坐的脚本语言。
- Node可以在不新增额外线程的情况下，依然可以对任务进行并发处理 —— Node.js是单线程的。
- Node使用Module模块去划分不同的功能，以简化应用的开发。Modules模块有点像C++语言中的类库。每一个Node的类库都包含了十分丰富的各类函数，比如http模块就包含了和http功能相关的很多函数，可以帮助开发者很容易地对比如http,tcp/udp等进行操作，还可以很容易的创建http和tcp/udp的服务器。
- 发布于2009年5月，由Ryan Dahl开发，实质是对Chrome V8引擎进行了封装。

## NodeJS运行环境安装
可以在你自己的笔记本安装，也可以在Linux服务器上安装。

安装方法参见[Linux安装步骤](/doc/NodeJS_install.md)

## 示例程序

文件名app.js

```
var http = require('http');
server = http.createServer(function (req, res) {
res.writeHeader(200, {"Content-Type": "text/plain"});
res.end("Hello World\n");
});
server.listen(8000);
console.log("httpd start @8000");
```

通过以下命令可以运行该node程序

![](/images/NodeJS/09@2x.png)

通过浏览器可访问该web应用（需要在服务器的安全策略中开放8000端口）
![](/images/NodeJS/08@2x.png)

## Express框架
Express 是一个保持最小规模的灵活的 Node.js Web应用程序开发框架，为Web应用程序提供一组强大的功能。


假设已经安装了 Node.js，接下来为应用创建一个目录，然后进入此目录并将其作为当前工作目录


```
$ mkdir myapp
$ cd myapp
$ npm init
$ npm install express -g --save

```
过程截图如下:
![](/images/NodeJS/10@2x.png)
![](/images/NodeJS/11@2x.png)

新建index.js文件，程序代码如下
```
const express = require('express')
const app = express()

app.get('/', (req, res) => res.send('Hello World express!'))

app.listen(3000, () => console.log('Example app listening on port 3000!'))
```


运行程序

```
$ node index.js
```
通过浏览器访问web应用，需放行相应的端口。
![](/images/NodeJS/12.png)

## Express 应用程序生成器
参考地址：http://www.expressjs.com.cn/starter/generator.html


安装express-generator 

```
$  npm install express-generator --save -g
```

创建了一个名称为myapp2的Express应用。并且设置Pug模板引擎


```
$ express --view=pug myapp2

$ cd myapp2

$ npm install

$ DEBUG=myapp2:* npm start
```

![](/images/NodeJS/13@2x.png)

![](/images/NodeJS/14.png)


## Express路由

```
app.get('/', function (req, res) {
  res.send('Hello World!')
})
```

## 静态文件
为了提供诸如图像、CSS 文件和 JavaScript 文件之类的静态文件，请使用 Express 中的 express.static 内置中间件函数。

例如，通过如下代码就可以将 public 目录下的图片、CSS 文件、JavaScript 文件对外开放访问了：

app.use(express.static('public'))

现在，你就可以访问 public 目录中的所有文件了：

http://localhost:3000/images/kitten.jpg

http://localhost:3000/css/style.css

http://localhost:3000/js/app.js

http://localhost:3000/images/bg.png

http://localhost:3000/hello.html


# NodeJS+Express+Mysql实现用户登录

## 初始化工程




