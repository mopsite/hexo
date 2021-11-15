---
title: 国际化（i18n）
date: 2021-10-22 13:01:44
---

若要让你的网站以不同语言呈现，你可以使用国际化功能。请现在 _config.yml 中调整`language`设定，这代表的是预设语言，你也可以设定多个语言来调整预设语言的顺位。

```yml
language: zh-tw

language:
- zh-tw
- en
```

### 语言文件

语言文件可以使用 YAML 或 JSON 编写，并放在主题文件夹中的 languages 文件夹。你可以在语言文件中使用 [printf](https://github.com/alexei/sprintf.js) 格式。

### 模板

在模板中，通过`__`或`_p`辅助函数，即可取得翻译后的字符串，前者用于一般使用，后者用于复杂字符串。例如：

```yml en.yml
index:
  title: Home
  add: Add
  video:
    zero: No videos
    one: One video
    other: %d videos
```

```
<%= __('index.title') %>
// Home

<%= _p('index.video', 3) %>
// 3 videos
```

### 路径

你可以在 Front-matter 中指定该页面的语言，也可以在 _config.yml 中修改`i18n_dir`设定，让 Hexo 自动侦测。

```yml
i18n_dir: :lang
```

`i18n_dir`的值是`:lang`，也就是说 Hexo 会捕获网址中的第一段以检测语言，举例来说：

```
/index.html => en
/archives/index.html => en
/zh-tw/index.html => zh-tw
```

捕获到的字符串唯有在语言文件存在的情况下，才会被当做是语言。因此 /archives/index.html 中的 archives 就不被当成是语言。
