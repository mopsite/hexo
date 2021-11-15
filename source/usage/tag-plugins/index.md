---
title: 标签插件
date: 2021-10-21 20:42:09
---

标签插件和 Front-matter 中的标签不同，它们是用于在文章中快速插入特定内容的插件。虽然你可以使用任何格式书写你的文章，但是标签插件永远可用，且语法也都是一致的。

标签插件不能在 Markdown 语法中使用，例如`[]({% post_path Lorem-ipsum %})`是不支持的。

### 引用块

在文章中插入引言，可包含作者、来源和标题。别名：quote。

```
{% blockquote [author[, source]] [link] [source_link_title] %}
content
{% endblockquote %}
```

没有提供参数，则只输出普通的块引用：

{%tabs quote1%}
<!-- tab 代码 -->
```
{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}
<!-- endtab -->
{%endtabs%}

引用书上的句子：

{%tabs quote2%}
<!-- tab 代码 -->
```
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
<!-- endtab -->
{%endtabs%}

引用网络上的文章：

{%tabs quote3%}
<!-- tab 代码 -->
```
{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}
<!-- endtab -->
{%endtabs%}

### 代码块

在文章中插入代码。别名：code。

```
{% codeblock [title] [lang:language] [url] [link text] [additional options] %}
code snippet
{% endcodeblock %}
```

其他选项使用键值对的形式，例如：`line_number:false first_line:5`。

|选项|描述|默认值|
|--|--|--|
|line_number|显示行号|true|
|highlight|启用代码高亮|true|
|first_line|指定第一行号码|1|
|mark|显示特定行，每个值由逗号分隔，使用破折号指定数字范围。例如：`mark:1,4-7,10`||
|wrap|将代码块包裹在表格元素（`<table>`）中|true|

普通的代码块：

{%tabs code1%}
<!-- tab 代码 -->
```
{% codeblock %}
alert('Hello World!');
{% endcodeblock %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% codeblock %}
alert('Hello World!');
{% endcodeblock %}
<!-- endtab -->
{%endtabs%}

指定语言：

{%tabs code2%}
<!-- tab 代码 -->
```
{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}
<!-- endtab -->
{%endtabs%}

附加说明：

{%tabs code3%}
<!-- tab 代码 -->
```
{% codeblock Array.map %}
array.map(callback[, thisArg])
{% endcodeblock %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% codeblock Array.map %}
array.map(callback[, thisArg])
{% endcodeblock %}
<!-- endtab -->
{%endtabs%}

附加说明和网址：

{%tabs code4%}
<!-- tab 代码 -->
```
{% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcodeblock %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcodeblock %}
<!-- endtab -->
{%endtabs%}

### 反引号代码块

另一种形式的代码块，不同的是它使用三个反引号来包裹。

````
``` [language] [title] [url] [link text] code snippet ```
````

### 框架

在文章中插入框架。

```
{% iframe url [width] [height] %}
```

利用这个可以嵌入音乐和视频：

```
{% iframe http://v.youku.com/v_show/id_XOTIxNDYzODU2.html 930 542 %}
```

### 图片

在文章中插入指定大小的图片。

```
{% img [class names] /path/to/image [width] [height] '"title text" "alt text"' %}
```

### 链接

在文章中插入链接，并自动给外部链接添加`target="_blank"`属性。

```
{% link text url [external] [title] %}
```

### 代码文件

插入 source/downloads/code 文件夹内的代码文件，该文件夹不是固定的，取决于你在 _config.yml 文件中`code_dir`的配置。

```
{% include_code [title] [lang:language] [from:line] [to:line] path/to/file %}
```

嵌入 test.js 文件全文:

```
{% include_code lang:javascript test.js %}
```

只嵌入第 3 行：

```
{% include_code lang:javascript from:3 to:3 test.js %}
```

嵌入第 5-8 行：

```
{% include_code lang:javascript from:5 to:8 test.js %}
```

嵌入第 5 行至文件结束：

```
{% include_code lang:javascript from:5 test.js %}
```

嵌入第 1-8 行：

```
{% include_code lang:javascript to:8 test.js %}
```

### 引用文章

引用其他文章的链接。

```
{% post_link filename [title] [escape] %}
```

在使用此标签时，可以忽略文章文件所在的路径或永久链接。例如，在文章中使用`{% post_link how-to-bake-a-cake %}`时，只需要一个名为 how-to-bake-a-cake.md 的文章文件即可。即使这个文件位于站点文件夹的 source/posts/2015-02-my-family-holiday 目录下，或者文章的永久链接是 2018/en/how-to-bake-a-cake，都没有影响。

默认链接文字是文章的标题，你也可以自定义要显示的文本。

默认对文章的标题和自定义标题里的特殊字符进行转义。可以使用`escape`选项，禁止对特殊字符进行转义。

链接使用文章的标题：

{%tabs post_link1%}
<!-- tab 代码 -->
```
{% post_link intro %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% post_link intro %}
<!-- endtab -->
{%endtabs%}

链接使用自定义文字：

{%tabs post_link2%}
<!-- tab 代码 -->
```
{% post_link intro '通往文章的链接' %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% post_link intro '通往文章的链接' %}
<!-- endtab -->
{%endtabs%}

对标题的特殊字符进行转义：

{%tabs post_link3%}
<!-- tab 代码 -->
```
{% post_link intro 'How to use <b> tag in title' %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% post_link intro 'How to use <b> tag in title' %}
<!-- endtab -->
{%endtabs%}

禁止对标题的特殊字符进行转义：

{%tabs post_link4%}
<!-- tab 代码 -->
```
{% post_link intro '<b>bold</b> custom title' false %}
```
<!-- endtab -->
<!-- tab 效果 -->
{% post_link intro '<b>bold</b> custom title' false %}
<!-- endtab -->
{%endtabs%}

### 文章摘要和截断

在文章中使用`<!-- more -->`，那么`<!-- more -->`之前的文字将会被视为摘要。首页中将只出现这部分文字，同时这部分文字也会出现在正文之中。

{%note danger%}
摘要可能会被 Front-matter 中的`excerpt`覆盖。
{%endnote%}


