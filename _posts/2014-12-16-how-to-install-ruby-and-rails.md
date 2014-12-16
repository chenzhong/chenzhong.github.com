---
layout: post
title:  快速正确安装ruby rails 环境
---

###步骤1

> 安装homebrew, 通过它安装系统所需要的包

```
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go/install)"
```
> 安装完成后，`brew doctor` 自检一下(可能要等一段时间)

###步骤2

> 安装rvm

```
curl -L https://get.rvm.io | bash -s stable
```
> 载入环境

```
source ~/.rvm/scripts/rvm
```

> 检查下是否安装正确

```
$ rvm -v
rvm 1.26.4 (master) by Wayne E. Seguin <wayneeseguin@gmail.com>, Michal Papis <mpapis@gmail.com> [https://rvm.io/]
```

### 步骤3

> 通过rvm安装ruby环境

```
$ rvm install 2.1.3
```

> 等待一段时间，就可以安装好

> 替换原有的ruby gem源

```
$ gem source -r https://rubygems.org/
$ gem source -a https://ruby.taobao.org
```

### 安装rails环境

```
$ gem install rails

$ rails -v
```

### 根据项目设置ruby版本及独立的gem环境

> 在项目根目录中，创建两个文件， `.ruby-version`, `.ruby-gemset`

> 在.ruby-version文件中，可以指定ruby的版本，在.ruby-gemset中，指定rails及相应的gem.


### oh My Zsh

> oh my zsh 跟 iterm2 是使用mac的必备，建议使用。
> oh my zsh [安装指南](https://github.com/robbyrussell/oh-my-zsh)

###  macvim

```
brew install ctags macvim --env-std --override-system-vim
```

> [vim配置](https://github.com/chenzhong/vim)