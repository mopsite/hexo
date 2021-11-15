---
title: 基本操作
date: 2021-10-20 18:00:30
---

你可以执行下列命令来创建一篇新文章或新页面。

```
hexo new [layout] <title>
```

你可以在命令中指定文章的布局（layout），默认为`post`，可以通过修改 _config.yml 中的`default_layout`参数来指定默认布局。

### 布局

Hexo 有三种默认布局：post、page 和 draft。在创建这三种不同类型的文件时，它们将会被保存到不同的路径。而你自定义的其他布局和 post 相同，都将储存到 source/_posts 文件夹。

|布局|路径|
|--|--|
|post|source/_posts|
|page|source|
|draft|source/_drafts|

### 文件名称

Hexo 默认以标题作为文件名称，但你可以编辑 _config.yml 中的`new_post_name`参数来改变默认的文件名称，举例来说，设为`:year-:month-:day-:title.md`可让你更方便的通过日期来管理文章。

|变量|描述|
|--|--|
|:title|标题（小写，空格将会被替换为短横线）|
|:year|建立的年份，比如 2015|
|:month|建立的月份（有前导 0），比如 04|
|:i_month|建立的月份（无前导 0），比如 4|
|:day|建立的日期（有前导 0），比如 07|
|:i_day|建立的日期（无前导 0），比如 7|

### 草稿

刚刚提到了 Hexo 的一种特殊布局：draft，这种布局在建立时会被保存到 source/_drafts 文件夹，你可以通过`publish`命令将草稿移动到 source/_posts 文件夹，该命令的使用方式与`new`十分类似，你也可以在命令中使用`layout`参数来指定布局。

```
hexo publish [layout] <title>
```

草稿默认不会显示在页面中，你可以在执行时加上`--draft`参数，或是在 _config.yml 中把`renter_drafts`参数设为 true 来预览草稿。

### 模板

在新建文章时，Hexo 会根据 scaffolds 文件夹内相对应的模板文件来建立文章，例如：

```
hexo new photo "My Gallery"
```

在执行这行指令时，Hexo 会尝试在 scaffolds 文件夹中寻找 photo.md，并根据其内容建立文章，以下是你可以在模板中使用的变量：

|变量|描述|
|--|--|
|layout|布局|
|title|标题|
|date|文件建立日期|

{%note info no-icon%}
Hexo 支持以任何格式书写文章，只要安装了相应的渲染插件。

例如，Hexo 默认安装了 hexo-renderer-marked 和 hexo-renderer-ejs，因此你不仅可以用 Markdown 写作，还可以用 EJS 写作。如果你安装了 hexo-renderer-pug，你甚至可以用 Pug 模板语言书写文章。

只需要将文章的扩展名从 md 改成 ejs，Hexo 就会使用 hexo-renderer-ejs 渲染这个文件，其他格式同理。
{%endnote%}
