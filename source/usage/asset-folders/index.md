---
title: 资源文件夹
date: 2021-10-21 20:42:34
---

资源（Asset）代表 source 文件夹中除了文章以外的所有文件，例如图片、CSS、JS 文件等。比方说，如果你的 Hexo 项目中只有少量图片，那最简单的方法就是将它们放在 source/images 文件夹中。然后通过类似于 `![](/images/image.jpg)`的方法访问它们。

对于那些想要更有规律地提供图片和其他资源以及想要将他们的资源分布在各个文章上的人来说，Hexo 也提供了更组织化的方式来管理资源。这个稍微有些复杂，但是它是资源管理非常方便的功能，可以用过将 _config.yml 文件中的`post_asset_folder`选项设为 true 来打开。

```yml _config.yml
post_asset_folder: true
```

当资源文件管理功能打开后，Hexo 将会在你每一次通过`heox new [layout] <title>`命令创建新文章时自动创建一个文件夹。这个资源文件夹将会有与这个文章文件一样的名字。将所有与你的文章有关的资源放在这个关联文件夹中之后，你可以通过相对路径来引用它们，这样你就得到了一个更简单而且方便得多的工作流。

随着标签插件被加入到核心代码中，你可以更简单地在文章中引用你的资源。

```
{% asset_path filename %}
{% asset_img [class names] slug [width] [height] [title text [alt text]] %}
{% asset_link filename [title] [escape] %}
```

比如说，当你打开文章资源文件夹功能后，你把一个 example.jpg 图片放在了你的资源文件夹中，如果通过使用相对路径的常规 Markdown 语法 `![](example.jpg)`，它不会出现在首页上，但是它会在文章中按你期待的方式工作。

正确的引用图片方式是使用下面的标签插件而不是 Markdown：

```
{% asset_img example.jpg This is an example image %}
```

通过这种方式，图片将会同时出现在文章和主页以及归档页中。

