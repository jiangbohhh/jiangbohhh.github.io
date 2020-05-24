---
title: "如何使用hugo搭建blog"
date: 2020-05-24T00:50:35+08:00
description: ""
Tags: ["Hugo", "Blog"]
draft: false
---



 [Hugo](https://gohugo.io/) ,号称最快的静态站点生成器后。 尝试搭建博客，发现不管是运行速度，还是打包速度都是非常快的。
Hugo 官方的定义是：

Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again.(Hugo 是使用 Go 编写的快速而现代的静态站点生成器，旨在使网站创建变得有趣。)

<!--more-->



## Step 1:安装hugo



> `Homebrew`是`macos`上的一个包管理工具，可以从[brew.sh](https://brew.sh/)上安装。

```shell
brew install go
```



验证是否安装：

```shell
hugo version
```

命令行中出现如下输出代表成功：

```
Hugo Static Site Generator v0.70.0/extended darwin/amd64 BuildDate: unknown
```



## Step 2: 创建站点

执行下面命令将会在`jiangbohhh.github.io`文件夹中创建一个新的Hugo站点：

```shell
hugo new site jiangbohhh.github.io
```





## Step 3: 添加主题

在[themes.gohugo.io](https://themes.gohugo.io/)中可以找到非常多的hugo主题。

在这里， 我们使用[Ananke theme](https://themes.gohugo.io/gohugo-theme-ananke/)主题。

首先，从Github上下载主题并添加到站点的`theme`路径中去：

```
cd jiangbohhh.github.io
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
```

然后，在站点配置文件中添加如下内容：

```
echo 'theme= "ananke"' >> config.toml
```





## Step 4: 添加写作内容

可以直接创建内容文件（例如： `content/<CATEGORY>/<FILE>.<FORMAT>`）并将内容写入文件中。当然也可以使用`new`命令创建文件。

```
hugo new posts/use-hugo-create-blog.md
```

编辑创建文件的内容，每个创建的文件都会有相同的开头如下：

```
---
title: "Use Hugo Create Blog"
date: 2020-05-24T00:50:35+08:00
draft: true
---
```

将内容写如到文件正文中，一篇文章即已经写好。





## Step 5: 启动Hugo服务

使用 `hugo server -D`可以启动一个Hugo服务。

启动后，命令行中会出现如下打印信息：

```
                   | EN
-------------------+-----
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  3
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0

Built in 16 ms
Watching for changes in /Users/jiangbo/github.com/owner/jiangbohhh.github.io/{archetypes,content,data,layouts,static,themes}
Watching for config changes in /Users/jiangbo/github.com/owner/jiangbohhh.github.io/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

服务启动成功后，我们可以通过`http://localhost:1313/`访问页面查看页面效果。





## Step 6: 定制主题

### 站点配置

打开`config.toml`文件：

```
baseURL = "https://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
theme = "ananke"
```

替换`title`中内容为自己的站点标题，在这里我们把`jiangohhh.github.io`的域名填充到`baseURL`的内容中去。



## Step 7: 创建静态页面

执行如下命令：

```
hugo -D
```

会在`public/`文件夹下生成静态文件。