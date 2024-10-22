---
title: '就算你是猪猪🐷我也不信教不会你的hugo博客教程（包括cloudflare或github actions自动构建）'
summary: 
# date: 2020-09-15T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["first"]
author: "Gendon"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Desc Text."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/<path_to_repo>/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

本教程甚至假设读者不熟悉git。
包括了安装使用git和hugo来免费部署在线博客的详细教程，以及利用github actions自动构建的教程，且参考查看了互联网上其他教程，踩了不少坑之后决定写出这篇教程总结记录。我的目标是尽我所能保证通俗易懂。

第一步，安装git ssh和hugo。使用你的包管理器下载这两个软件，比如我所使用arch linux，直接

```bash
yay -S git ssh hugo
```

就可以了，苹果则为`brew install hugo`，windows对着左下角win图标右键，点击“命令提示符”，或者windows自带搜索框搜索powershell，打开输入`winget install git hugo`就可以了，不可以的话先查关键词"win scoop" "win choco"查询这两个包管理器的安装教程，也非常简单，然后scoop或`choco install git ssh hugo`。

第二步，直接命令行cd进入你想放博客项目文件的地方，windows用户可以在文件管理器找个地方右键然后点击“在此处打开命令提示符”。
输入

```bash
hugo new site MyBlog --format yaml
# 使用hugo 新建 一个网站，网站名字是MyBlog，使用--format参数指定配置文件格式为yaml。
```

为什么使用yaml，很简单，因为hugo的yaml配置，比较新的参考教程最多，而且yaml这里已经足够用了，虽然我也喜欢toml，但说不定过几天就换svelte vue ts自己搭一个了。

`cd MyBlog`进入项目目录。

```bash
hugo new post/love.md
```

hugo就会在项目的`content/post/`下，根据`archetypes/default.md`生成一个love.md。

打开这个文件，看不懂顶部代码是什么意思没关系，我们是猪猪🐷，猪猪🐷不用思考那么多，在这个文件的底部空白处新开几行，在新的行随便乱敲点什么吧。注意不要破坏原有的---短杠行。

注意先确认保存修改，现在可以直接输入

```bash
hugo server -D
# hugo的server命令运行一个网络程序提供给我们访问。-D参数的意思是在根据default.md中的draft(草稿)参数生成的md文件顶部也会有draft，根据这个参数与否标记文章的是否草稿属性
```

来运行项目了。放心点击命令块右上角的复制，不用删除里面的描述文字，直接粘贴运行就可以了，打开浏览器，自己输入或点击 http://0.0.0.0:1313 进入hugo服务器运行的博客网站。
到目前为止，如果有任何报错，请复制询问AI。
是不是不够好看，太简单了？

在进一步之前我们还是先把项目接入git吧，这太重要了。

```bash
git init
git add README.md
git commit -m "first commit"
git branch -M main
```

现在需要你有一个github.com账号，注册登录这些应该就不用教了把，纯小白的开个浏览器网页翻译加qq邮箱也能搞定。但是如果你的网络不够神奇，连接github是不够稳定会断的。这一步的难度和你所在地区有关。实在不行，改用gitlab。
然后最难的一步来了，各位读猪请睁大眼睛，这关过了就是胜利。

你可以跟着 **(推荐)** 以下教程完成这一步骤。
https://docs.github.com/zh/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
https://docs.github.com/zh/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
这个官方教程足够简单。
我复述一遍。命令行输入：

```shell
ssh-keygen -t ed25519-sk -C "你的@邮箱.com"

```

