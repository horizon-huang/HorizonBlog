title: Mac OS 10.11下安装Scrapy框架
categories: scrapy
tags: [scrapy, 安装]
---
## 前言
> Scrapy框架是个比较简单易用基于python的爬虫框架，[Scrapy中文文档](http://scrapy-chs.readthedocs.org/zh_CN/latest/)可具体查看。

## 安装
> 在Mac系統下安裝過程中常常會出現問題，最關鍵的是不要Mac自帶的python安裝Scrapy，若這樣做會出現Operation not permitted等錯誤。

使用homebrew或pyenv安装python，然后再进行Scrapy的安装。

```bash
$ sudo pip install scrapy
```

<!-- more -->

## 常见问题

#### 解决ImportError:cannot import name xmlrpc_client问题
> 安装完成之后，终端下输入如下命令查看Scrapy版本并验证是否成功，却发现出了问题，提示
ImportError:cannot import name xmlrpc_client

```bash
$ sudo rm -rf /Library/Python/2.7/site-packages/six*
$ sudo rm -rf /System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/six*
$ sudo pip install six
```
卸载掉six并重装，再次查看Scrapy版本，搞定。
