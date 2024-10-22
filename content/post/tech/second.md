---
title: 'Second'
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

# 双栏文件管理器

## 概述

双栏文件管理器是一款功能强大的文件管理应用，支持双栏视图、网格视图、文件和文件夹的创建、删除、重命名等操作。该应用使用 Flutter 框架开发，结合 GetX 状态管理，提供了流畅的用户体验。

## 功能特性

- **双栏视图**：支持单栏和双栏视图切换，方便用户在不同场景下管理文件。
- **网格视图**：支持列表视图和网格视图切换，提供更直观的文件展示方式。
- **文件操作**：支持文件和文件夹的创建、删除、重命名等操作。
- **选择模式**：支持多选模式，方便批量操作文件。 - **实时监控**：自动监控文件夹变化，实时更新文件列表。
- **面包屑导航**：方便用户快速导航到任意目录。
- ## 安装与运行
- ### 前提条件
- Flutter SDK：确保你已经安装了 Flutter SDK，并且环境变量配置正确。
- Dart SDK：Flutter SDK 包含了 Dart SDK，无需单独安装。
- IDE：推荐使用 Android Studio 或 Visual Studio Code 进行开发。
- ### 安装步骤

1. **克隆仓库**： `bash git clone https://github.com/runesign/file_manager.git `
2. **进入项目目录**： `cd  file_manager `
3. **安装依赖**： `flutter pub get `
4. **运行应用**： `flutter run `

### 构建应用

**构建 APK**：
`flutter build apk `
**构建 iOS 应用**：
`flutter build ios `

构建其他平台基本如上。

## 使用指南

### 主界面

- **顶部导航栏**：包含应用标题和视图切换按钮。
- **视图切换按钮**：点击按钮可以在单栏和双栏视图之间切换。
- **网格/列表视图切换按钮**：点击按钮可以在网格视图和列表视图之间切换。
- **文件列表**：显示当前目录下的文件和文件夹。
- **文件夹**：点击文件夹可以进入该文件夹。
- **文件**：点击文件可以打开文件（当前版本仅支持打印文件名）。
- **底部操作栏**：包含常用的文件操作按钮。
- **选择模式**：点击按钮进入选择模式，可以多选文件进行批量操作。
- **全选**：点击按钮可以全选当前目录下的文件。
- **新建文件/文件夹**：点击按钮可以创建新的文件或文件夹。
- **返回上级目录**：点击按钮可以返回上级目录。
- ### 文件操作
- **删除文件**：在选择模式下，选中文件后点击删除按钮，可以删除选中的文件。
- **重命名文件**：在选择模式下，选中文件后点击重命名按钮，可以重命名选中的文件。
- **新建文件/文件夹**：点击新建按钮，输入名称后可以选择创建文件或文件夹。
- ## 技术栈
- **Flutter**：跨平台 UI 框架，用于构建高性能、高保真的移动应用。
- **GetX**：轻量级状态管理库，用于管理应用的状态和依赖注入。
- **path_provider**：用于获取应用的文件存储路径。
- **dart:io**：用于文件和目录操作。
- ## 贡献 欢迎贡献代码、提交问题和建议。请遵循以下步骤：

1. **Fork 仓库**。
2. **创建新分支**：`git checkout -b feature/your-feature-name`。
3. **提交更改**：`git commit -m 'Add some feature'`。
4. **推送分支**：`git push origin feature/your-feature-name`。
5. **提交 Pull Request**。
6. ## 许可证 本项目采用 GPL3.0 许可证。详情请参阅 [LICENSE](LICENSE) 文件。
7. ## 联系 如有任何问题或建议，请通过以下方式联系：

- 邮箱：runesign@outlook.com
- GitHub：[runesign](https://github.com/runesign)
