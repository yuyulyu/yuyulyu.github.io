---
title: Rust, Rustlings Environment Configuration
description: Setting up Rust and Rustlings in various environments, and via remote access.
author: yoyo
date: 2024-09-19 23:14:00 +0800
categories: [Operating System, Rust]
tags: [rust, Linux]
---

## Linux

### Installing Linux on a Mac

### Access to university's Linux

```bash
ssh <username>@linux.bath.ac.uk
```

## Clone respotery from github

### Creating SSH Key

To clone GitHub repositories using SSH, generate an SSH key in the Linux environment with the following command:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

View and copy the public key:

```bash
cat ~/.ssh/id_rsa.pub
```

Go to GitHub, go to "<ins>Settings</ins>". On the settings page, click "<ins>SSH and GPG keys</ins>". Click "<ins>New SSH Key</ins>", paste the copied public key, add a description, and click "</ins>Add SSH Key<ins>".

### Clone the Repository Locally

#### Using SSH

In the GitHub repository, click the green "Code" button and select the SSH option. Copy the provided URL and then, in your local Linux environment, execute:

```bash
git clone <copied_ssh_url>
```

After cloning, use the ls command to view the cloned directory and cd to enter it. Install Rustlings with:

```bash
cargo install --force --path .
```

Using HTTPS

Alternatively, the repository can also be cloned by HTTPS:

```bash
git clone <copied_https_url>
```

## Install Rust & Rustlings

### Rust

To install Rust locally in a Linux environment, refer to the [ArceOS Tutorial Book](https://rcore-os.cn/arceos-tutorial-book/ch01-02.html)[^arceos]:

```bash
curl https://sh.rustup.rs -sSf | sh
```

After installation, reopen the terminal or apply the new environment variable settings with:

```bash
source $HOME/.cargo/env
```

Confirm the Rust toolchain installation:

```bash
rustc --version
```

### Rustlings

Navigate to the cloned directory and install:

```bash
cargo install --force --path .
```


[^arceos]:Arceos 教程 Rust 开发环境配置 - ArceOS Tutorial Book (rcore-os.cn): [https://rcore-os.cn/arceos-tutorial-book/ch01-02.html](https://rcore-os.cn/arceos-tutorial-book/ch01-02.html).

