---
layout: post
title:  "Windows10下安装python 并配置 pypi 源"
date:   2019-07-28 16:18:00 +0800
categories: jekyll update
---
本文介绍在 Windows10 系统上安装 64位 Python 过程。配置 python编程环境时，推荐使用 VS Code 作为写 python 程序的编辑器，见：
[Windows10 安装VS Code编辑器, 配置 Python 编程环境]({% link _posts/2019-07-28-install_vscode_for_writing_python.md %})

- [Python 简介](#python-简介)
  - [Python 版本](#python-版本)
- [安装 Python](#安装-python)
  - [从官网下载安装包](#从官网下载安装包)
  - [选择安装选项](#选择安装选项)
  - [解除 260 个字符路径长度限制 (可选)](#解除-260-个字符路径长度限制-可选)
  - [测试 Python 安装](#测试-python-安装)
    - [使用 powershell 测试](#使用-powershell-测试)
      - [打开 powershell](#打开-powershell)
      - [测试 python](#测试-python)
- [配置 pypi (python package index) 源 (推荐)](#配置-pypi-python-package-index-源-推荐)
- [更多阅读](#更多阅读)
  - [powershell 介绍](#powershell-介绍)

___
## Python 简介
Python 官网：<https://www.python.org>

Python（英国发音：/ˈpaɪθən/ 美国发音：/ˈpaɪθɑːn/）是一种广泛使用的解释型、高级编程、通用型编程语言，由吉多·范罗苏姆 ([Guido van Rossum](https://en.wikipedia.org/wiki/Guido_van_Rossum)) 创造，第一版发布于1991年。可以视之为一种改良（加入一些其他编程语言的优点，如面向对象）的LISP。Python的设计哲学强调代码的**可读性**和**简洁的语法**（尤其是使用空格缩进划分代码块，而非使用大括号或者关键词）。相比于C++或Java，Python让开发者能够用更少的代码表达想法。不管是小型还是大型程序，该语言都试图让程序的结构清晰明了。
 
Python 解释器本身几乎可以在所有的操作系统中运行。Python的其中一个解释器CPython是用C语言编写的、是一个由社群驱动的**自由软件**，当前由Python软件基金会管理。

(摘自 [Python](https://zh.wikipedia.org/wiki/Python) "wikipedia")

___
### Python 版本
现在最新的 Python 稳定版本是 Python3.7.4 ，开发中的版本是 3.8 。

需要注意的是，python2 到 python3 的版本更新很大，2 和 3 是不兼容的。现在仍然有许多项目是使用 python2 编写的，但 python2 的官方支持是到 2020 年 (虽然可能还会延长支持的时间)。最新的 python2 是 python2.7.16 。

___
## 安装 Python
### 从官网下载安装包
现在的新电脑都是 _64位_ 的处理器，选择官网下载页面的 `x86-64 executable installer` ，这会下载 python-3.7.3-amd64.exe 安装包 (这个是常见的提供安装界面的安装包)。<https://www.python.org/downloads/windows/>

![download python](/assets/images/setup_python_windows_with_vscode/Python-Windows-Download.jpg)

___
### 选择安装选项

1. 把 Python 加入到环境变量 PATH 中，这样可以从命令行工具 (cmd or powershell) 中直接访问
![add to PATH](/assets/images/setup_python_windows_with_vscode/installpython-addpath.jpg)
2. Install Now

出于让教程简单，Customize installation 中的选项就不介绍了。但是，不建议把 Python 安装到自定义的位置，这可能会造成麻烦。

___
### 解除 260 个字符路径长度限制 (可选)
Windows10 有 260 字符路径长度限制，在安装好python后，安装界面会提示选择解除限制。如果没有在那里解除限制，可以搜索如何更改注册表来解除限制。

___
### 测试 Python 安装
Windows10 上可以使用 Powershell 或者 cmd 命令行工具来测试是否可以正常地使用 Python。
#### 使用 powershell 测试
##### 打开 powershell
+ 开始菜单 -> Windows PowerShell -> Windows PowerShell
+ 快捷键: `Win+R` 打开运行 (Run)，输入 `powershell`

##### 测试 python
在powershell中输入 python，这会启动 python 解释器，(在解释器中，输入一句代码，执行一句代码) 然后输入
``` python
print("hello, world ^_^")
```
注意在 python 解释器中没有语法高亮。输入 `exit()` 推出 python 解释器。
![hello world (powershell)](/assets/images/setup_python_windows_with_vscode/testpython-powershell-hello.jpg)

## 配置 pypi (python package index) 源 (推荐)
python 的功能十分强大，一部分得益于它丰富的开源软件包。pypi(python package index)上有许多开源的包，提供科学计算，写网络爬虫等不同方面的功能。

但是 pypi 的官方镜像在国外，访问较慢。所以使用国内的镜像，这里使用清华TUNA提供的镜像(清华源)，官方配置教程见：<https://mirrors.tuna.tsinghua.edu.cn/help/pypi/>

步骤为：
1. 打开powershell
2. 在powershell命令行中输入

``` shell
pip install --upgrade --user -i https://pypi.tuna.tsinghua.edu.cn/simple pip
# 这是注释
# 或者输入下一句注释中的命令
# pip install pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

![set up pip](/assets/images/setup_python_windows_with_vscode/setup-pip.jpg)

## 更多阅读
### powershell 介绍
PowerShell（包括Windows PowerShell and PowerShell Core）是微软公司开发的任务自动化和配置管理框架，由.NET Framework和.NET Core是构建的命令行界面壳层相关脚本语言组成，最初仅Windows组件，后于2016年8月18日开源并跨平台支持。

UNIX系统一直有着功能强大的壳程序（shell），Windows PowerShell的诞生就是要提供功能相当于UNIX系统的命令行壳程序（例如：sh、bash或csh），同时也内置脚本语言以及辅助脚本程序的工具。