然后一路回车猪突猛进直到世界空无一物。
运行以下获取公钥：

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
# 运行完这个命令会返回一串文字，全部复制下来
```

接着进入 https://github.com/settings/ssh/new 名字随便，把刚刚复制的东西全部粘贴去key，好像有回车不行，又好像能智能识别，本猪🐷忘了
你过关！让我们下一关。

点击进入 https://repo.new 新建一个仓库，名字填
`你的github用户name.github.io`
选项看着眼花看不懂没关系，我们是猪猪🐷，猪猪🐷不用思考那么多，猪猪🐷喜欢吃青菜，输入完名字往下拉看见绿色的按钮就点就行了。

创建完之后又来到一个让我们选东西吃的地方，这里是最简单的，想吃哪个吃哪个，先吃后吃吃几次都行，吭哧吭哧。因为上面已经为项目接入了git，不用再接入一次，而另外有些一次生效的命令就算我们再输入同样的命令也不会有什么影响，所以，完全不用害怕。如果你好奇这些命令是什么意思，可以去搜索git基础教程学习。或者复制去问AI。
简单的说就是输入以下：

```bash
git remote add origin git@github.com:你的github用户name/MyBlog.git
git push -u origin main
```

在项目下添加一个文件，".gitignore"，输入内容"/public"。

现在你每一次新增或修改完文章，都可以通过以下命令提交更新到项目并推送到github/gitlab。

```bash
git add .
git commit -m "update"
git push
```

由于我写教程考虑到Windows用户，就这么写出来了，不然就一行或者alias了。

我们现在来安装主题。
https://github.com/adityatelange/hugo-PaperMod/wiki/Installation
这是我选择的主题，主题换起来很容易，不用担心，我们先用起来，不要有顽霉主义，先用起来。

该主题的教程给出四个方法，我们选择标有 **(recomended)** 的方法，不在这种小事上给自己没事找事。不然等等报错你就知错了。

```bash
git submodule add --depth=1 https://gitclone.com/github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive # 当你要重新克隆你的项目时请记得输入这条命令更新子插件（这里也就是主题模组）
# 看不懂没关系，点击右上角复制粘贴全部带着这句话一起输入就可以了，我们是猪猪🐷，猪猪🐷不用思考那么多
```

然后修改项目里面的`hugo.yml`，你可以先复制粘贴修改我现在在用的 https://github.com/runesign/runesign.github.io/blob/main/hugo.yml 也可以参考官方教程的。
还有 `archetypes/default.md`，可以参考 https://www.sulvblog.cn/posts/blog/build_hugo/
https://github.com/xyming108/sulv-hugo-papermod/blob/main/archetypes/default.md?plain=1 这是来自一位同样使用papermod主题的博主的分享和教程。

注意请使用右侧Raw旁的复制符号，如果你不懂这里的配置是什么意思的话可以全部复制去问AI，以及多看多查教程。

最后一步，自动构建部署到互联网上。这步其实很简单，别慌。
有两种办法，第一种非常简单，而且支持GitLab，注册一个 https://cloudflare.com 账号，之后点击操作面板右侧"Wokers和Pages"-->"pages"-->"连接到Git"，然后根据提示一路选择就行，很简单，遇到要填的不要慌，除了一处应用要选Hugo，其他直接默认就行。然后就自动构建好了。

另一种是GitHub Actions。
打开你的GitHub博客仓库主页，点击上侧Settings，点击左侧Pages，中间有一个
Build and deployment
Source
Deploy from a branch
此时点击Deploy from a branch，点击切换成GitHub Actions。

在项目中新建".github/workfows/"文件夹，其下再写一个hugo.yaml，内容如下：

```yaml
# Sample workflow for building and deploying a Hugo site to GitHub Pages
name: Deploy Hugo site to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches:
      - main

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

# Default to bash
defaults:
  run:
    shell: bash

jobs:
  # Build job
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.134.2
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb
      - name: Install Dart Sass
        run: sudo snap install dart-sass
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive
          fetch-depth: 0
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v5
      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
      - name: Build with Hugo
        env:
          HUGO_CACHEDIR: ${{ runner.temp }}/hugo_cache
          HUGO_ENVIRONMENT: production
          TZ: America/Los_Angeles
        run: |
          hugo \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

保存并通过之前说过的命令更新上传：

```bash
git add .
git commit -m "update"
git push
```

好了，现在过一会你就能访问你的xxxxxxxx.github.io了
word天终于写完了顶部代码是什么意思没关系，我们是猪猪🐷，猪猪🐷不用思考那么多，在这个文件的底部空白处新开几行，随便乱敲点什么吧。

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
