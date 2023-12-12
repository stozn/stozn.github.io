---
date: 2023-01-31 
categories:
  - Hello
  - World
---

# Hello world!


## 简介  
Anaconda是一个用于科学计算的Python发行版，支持Linux, Mac, Windows,包含了众多流行的科学计算、数据分析的Python包。

## 下载地址：
https://mirrors.aliyun.com/anaconda/ 
包括 完整版 (archive/)目录 和 miniconda(miniconda/)目录

## 配置方法
Linux用户可以通过修改用户目录下的 .condarc 文件，一般路径为 ~/.condarc

Windows 用户无法直接创建名为 .condarc 的文件，可先执行 conda config --set show_channel_urls yes 生成该文件之后再修改，一般路径为

注：由于更新过快难以同步，不同步pytorch-nightly, pytorch-nightly-cpu, ignite-nightly这三个包。

.condarc 文件中用以下内容替换

```
channels:
  - defaults
show_channel_urls: true
default_channels:
  - http://mirrors.aliyun.com/anaconda/pkgs/main
  - http://mirrors.aliyun.com/anaconda/pkgs/r
  - http://mirrors.aliyun.com/anaconda/pkgs/msys2
custom_channels:
  conda-forge: http://mirrors.aliyun.com/anaconda/cloud
  msys2: http://mirrors.aliyun.com/anaconda/cloud
  bioconda: http://mirrors.aliyun.com/anaconda/cloud
  menpo: http://mirrors.aliyun.com/anaconda/cloud
  pytorch: http://mirrors.aliyun.com/anaconda/cloud
  simpleitk: http://mirrors.aliyun.com/anaconda/cloud

```
即可添加 Anaconda Python 免费仓库。