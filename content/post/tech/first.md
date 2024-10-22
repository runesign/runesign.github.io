---
# lastmod: "2024-10-22T13:15:22+08:00"
draft: true
title: "就算你是猪猪🐷我也不信教不会你的hugo博客教程（包括github actions自动构建）"
---

本教程假设各位读猪几乎完全不会使用git。
包括了安装使用git和hugo来部署博客的详细教程，以及利用github actions自动构建的教程，且参考查看了互联网上其他教程，踩了不少坑之后决定写出这篇教程总结记录。我的目标是尽我所能保证通俗易懂。

第一步，安装git和hugo。使用你的包管理器下载这两个软件，比如我所使用arch linux，直接

```bash
yay -S git hugo
```

就可以了，苹果则为brew install hugo，windows对着左下角win图标右键，点击“命令提示符”，或者windows自带搜索框搜索powershell，打开输入`winget install git hugo`就可以了，不可以的话先查关键词"win scoop" "win choco"查询这两个包管理器的安装教程，也非常简单，然后scoop或choco install git hugo。

第二步，直接命令行cd进入你想放博客项目文件的地方，windows用户可以在文件管理器找个地方右键然后点击“在此处打开命令提示符”。
输入

```bash
hugo new site MyBlog --format yaml
# 使用hugo 新建 一个网站，网站名字是MyBlog，使用--format参数指定配置文件格式为yaml。
```

意思是：为什么使用yaml很简单，因为hugo的yaml配置，比较新的参考教程最多，而且yaml这里已经足够用了，虽然我也喜欢toml，但说不定过几天就换svelte vue ts自己搭一个了。

`cd MyBlog`进入项目目录。

```bash
hugo new post/love.md
```

hugo就会在项目的content/post/下，根据archetypes/default.md生成一个love.md。

打开这个文件，看不懂顶部代码是什么意思没关系，我们是猪猪🐷，猪猪🐷不用思考那么多，在这个文件的底部空白处新开几行，随便乱敲点什么吧。

注意先确认保存修改，现在可以直接输入

```bash
hugo server -D
# hugo的server命令运行一个网络程序提供给我们访问。-D参数的意思是在根据default.md中的draft(草稿)参数生成的md文件顶部也会有draft，根据这个参数与否标记文章的是否草稿属性
```

来运行项目了。放心点击命令块右上角的复制，不用删除里面的描述文字，直接粘贴运行就可以了，打开浏览器，自己输入或点击 0.0.0.0:1313 进入hugo服务器运行的博客网站。
到目前为止，如果有任何报错，请复制询问AI。

是不是不够好看，太简单了？我们现在来安装主题。
我们还是先把项目接入git吧。

```bash

```

https://github.com/adityatelange/hugo-PaperMod/wiki/Installation
这是我选择的主题，主题换起来很容易，不用担心，我们先用起来，不要有顽霉主义，先用起来。

教程给出四个方法，我们选择标有 **(recomended)** 的方法，不在这种小事上给自己没事找事。不然等等报错你就知错了。

```bash
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive # 当你要重新克隆你的项目时请记得输入这条命令更新子插件（这里也就是主题模组）
# 看不懂没关系，点击右上角复制粘贴全部带着这句话一起输入就可以了，我们是猪猪🐷，猪猪🐷不用思考那么多
```
