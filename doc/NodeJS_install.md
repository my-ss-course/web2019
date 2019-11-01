# Linux平台下安装NodeJS
## 下载安装文件
http://nodejs.cn/download/
![](/images/NodeJS/05.png)
## 安装步骤

### 将安装文件上传到某个目录，并解压 

![](/images/NodeJS/06@2x.png)

```
 tar -xvf node-v12.13.0-linux-x64.tar.xz
```
### 重命名文件夹并移动到/usr/local目录

```
 mv node-v12.13.0-linux-x64 /usr/local/nodejs
```
### 建立软链接

```
ln -s /usr/local/nodejs/bin/npm /usr/local/bin/
ln -s /usr/local/nodejs/bin/node /usr/local/bin/
```

### 检查安装结果
```
node  -v
```

![](/images/NodeJS/07@2x.png)

