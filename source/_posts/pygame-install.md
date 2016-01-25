title: Mac OS X 10.x下安装Pygame
categories: python
tags: [python, pygame]
---
## 前言
> Pygame是一个利用SDL库写的游戏库,Pygame对应的Python版本为2.7（这个很重要）。

## 安装
```bash
$ brew install sdl sdl_image sdl_mixer sdl_ttf portmidi
$ brew tap homebrew/headonly
$ brew install smpeg --HEAD（这个不是必需的）
$ sudo pip install hg+http://bitbucket.org/pygame/pygame
```

具体安装可查看[http://juliaelman.com/blog/2013/04/02/installing-pygame-on-osx-mountain-lion/](http://juliaelman.com/blog/2013/04/02/installing-pygame-on-osx-mountain-lion/)

## 安装中出现的问题
#### 1、Cannot find command 'hg'
> 出现这个问题是因为系统不存在hg命令，需安装[Mercurial](https://www.mercurial-scm.org)。

#### 2、弹出 需要下载x11的安装包 的提示
> 根据提示点击继续，显示缺少x11安装包，需安装[XQuartz](http://www.xquartz.org)，XQuartz软件内附有x11安装包。安装完成后重启系统，然后再次执行上面的命令。

