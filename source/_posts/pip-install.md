title: Python包管理器pip安装
categories: python
tags: [python, pip]
---
## 前言
> pip 是一个安装和管理 Python 包的工具 , 是 easy_install 的一个替换品。安装方法：

## 安装
```bash
$ wget https://raw.github.com/pypa/pip/master/contrib/get-pip.py
$ [sudo] python get-pip.py
```

<!-- more -->

wget若没有，需要先安装（若不想安装，可拷贝[get-pip.py](https://bootstrap.pypa.io/get-pip.py)代码，新建get-pip.py文件粘贴），wget安装方法：
```bash
brew install wget（brew同样需先安装）
或者：
curl -O http://ftp.gnu.org/gnu/wget/wget-[version].tar.gz（其中[version]为具体版本号，进入网址查看并替换）
tar -xzvf wget-[version].tar.gz
cd wget-[version]
./configure --with-ssl=openssl
make
[sudo] make install
[sudo] make clean
```

> 但是安装过程可能会出现错误：
> <span style="color: red"> An error occurred while trying to run get-pip.py. Make sure you have setuptools or distribute installed.<span>

出现这个错误，说明首先要安装setuptools, 安装方法：
```bash
wget -q http://peak.telecommunity.com/dist/ez_setup.py
python ez_setup.py
```