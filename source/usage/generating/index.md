---
title: 生成文件
date: 2021-10-21 20:43:23
---

使用 Hexo 生成静态文件快速而且简单。

```
hexo generate
```

### 监视文件

Hexo 能够监视文件变动并立即重新生成静态文件，在生成时会比对文件的 SHA1 总和检验码（checksum），只有变动的文件才会写入。

```
hexo generate --watch
```

### 自动部署

你可执行下列的其中一个命令，让 Hexo 在生成完毕后自动部署网站，两个命令的作用是相同的。

```
hexo generate --deploy
hexo deploy --generate
```

上面两个命令可以简写为：

```
hexo g -d
hexo d -g
```
