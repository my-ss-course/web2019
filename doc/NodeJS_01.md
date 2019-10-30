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


## 示例程序

```
var http = require('http');
server = http.createServer(function (req, res) {
res.writeHeader(200, {"Content-Type": "text/plain"});
res.end("Hello World\n");
});
server.listen(8000);
console.log("httpd start @8000");
```
## Express模块

# NodeJS+Express+Mysql实现用户登录




