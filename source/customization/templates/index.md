---
title: 模板
date: 2021-10-22 13:01:09
---

模板决定了网站内容的呈现方式，每个主题至少都应包含一个 index 模板，以下是每个页面对应的模板名称：

|模板|用途|回退|
|--|--|--|
|index|首页||
|post|文章|index|
|page|分页|index|
|archive|归档|index|
|category|分类归档|archive|
|tag|标签归档|archive|

### 布局（Layout）

如果页面结构类似，例如两个模板都有页首（Header）和页脚（Footer），你可以考虑通过「布局」让两个模板共享相同的结构。一个布局文件必须要能显示`body`变量的内容，如此一来模板的内容才会被显示，举例来说：

```ejs index.ejs
index
```

```ejs layout.ejs
<!DOCTYPE html>
<html>
  <body><%- body %></body>
</html>
```

生成：

```html
<!DOCTYPE html>
<html>
  <body>
    index
  </body>
</html>
```

每个模板都默认使用 layout 布局，你可以在 Front-matter 指定其他布局，或是设为 false 来关闭布局功能，你甚至可以在布局中再使用其他布局来建立嵌套布局。

### 布局模板（Partial）

布局模板让你在不同模板之间共享相同的组件，例如页首（Header）、页脚（Footer）或侧边栏（Sidebar）等，可利用布局模板功能分割为独立文件，让维护更加便利。举例来说：

```ejs partial/header.ejs
<h1 id="logo"><%= config.title %></h1>
```

```ejs index.ejs
<%- partial('partial/header') %>
<div id="content">Home page</div>
```

生成：

```html
<h1 id="logo">My Site</h1>
<div id="content">Home page</div>
```

你还可以在局部模板中指定局部变量并使用。

```ejs partial/header.ejs
<h1 id="logo"><%= title %></h1>
```

```ejs index.ejs
<%- partial('partial/header', {title: 'Hello World'}) %>
<div id="content">Home page</div>
```

生成：

```html
<h1 id="logo">Hello World</h1>
<div id="content">Home page</div>
```

### 优化

如果你的主题太过于复杂，或是需要生成的文件量太过于庞大，可能会大幅降低性能。除了简化主题外，你可以考虑 Hexo 2.7 新增的局部缓存（Fragment Caching）功能。

本功能借鉴于 [Ruby on Rails](https://guides.rubyonrails.org/caching_with_rails.html#fragment-caching)，它储存局部内容，下次便能直接使用缓存内容，可以减少文件夹查询并让生成速度更快。

它可用于页首、页脚、侧边栏等文件不常变动的位置，举例来说：

```
<%- fragment_cache('header', function(){
  return '<header></header>';
});
```

如果你使用局部模板的话，可以更简单：

```
<%- partial('header', {}, {cache: true});
```
