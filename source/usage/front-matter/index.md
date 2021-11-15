---
title: Front Matter
date: 2021-10-21 20:40:28
---

Front-matter 是文件最上方以`---`分隔的区域，用于指定单个文件的变量，举例来说：

```
---
title: Hello World
date: 2021/10/14 13:19:47
---
```

### 参数

以下是预先定义的参数，你可以在模板中使用这些参数值并加以利用。

|参数|描述|默认值|
|--|--|--|
|layout|布局|_config.yml 中的 `dafault_layout`|
|title|标题|文章的文件名|
|date|建立日期|文件建立日期|
|updated|更新日期|文件更新日期|
|comments|开启文章的评论功能|true|
|tags|标签（不适用于分页）||
|categories|分类（不适用于分页）||
|permalink|覆盖文章网址||
|excerpt|页面摘录纯文本||
|disableNunjucks|启用后将禁用 Nunjucks 标签和标签插件的渲染||
|lang|覆盖自动检测的语言|继承自 _config.yml|

### 布局

默认的布局是 post，它和 _config.yml 中的`default_layout`选项值一致。当一篇文章禁用了布局（`layout: false`），就不会再被主题处理。然而，它仍然会被任何可用的渲染器渲染。如果一篇文章采用 Markdown 书写，并且安装了 Markdown 渲染器，它将会被渲染成 HTML 文件。

无论什么布局，[标签插件](tag-plugins/) 都会被渲染，除非禁用了渲染器或者`disableNunjucks`选项。

### 分类和标签

只有文章支持分类和标签，你可以在 Front-matter 中设置。在其他系统中，分类和标签听起来很接近，但是在 Hexo 中两者有着明显的差别：分类具有顺序性和层次性，也就是说`Foo, Bar`不等于`Bar, Foo`；而标签没有顺序和层次。

```
---
categories:
- Diary
tags:
- PS3
- Games
---
```

{%note danger no-icon%}
如果你有过使用 WordPress 的经验，就很容易误解 Hexo 的分类方式。WordPress 支持对一篇文章设置多个分类，而且这些分类可以是同级的也可以是父子分类。但是 Hexo 不支持指定多个同级分类。下面的指定方法：

```
categories:
  - Diary
  - Life
```

会使分类 Lift 称为 Diary 的子分类，而不是并列分类。因此，有必要为你的文章选择尽可能准确的分类。如果你需要为文章添加多个分类，可以尝试以下方法：

```
categories:
- [Diary, PlayStation]
- [Diary, Games]
- [Life]
```

此时，这篇文章同时包括三个分类：PlayStation 和 Games 分别是父分类 Diary 的子分类。同时 Life 是一个没有子分类的分类。
{%endnote%}

### JSON Front-matter

除了 YAML 外，你也可以使用 JSON 来编写 Front-matter，只要将`---`换成`;;;`即可：

```
title: Hello World
date: 2021/10/14 13:19:47
;;;
```

