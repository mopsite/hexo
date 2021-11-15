---
title: 配置
date: 2021-10-20 21:24:26
---

你可以在 _config.yml 文件中修改大部分的配置。

### 网站

|参数|描述|
|--|--|
|title|网站标题|
|subtitle|网站副标题|
|description|网站描述|
|keywords|网站的关键词。支持多个关键词。|
|author|你的名字|
|language|网站使用的语言。对于简体中文，不同的主题可能会有不同的值，常见的有`zh-Hans`和`zh-CN`。|
|timezone|网站时区。Hexo 默认使用你电脑的时区。一般，对于中国大陆地区可以使用`Asia/Shanghai`。|

{%note info no-icon%}
其中，`description`主要用于 SEO，告诉搜索引擎一个关于你站点的简单描述，通常建议在其中包含你网站的关键词。`author`参数用于主题显示文章的作者。
{%endnote%}

### 网址

|参数|描述|默认值|
|--|--|--|
|url|网址，必须以 http:// 或 https:// 开头||
|permalink|文章的永久链接格式|:year/:month/:day/:title/|
|permalink_defaults|永久链接中各部分的默认值||
|pretty_urls|改写永久链接的值来美化 URL||
|pretty_urls.trailing_index|是否在永久链接中保留尾部的 index.html|true|
|pretty_urls.trailing_html|是否在永久链接中保留尾部的 .html，对尾部的 index.html 无效|true|

{%note info no-icon%}
比如，一个页面的永久链接是 http://example.com/foo/bar/index.html ，设置为：

```yml
pretty_urls:
  trailing_index: false
```

此时页面的永久链接会变为 http://example.com/foo/bar/ 。
{%endnote%}

### 目录

