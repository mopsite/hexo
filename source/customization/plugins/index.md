---
title: 插件
date: 2021-10-22 13:02:15
---

Hexo 有强大的插件系统，使你能轻松扩展功能而不用修改核心模块的源码。在 Hexo 中有两种形式的插件：

### 脚本（Scripts）

如果你的代码很简单，建议你编写脚本，你只需要把 JavaScript 文件放到 scripts 文件夹，在启动时就会自动载入。

### 插件（Packages）

如果你的代码较复杂，或是你想要发布到 NPM 上，建议你编写插件。首先，在 node_modules 文件夹中建立文件夹，文件夹名称开头必须为`hexo-`，如此一来 Hexo 才会在启动时载入，否则 Hexo 将会忽略它。

文件夹内至少要包含 2 个文件：一个是主程序，另一个是 package.json（描述插件的用途和所依赖的插件）。

```
.
├── index.js
└── package.json
```

package.json 中至少要包含`name`、`version`和`main`属性，例如：

```json package.json
{
  "name": "hexo-my-plugin",
  "version": "0.0.1",
  "main": "index"
}
```
