title: Python多版本管理－pyenv安装及使用
categories: python
tags: [python, pyenv]
---
## 前言
> pyenv是用来管理电脑内不同版本的Python的一个管理工具，并且切换不同版本不会影响到系统自带的Python。
> 具体可以猛戳这里：[https://github.com/yyuu/pyenv](https://github.com/yyuu/pyenv)

## pyenv安装
```bash
$ brew install pyenv
```

> homebrew若没有需先安装，具体安装方法非常简单，不在这说明。

<!-- more -->

## pyenv使用

### pyenv versions
查看当前 pyenv 可检测到的所有版本，处于激活状态的版本前以 * 标示。
```bash
$ pyenv versions
* system (set by /Users/horizon/.python-version)
  3.5.1
```

### pyenv version
查看当前处于激活状态的版本，括号中内容表示这个版本是由哪条途径激活的（global、local、shell）
```bash
$ pyenv version
system (set by /Users/horizon/.python-version)
```

### pyenv install
使用 python-build（一个插件） 安装一个 Python 版本，到 $PYENV_ROOT/versions 路径下。
```bash
$ pyenv install -v 3.5.1
```

建议添加 -v 参数用于显示细节。python-build 会首先尝试从一个镜像站点下载包，此时可以去 /tmp/python-build.xxx 里面关心一下下载速度。如果太慢，可以直接在 shell 里 ctrl-c 终止此次下载，然后 python-build 会自动去 python.org/ftp 下载。不一定哪个更快。 

### pyenv uninstall
卸载一个版本
```bash
$ pyenv uninstall 3.5.1
```

### pyenv rehash
为所有已安装的可执行文件 （如：~/.pyenv/versions/*/bin/*） 创建 shims，因此，每当你增删了 Python 版本或带有可执行文件的包（如 pip）以后，都应该执行一次本命令
```bash
$ pyenv install 3.5.1
$ pyenv rehash
```

### pyenv global
设置全局的 Python 版本，通过将版本号写入 ~/.pyenv/version 文件的方式。
```bash
$ pyenv global 3.5.1
```

### pyenv local
设置面向程序的本地版本，通过将版本号写入当前目录下的 .python-version 文件的方式。通过这种方式设置的 Python 版本优先级较 global 高。pyenv 会从当前目录开始向上逐级查找 .python-version 文件，直到根目录为止。若找不到，就用 global 版本。
```bash
$ pyenv local 3.5.1
```

### pyenv shell
设置面向 shell 的 Python 版本，通过设置当前 shell 的 PYENV_VERSION 环境变量的方式。这个版本的优先级比 local 和 global 都要高。--unset 参数可以用于取消当前 shell 设定的版本。
```bash
$ pyenv shell pypy-2.2.1
$ pyenv shell --unset
```


## 在Mac下需要的配置工作

当使用pyenv local [version]切换本地python版本时，发现python还是之前的版本，原因是没有配置shell configuration，具体配置如下：
```bash
在~/.bash_profile的最下面加入
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi
然后执行
$ source .bash_profile  #更新shell配置
```
