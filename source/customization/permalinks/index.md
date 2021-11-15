---
title: 永久链接
date: 2021-10-22 13:00:14
---

你可以在 _config.yml 配置中调整网站的永久链接，或者在每篇文章的 Front-matter 中指定。

### 变量

除了下列变量外，你还可以使用 Front-matter 中的所有属性。

|变量|描述|
|---|---|
|:year|文章的发表年份（4 位数）|
|:month|文章的发表月份（2 位数）|
|:i_month|文章的发表月份（去掉开头的 0）|
|:day|文章的发表日期（2 位数）|
|:i_day|文章的发表日期（去掉开头的 0）|
|:hour|文章发表的小时（2 位数）|
|:minute|文章发表的分钟（2 位数）|
|:second|文章发表的秒钟（2 位数）|
|:title|文件名称（带路径）|
|:name|文件名称（不带路径）|
|:post_title|文章标题|
|:id|文章 ID|
|:category|分类。如果没有分类，则是`default_category`配置信息|
|:hash|文件名的 SHA1 哈希值，作用与`:title`相同|

你可以在`permalink_defaults`参数下调整永久链接中各变量的默认值：

```yml
permalink_defaults:
  lang: en
```

### 示例

```yml source/_posts/hello-world.md
title: Hello World
date: 2013-07-14 17:01:34
categories:
  - foo
  - bar
```

|参数|结果|
|--|--|
|:year/:month/:day/:title/|2013/07/14/hello-world|
|:year-:month-:day-:title.html|2013-07-14-hello-world.html|
|:category/:title/|for/bar/hello-world/|
|:title-:hash/|hello-world-a2c8ac003b43/|

`:title`和`:name`都是表示文件名，其区别在于是否在文件名前加上路径。

```yml source/_posts/lorem/hello-world.md
title: Hello World
date: 2013-07-14 17:01:34
categories:
  - foo
  - bar
```

|参数|结果|
|--|--|
|:year/:month/:day/:title/|2013/07/14/lorem/hello-world/|
|:year/:month/:day/:name/|2013/07/14/hello-world/|

### 多语种支持

若要建立一个多语种的网站，你可在 _config.yml 中修改`new_post_name`和`permalink`参数，如下：

```yml
new_post_name: :lang/:title.md
permalink: :lang/:title/
```

当你建立新文章时，文章会被储存到：

```
hexo new "Hello World" --lang tw
# => source/_posts/tw/Hello-World.md
```

而网址会是：http://localhost:4000/tw/hello-world/ 。
