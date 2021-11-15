---
title: 部署
date: 2021-10-20 18:00:39
---

Hexo 提供了快速方便的一键部署功能，让你只需一条命名就能将网站部署到服务器上。

```
hexo deploy
```

该命令可以简写成：

```
hexo d
```

在开始之前，你必须先在 _config.yml 中修改参数，一个正确的部署配置中至少要有`type`参数，例如：

```yml
deploy:
  type: git
```

你可以同时使用多个 deployer，Hexo 会按照顺序执行每个 deployer：

```yml
deploy:
  type: git
  repo:
deploy:
  type: heroku
  repo:
```

{%note warning%}
YAML 依靠缩进来确定元素间的从属关系。因此，请确保每个 deployer 的缩进长度相同，并使用空格缩进。
{%endnote%}

### 安装插件

安装 [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git) 插件。

```
npm install hexo-deployer-git --save
```

### 修改配置

```yml
deploy:
  type: git
  repo: <repository url> #https://bitbucket.org/JohnSmith/johnsmith.bitbucket.io
  branch: [branch]
  message: [message]
```

|参数|描述|
|--|--|
|repo|库（Repository）地址|
|branch|分支名称|
|message|自定义提交信息|

### 生成并推送

生成站点文件并推送至远程库。

```
hexo clean
hexo deploy
```

### 这一切是如何发生的

当执行`hexo deploy`时，Hexo 会将 public 目录中的文件和目录推送至 _config.yml 中指定的远程仓库和分支中，并且**完全覆盖**分支下的已有内容。

{%note danger no-icon%}
由于 Hexo 的部署默认使用 master 分支，所以如果你同时正在使用 Git 管理你的站点目录，你应该注意你的部署分支应当不同于写作分支。一个好的实践是将站点目录和 Pages 分支存放在两个不同的 Git 仓库中，可以有效避免相互覆盖。Hexo 在部署你的站点生成的文件时并不会更新你的站点目录。因此你应该手动提交并推送你的写作分支。
{%endnote%}

此外，如果你的 GitHub Pages 需要使用 CNAME 文件自定义域名，请将 CNAME 文件至于 source 目录下，只有这样`hexo deploy`才能将 CNAME 文件一并推送至部署分支。
