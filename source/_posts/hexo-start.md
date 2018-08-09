---
title: Hexo Start
date: 2018-08-08 19:43:43
tags:
  - hexo
  - blog tool
categories:
  - hexo
top_img: false
---

# [Hexo](https://hexo.io/docs/)

> 一个静态博客框架，支持使用[Markdown](https://daringfireball.net/projects/markdown/)编写文章，然后生成静态网站
> 有很多第三方[主题](https://hexo.io/themes/)可选，也可以自定义主题
> 支持部署到多种平台，例如：Git、Heroku、Rsync
> 丰富的[插件](https://hexo.io/plugins/)，例如：hexo-browsersync

# Quick Start

## 安装依赖

```bash
brew install git
brew install node
brew install yarn
yarn global add hexo-cli
```

## 创建博客

```bash
# 创建项目
hexo init <folder>

# 启动服务, http://localhost:4000
cd <folder>
yarn install
hexo server

# 添加新博客
hexo new "my-post"

# 编辑内容
vim source/_posts/my-post.md
```

## [部署](https://hexo.io/docs/deployment.html)

```yaml
# _config.yml
deploy:
  type: git
  repo: git@github.com:xxx/xxx.git
  branch: master
  message: "{{ now('YYYY-MM-DD HH:mm:ss') }}"
```

```bash
yarn add hexo-deployer-git
hexo deploy -g
```