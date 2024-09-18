---
title: Rust, Rustlings Environment Configuration
description: 
author: yoyo
date: 2024-09-20 11:33:00 +0800
categories: [Operating System, Rust]
tags: [rust, Linux]
---

## Linux

### 这一段写mac怎么本地安装Linux环境

### Access to university's Linux

```bash
ssh <username>@linux.bath.ac.uk
```

## Clone respotery from github

### 创建ssh key

用于ssh方式克隆github代码。在linux环境下，使用ssh-keygen -t rsa -b 4096 -C "你的邮箱"命令，创建ssh key，下面的选项全部直接敲回车即可。 随后使用 cat ~/.ssh/id_rsa.pub 命令查看生成的公钥，并完整的复制下来。 在github仓库界面点击自己的头像，选择settings。进入到设置页面后，点击左侧的SSH and GPG keys选项。点击New SSH key选项，并将复制下来的内容粘贴上去，添加该ssh key的描述。随后点击Add SSH key，并一路点击确认即可。

### clone实验仓库到本地

#### ssh

在前面点击链接生成的仓库中，同样点击醒目的 code 绿色按钮，选择local下的ssh选项，复制下面的链接。随后回到本地linux环境下，使用git clone 复制的链接的方式，将目标仓库clone到本地。随后，使用ls命令查看自己clone下来的文件夹，再使用cd命令进入到该文件夹下，使用  cargo install --force --path . 安装rustlings。

#### html

## Install Rust & Rustlings

### Rust

本地安装rust。进入linux环境下，参考[Arceos 教程 Rust 开发环境配置 - ArceOS Tutorial Book (rcore-os.cn)](https://rcore-os.cn/arceos-tutorial-book/ch01-02.html) 中，找到Rust 开发环境配置的章节，相应配置即可，你可以同时将后续需要的环境也配置好.

首先安装 Rust 版本管理器 rustup 和 Rust 包管理器 cargo，这里我们用官方的安装脚本来安装：

```bash
curl https://sh.rustup.rs -sSf | sh
```

安装完成后，我们可以重新打开一个终端来让之前设置的环境变量生效。我们也可以手动将环境变量设置应用到当前终端，只需要输入以下命令：

```bash
source $HOME/.cargo/env
```

接下来，我们可以确认一下我们正确安装了 Rust 工具链：

```bash
rustc --version
```

可以看到当前安装的工具链的版本。

接下来安装一些Rust相关的软件包

```bash
rustup target add riscv64gc-unknown-none-elf
rustup component add llvm-tools-preview
rustup component add rust-src
```

### Rustlings

随后，使用ls命令查看自己clone下来的文件夹，再使用cd命令进入到该文件夹下，使用  cargo install --force --path . 安装rustlings。

