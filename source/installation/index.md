---
title: 安装
date: 2021-10-20 17:56:11
---

安装 Hexo 相当简单，只需几分钟时间，只需要先安装下列应用程序即可：

- [Node.js](https://nodejs.org/zh-cn/)（Node.js 版本需不低于 10.13，建议使用 Node.js 12.0 及以上版本）
- [Git](https://git-scm.com/)

所有必备的应用程序安装完成后，即可使用 npm 全局安装 Hexo：

```
npm install -g hexo-cli
```

对于熟悉 npm 的进阶用户，可以仅局部安装 hexo 包：

```
npm install hexo
```

局部安装以后，可以使用以下两种方式执行 Hexo：

1. `npm hexo <command>`
2. 将 Hexo 所在目录下的`node_modules`添加到环境变量中即可直接使用`hexo <command>`：
  ```
  echo 'PATH="$PATH:./node_modules/.bin"' >> ~/.profile
  ```

{%note warning%}
强烈建议永远安装最新版本的 Hexo，以及推荐的 Node.js 版本。
{%endnote%}
