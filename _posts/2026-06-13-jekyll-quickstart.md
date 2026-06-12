---
title: "Jekyll 静态博客快速上手"
date: 2026-06-13 14:30:00 +0800
categories: [技术]
tags: [Jekyll, GitHub Pages, 教程]
author: 博客作者
description: "用 Jekyll + GitHub Pages 十分钟搭一个属于自己的静态博客，附中文踩坑指南。"
---

## 写在前面

如果你只想**最快**搭一个能写文章的博客，不关心主题、不关心评论、不关心 SEO，那 Jekyll + GitHub Pages 真的是 10 分钟就能搞定的事。这篇文章就把流程写清楚。

## 一分钟了解原理

```
你写 Markdown
    ↓ git push
GitHub 仓库收到代码
    ↓ 自动触发构建
Jekyll 渲染成 HTML
    ↓ CDN 分发
访客看到的就是普通网页
```

整个过程没有服务器，没有数据库，所有内容就是一堆 `.html` 文件，托管在 GitHub 的服务器上。

## 步骤 1：准备 GitHub 仓库

1. 注册/登录 GitHub
2. 新建仓库，**名字必须是 `<你的用户名>.github.io`**，**必须 public**
3. 其他选项（README/license/.gitignore）**都不要勾选**，保持空仓库

## 步骤 2：拉取一个现成主题

`Academic Pages` 是一个为学术 / 个人场景设计良好的 Jekyll 主题：

```bash
git clone https://github.com/academicpages/academicpages.github.io.git
cd academicpages.github.io
git remote set-url origin https://github.com/<你的用户名>/<你的用户名>.github.io.git
git push -u origin master
```

等 3-5 分钟，访问 `https://<你的用户名>.github.io/` 就能看到效果了。

## 步骤 3：写文章

所有文章放在 `_posts/` 目录，文件名格式：

```
YYYY-MM-DD-标题.md
```

文章内容用 Markdown 写，文件顶部要有 frontmatter：

```yaml
---
title: "文章标题"
date: 2026-06-13 14:30:00 +0800
categories: [技术]
tags: [Jekyll, 教程]
description: "一句话描述，用于 SEO。"
---

# 这是你的文章正文

用 **Markdown** 写就行。
```

写完 `git add . && git commit -m "新文章" && git push` 即可。

## 步骤 4：本地预览（可选）

不想每次都推到 GitHub 才看效果？本地装个 Ruby 就能实时预览：

```bash
# Windows: 从 https://rubyinstaller.org/ 下载 Ruby+Devkit 3.2
# Mac: brew install ruby
# Linux: apt install ruby-full

gem install bundler
cd <项目目录>
bundle install
bundle exec jekyll serve
# 浏览器打开 http://localhost:4000
```

每次改文件浏览器会自动刷新（livereload）。

## 常见踩坑

### 中文路径导致 Jekyll 报错

Jekyll 在 Windows 上对中文路径支持不完美。如果你的项目放在 `C:\Users\中文名\桌面\xxx`，可能会遇到编码错误。**解决办法**：把项目移到 `C:\dev\xxx` 之类的纯英文路径再开发。

### `bundle install` 下载慢

换国内 RubyGems 镜像：

```bash
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
```

### 修改 `_config.yml` 不生效

`_config.yml` 修改后**必须重启 Jekyll 服务**才能生效（其他文件改完会自动刷新）。

### 评论、SEO、Analytics

这些都需要在外部服务（Disqus / Giscus / Google Analytics 等）注册账号后，把 ID 填回 `_config.yml`。本站使用的是 [Giscus](https://giscus.app/zh-CN) + GA4，对中文社区最友好。

## 推荐资源

- [Jekyll 官方文档](https://jekyllrb.com/docs/)
- [Academic Pages 主题](https://github.com/academicpages/academicpages.github.io)
- [Minimal Mistakes 主题](https://github.com/mmistakes/minimal-mistakes)（更轻量）
- [Giscus 中文文档](https://giscus.app/zh-CN)

---

写博客这件事本身不难，难的是**坚持写下去**。愿你我都能坚持下去。
