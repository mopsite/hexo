---
title: 服务器
date: 2021-10-21 20:43:08
---

### hexo-server

Hexo 3.0 把服务器独立成了单独的模块，你必须先安装 [hexo-server](https://github.com/hexojs/hexo-server) 才能使用。

```
npm install hexo-server --save
```

安装完成后，输入以下命令启动服务器，你的网站会在 http://localhost:4000 下启动。在服务器启动期间，Hexo 会监视文件变动并自动更新，你无需重启服务器。

```
hexo server
```

如果你想要更改端口，或是在执行时遇到了 EADDRINUSE 错误，可以在执行时使用`-p`选项指定其他端口，如下：

```
hexo server -p 5000
```

#### 静态模式

在静态模式下，服务器只处理 public 文件夹内的文件，而不会处理文件变动，在执行时，你应该先自行执行`hexo generate`，此模式通常用于生产环境（production mode）下。

```
hexo server -s
```

#### 自定义 IP

服务器默认运行在`0.0.0.0`，你可以覆盖默认的 IP 设置，如下：

```
hexo server -i 192.168.1.1
```

指定这个参数后，你就只能通过该 IP 才能访问网站。例如，对于一台使用无线网络的笔记本电脑，除了指向本机的`127.0.0.1`外，通常还有一个`192.168.*.*`的局域网 IP，如果像上面那样使用`-i`参数，就不能用`127.0.0.1`来访问站点了。对于有公网 IP 的主机，如果你指定一个局域网 IP 作为`-i`参数值，那就就无法通过公网来访问站点。

### Pow

[Pow](http://pow.cx/) 是一个 Mac 系统上的零配置 Rack 服务器，它也可以作为一个简单易用的静态文件服务器来使用。

#### 安装

```
curl get.pow.cs | sh
```

#### 设置

在 ~/.pow 文件夹建立链接（symlink）。

```
cd ~/.pow
ln -s /path/to/myapp
```

你的网站将会 http://myapp.dev 下运行，网址根据链接名称而定。