|参数|描述|默认值|
|--|--|--|
|source_dir|资源文件夹，用来存放内容。|source|
|public_dir|公共文件夹，用来存放生成的站点文件。|public|
|tag_dir|标签文件夹。|tags|
|archive_dir|归档文件夹。|archives|
|category_dir|分类文件夹。|categories|
|code_dir|`source_dir`下的子目录，包含 code 文件夹。|downloads/code|
|i18n_dir|国际化（i18n）文件夹。|:lang|
|skip_render|跳过指定文件夹的渲染。匹配到的文件不会被改动，直接复制到 public 目录中。可以使用 [glob](https://github.com/micromatch/micromatch#extended-globbing) 表达式来匹配路径。||

{%note info no-icon%}
比如，设置了：

```yml
skip_render: "mypage/**/*"
```

会直接将 source/mypage 目录下的所有文件不做改动地输出到 public 目录下。

你也可以使用这种方法来跳过对指定文章文件的渲染，例如：

```yml
skip_render: "_posts/test-post.md"
```

这将会忽略对 test-post.md 的渲染。

如果你刚开始接触 Hexo，通常没有必要修改这部分的值。
{%endnote%}

### 写作

|参数|描述|默认值|
|--|--|--|
|new_post_name|新文章的文件名称|:title.md|
|default_layout|预设布局|post|
|titlecase|把标题转换为首字母大写|false|
|external_link|在新标签中打开链接||
|external_link.enable|启用在新标签中打开链接|true|
|external_link.field|对整个网站（site）生效或仅对文章（post）生效|site|
|external_link.exclude|需要排除的域名。主域名和子域名需分别配置||
|filename_case|把文件名转换为（1）小写或（2）大写|0|
|render_drafts|显示草稿|false|
|post_asset_folder|启动资源文件夹|false|
|relative_link|把链接改为与根目录的相对地址|false|
|future|显示未来的文章|true|
|highlight|代码块的设置，请参考 Highlight.js||
|prismjs|代码块的设置，请参考 PrismJS||

### 分类 & 标签

|参数|描述|默认值|
|--|--|--|
|default_category|默认分类|uncategorized|
|category_map|分类别名||
|tag_map|标签别名||

### 日期 / 时间格式

Hexo 使用 [Moment.js](https://momentjs.com/) 来解析和显示时间。

|参数|描述|默认值|
|--|--|--|
|date_format|日期格式|YYYY-MM-DD|
|time_format|时间格式|HH:mm:ss|
|updated_option|当 Front Matter 中没有指定`updated`时的取值|mtime|

{%note info no-icon%}
`updated_option`控制了当 Front Matter 中没有指定`updated`时，`updated`如何取值：

- mtime：使用文件的最后修改时间。这是从 Hexo 3.0.0 开始的默认行为。
- date：使用`date`作为`updated`的值。可用于 Git 工作流之中，因为使用 Git 管理站点时，文件的最后修改日期常常会发生变化。
- empty：直接删除`updated`。使用这一选项可能会导致大部分主题和插件无法正常工作。
{%endnote%}

### 分页

|参数|描述|默认值|
|--|--|--|
|per_page|每页显示的文章量（0 为关闭分页功能）|10|
|pagination_dir|分页目录|page|


### 包括或不包括目录和文件

在 Hexo 配置文件中，通过设置 include/exclude 可以让 Hexo 进行处理或忽略某些目录和文件夹。你可以使用 [glob](https://github.com/micromatch/micromatch#extended-globbing) 表达式对目录和文件进行匹配。

|参数|描述|
|--|--|
|include|Hexo 默认会忽略隐藏文件以及`_`和`.`开头的文件(夹)，_post 和 _data 等目录除外。|
|exclude|Hexo 会忽略这些文件和目录。|
|ignore|Hexo 会忽略这些文件和目录。|

{%note warning%}
`include`和`exclude`只适用于 source 文件夹，而`ignore`适用于所有文件夹。
{%endnote%}

例如：

```
include:
  # 包括 'source/css/_typing.css' 文件
  - "css/_typing.css"
  # 包括 'source/_css/' 中的任何文件，但不包括子目录及其中的文件
  - "_css/*"
  # 包括 'source/_css/' 中的任何文件和子目录下的任何文件
  - "_css/**/*"

exclude:
  # 不包括 'source/js/test.js' 文件
  - "js/test.js"
  # 不包括 'source/js/' 中的文件、但包括子目录下的所有目录和文件
  - "js/*"
  # 不包括 'source/js/' 中的文件和子目录下的任何文件
  - "js/**/*"
  # 不包括 'source/js/' 目录下的所有文件名以 'test' 开头的文件，但包括其它文件和子目录下的单文件
  - "js/test*"
  # 不包括 'source/js/' 及其子目录中任何以 'test' 开头的文件
  - "js/**/test*"
  # 不要用 exclude 来忽略 'source/_posts/' 中的文件。你应该使用 'skip_render'，或者在要忽略的文件的文件名之前加一个下划线 '_'
  # 在这里配置一个 - "_posts/hello-world.md" 是没有用的

ignore:
  # 忽略所有 'foo' 文件夹
  - "**/foo"
  # 只忽略 'themes/' 下的 'foo' 文件夹
  - "**/themes/*/foo"
  # 忽略所有 'themes/' 及其子目录下的 'foo' 文件夹
  - "**/themes/**/foo"
```

### 扩展
|参数|描述|
|--|--|
|theme|当前主题名称。值为`false`时禁用主题|
|theme_config|主题的配置。在这里放置的配置会覆盖主题目录下 _config.yml 中的配置|

### 部署

|参数|描述|
|--|--|
|deploy|部署部分的设置|
|deploy.type|部署类型，通常设置为`git`|
|deploy.repo|要部署到的远程仓库的链接|
|deploy.branch|要部署到的远程仓库的分支名|

### 备用站点配置文件

可以在 hexo-cli 中使用`--config`参数来指定自定义配置文件的路径。你可以使用一个 YAML 或 JSON 文件的路径，也可以使用逗号（无空格）的多个 YAML 或 JSON 文件的路径。例如：

```
# 使用 'custom.yml' 代替 '_config.yml'
hexo server --config custom.yml

# 使用更多个配置文件，排在后面的文件优先（将覆盖前面文件中的配置）
hexo generate --config custom.yml,custom2.json,custom3.yml
```

当你指定了多个配置文件以后，Hexo 会按顺序将这部分配置文件合并成一个 _multiconfig.yml。如果遇到重复的配置，排在后面的文件的配置会覆盖排在前面的文件的配置。这个原则适用于任意数量、任意深度的 YAML 和 JSON 文件。

例如，使用`--config`指定了两个自定义配置文件：

```
hexo generate --config custom.yml,custom2.json
```

如果 custom.yml 中指定了`foo: bar`，在 custom2.json 中指定了 `"foo": "dinosaur"`，那么在 _multiconfig.yml 中你会得到`foo: dinosaur`。

### 备用主题配置文件

通常情况下，Hexo 主题是一个独立的项目，并拥有一个独立的 _config.yml 配置文件。

除了自行维护独立的主题配置文件，你也可以在其他地方对主题进行配置。

#### 配置文件中的 theme_config

```yml # _config.yml
theme: "my-theme"
theme_config:
  bio: "My awesome bio"
  foo:
    bar: 'a'
```

```yml # themes/my-theme/_config.yml
bio: "Some generic bio"
logo: "a-cool-image.png"
  foo:
    baz: 'b'
```

最终主题配置的输出是：

```yml
{
  bio: "My awesome bio",
  logo: "a-cool-image.png",
  foo: {
    bar: "a",
    baz: "b"
  }
}
```

#### 独立的 _config.[theme].yml 文件

独立的主题配置文件应放置于站点根目录下，支持 yml 或 json 格式。需要配置站点 _config.yml 文件中的`theme`，以供 Hexo 寻找 _config.[theme].yml 文件。

```yml # _config.yml
theme: "my-theme"
```

```yml # _config.my-theme.yml
bio: "My awesome bio"
foo:
  bar: 'a'
```

```yml # themes/my-theme/_config.yml
bio: "Some generic bio"
logo: "a-cool-image.png"
  foo:
    baz: 'b'
```

最终主题配置的输出是：

```yml
{
  bio: "My awesome bio",
  logo: "a-cool-image.png",
  foo: {
    bar: "a",
    baz: "b"
  }
}
```

{%note warning%}
强烈建议你将所有的主题配置集中在一起。如果你不得不在多处配置你的主题，那么这些信息对你将会非常有用：Hexo 在合并主题配置时，Hexo 配置文件中的 `theme_config` 的优先级最高，其次是 _config.[theme].yml 文件，最后是位于主题目录下的 _config.yml 文件。
{%endnote%}
