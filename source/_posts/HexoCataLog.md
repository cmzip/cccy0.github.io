---
title: HEXO的文件目录
categories: Hexo
---

*我的Blog大致已经建的差不多了,在这里先把Hexo的目录整理一下.还有一些东西以后再写.*
# Hexo备份目录:

### scaffolds
>模版 文件夹。当新建文章时，Hexo 会根据 scaffold 来建立文件.
>Hexo的模板是指在新建的markdown文件中默认填充的内容。例如，如果您修改scaffold/post.md中的Front-matter内容，那么每次新建一篇文章时都会包含这个修改.

### source
>资源文件夹是存放用户资源的地方。除 _posts 文件夹之外，开头命名为 _ (下划线)的文件 / 文件夹和隐藏的文件将会被忽略.
>Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去.

### themes
>主题 文件夹。Hexo 会根据主题来生成静态页面.

### _config.yml
>网站的配置信息.

# Other目录:

### package.json
>应用程序的信息。

### .deploy_git
>Hexo建立的版本库,用来Hexo deploy到远程库中的.

### .git
>自己建立的git库.

### node_modules
>node的模块npm,是node.js的包管理工具,执行npm install会安装.

### public
>执行hexo g生成的静态文件,hexo deploy会复制这个目录部署.

### .gitignore
>git的时候忽略的文件.



