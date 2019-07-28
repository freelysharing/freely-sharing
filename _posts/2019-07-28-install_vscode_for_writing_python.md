---
layout: post
title:  "Windows10 安装VS Code编辑器, 配置 Python 编程环境"
date:   2019-07-28 19:18:00 +0800
categories: jekyll update
---
本文介绍安装 VS Code 和 VS Code 的 python 插件，Code Runner 插件，配置简单的 python 编程环境。安装 python 见：
[Windows10下安装python 并配置 pypi 源]({% link _posts/2019-07-28-setup_python_windows.md %})

- [VS Code 简介](#vs-code-简介)
    - [编辑器 (Editor) 还是 集成开发环境 (IDE)](#编辑器-editor-还是-集成开发环境-ide)
- [安装 VS Code](#安装-vs-code)
  - [安装中文 (可选)](#安装中文-可选)
  - [安装 python 插件](#安装-python-插件)
  - [安装 Code Runner (推荐)](#安装-code-runner-推荐)
- [vscode 中运行 python](#vscode-中运行-python)
  - [编写 python 程序文件](#编写-python-程序文件)
  - [运行](#运行)
  - [format document (格式化python文档)](#format-document-格式化python文档)

## VS Code 简介
VS Code 官网：<https://code.visualstudio.com/>

Visual Studio Code（简称VS Code）是一个由微软开发的，同时支持Windows、Linux、和macOS系统且开放源代码的代码编辑器，它支持测试，并内置了Git 版本控制功能，同时也具有开发环境功能，例如代码补全（类似于 IntelliSense）、代码片段、和代码重构等，该编辑器支持用户个性化配置，例如改变主题颜色、键盘快捷方式等各种属性和参数，还在编辑器中内置了扩展程序管理的功能。

(摘自 [Visual Studio Code](https://zh.wikipedia.org/wiki/Visual_Studio_Code) "wikipeida")

#### 编辑器 (Editor) 还是 集成开发环境 (IDE)
这里推荐使用 VS Code 编写python代码，刚入门时 VS Code + Python 插件 提供的功能已经足够了，如语法高亮，代码补全提示等。
并且如果需要编写多种语言的代码，有一个熟悉的编辑器比使用多个专门的IDE (integrated development environment 集成开发环境) 方便。
VS Code 安装大概 200MB。而如果像 JetBrains 的 IDE，大概一个接近 1G 吧。(没查到数据，自己也没有安装)

相比编辑器，IDE 提供了更多的功能，如JetBrains 的 PyCharm，提供的功能如：
+ 代码分析与辅助功能，拥有补全代码、高亮语法和错误提示
+ 项目和代码导航：专门的项目视图，文件结构视图和和文件、类、方法和用例的快速跳转
+ 集成单元测试，按行覆盖代码

这些功能是普通编辑器不容易提供的，专门写一门语言的代码时很有帮助。

## 安装 VS Code
在官网下载，安装选项比较简单。 <https://code.visualstudio.com/>

### 安装中文 (可选)
vscode 默认时英文的。并且很多插件的功能和配置都是英文的，可以尝试使用英文的 vscode。(如果英文的vscode中插件功能显示了中文，可以搜索一下方法)

安装中文：在左侧第五个按钮，输入 `@category:"language packs"` , 然后安装中文包。接着 reload vscode 使插件生效。
![install Chinese](/assets/images/install_vscode_for_writing_python/install-chinese.jpg)

### 安装 python 插件
同样在插件栏，输入 `python`，可以看到很多 python 插件。这里使用的是微软提供的 Python 插件 (别忘了vscode是微软和开源社区共同开发的)
![python extension](/assets/images/install_vscode_for_writing_python/python-extension.jpg)

### 安装 Code Runner (推荐)
这个插件可以提供便捷的按钮，让运行 python 程序更方便。搜索并安装即可。安装完重启，右上角多了一个箭头，可以运行当前的程序文件。
![code runner](/assets/images/install_vscode_for_writing_python/code-runner.jpg)

## vscode 中运行 python
在vscode中写 python 代码，常用到的是语法高亮，格式化python文件。

vscode有工作区的概念，写程序时在一个工作区写一种代码或者写一个工程的代码。

### 编写 python 程序文件
首先打开一个文件夹作为工作区，从菜单中选择：文件 -> 打开文件夹。注意选择一个全是英文的文件夹作为工作区，否则以后某些代码可能无法运行。(同时windows用户名最好是英文名，这样可以避免麻烦)。

就写比较传统的代码。新建一个文件 `hello-world.py` ，注意文件后缀名必须是 `.py` ，英文的标点。否则会出错。(代码中必须使用**英文标点**！) 在文件中输入或者复制以下代码 (注意**使用英文标点**)。

``` python
print("hello, world ^_^")
print("love yourself, love life")
```

### 运行
保存文件后，按右上角的箭头(需要安装 Code Runner)启动 python 解释器运行代码。这时下方会打开终端(terminal)，并显示调用python的命令，及运行的结果。

![run hello world](/assets/images/install_vscode_for_writing_python/run-hello-world.jpg)

### format document (格式化python文档)
写代码有统一清晰的格式和风格可以让代码更容易阅读，也让代码更容易维护。vscode 也提供了格式化代码的功能，在文件中点击鼠标右键，找到格式化文档，会提示安装 `autopep8`，以提供格式化的功能。(注意配置好 pypi源，否则从国外官方 pypi 源下载很慢)。见：
[Windows10下安装python 并配置 pypi 源]({% link _posts/2019-07-28-setup_python_windows.md %})