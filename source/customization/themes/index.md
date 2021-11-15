---
title: 主题
date: 2021-10-22 13:00:55
---

创建 Hexo 主题非常容易，你只要在 themes 文件夹内，新增一个任意名称的文件夹，并修改 _config.yml 内的`theme`设定，即可切换主题。一个主题可能会有以下结构：

```
.
├── _config.yml
├── languages
├── layout
├── scripts
└── source
```

### _config.yml

主题的配置文件。和 Hexo 配置文件不同，主题配置文件修改时会自动更新，无需重启 Hexo Server。

### languages

语言文件夹。请参见 [国际化（i18n）](../internationalization)。

### layout

布局文件夹。用于主题的模板文件，决定了网站内容的呈现方式。Hexo 内建 [Swing](https://github.com/node-swig/swig-templates) 模板引擎，你可以另外安装插件来获得 [EJS](https://github.com/hexojs/hexo-renderer-ejs)、[Haml](https://github.com/hexojs/hexo-renderer-haml)、[Jade](https://github.com/hexojs/hexo-renderer-jade) 或 [Pug](https://github.com/maxknee/hexo-render-pug) 支持，Hexo 根据模板文件的扩展名来决定所使用的模板引擎，例如：

```
layout.ejs   - 使用 EJS
layout.swig  - 使用 Swig
```

你可以参考 [模板](../templates) 以获得更多信息。

### scripts

脚本文件夹。在启动时，Hexo 会载入此文件夹内的 JavaScript 文件，请参见 [插件](../plugins) 以获得更多信息。

### source

资源文件夹，除了模板以外的资源，例如 CSS、JavaScript 文件等，都应该放在这个文件夹中。文件或文件夹开头名称为`_`或隐藏的文件会被忽略。

如果文件可以被渲染的话，会经过解析然后储存到 public 文件夹，否则会直接拷贝到 public 文件夹。
