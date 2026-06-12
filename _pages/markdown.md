---
permalink: /markdown/
title: "Markdown 写作指南"
author_profile: true
redirect_from:
  - /md/
  - /markdown.html
---

{% include toc %}

## 写文章的基本流程

1. 在 `_posts/` 目录下新建一个 `.md` 文件
2. 文件名格式必须是 `YYYY-MM-DD-标题.md`，例如 `2026-06-13-jekyll-quickstart.md`
3. 在文件顶部加一段 frontmatter（YAML 格式）
4. 写正文（标准 Markdown）
5. `git add . && git commit -m "..." && git push`，5 分钟内自动构建

## Frontmatter 必填字段

```yaml
---
title: "文章标题"
date: 2026-06-13 14:30:00 +0800
categories: [技术]
tags: [Jekyll, 教程]
author: 博客作者
description: "一句话描述，SEO 用。"
---
```

可选字段：

- `permalink`：自定义 URL 路径
- `comments: false`：关闭评论
- `share: false`：关闭分享按钮
- `related: true`：显示相关文章
- `toc: true`：显示目录
- `modified_time`：最后修改时间

## 目录结构

- `_config.yml`：站点全局配置
- `_data/navigation.yml`：顶部导航菜单
- `_pages/`：独立页面（关于、归档、隐私等）
- `_posts/`：博客文章
- `_drafts/`：草稿（不会被发布）
- `_includes/`：Liquid 模板片段
- `_layouts/`：页面布局
- `_sass/`：样式表源文件
- `assets/`：静态资源（CSS、JS、图片）
- `images/`：网站图片
- `files/`：可下载文件（PDF 等）

## 常用 Markdown 语法

### 强调

```markdown
*斜体* 或 _斜体_
**粗体** 或 __粗体__
~~删除线~~
```

### 列表

```markdown
- 无序列表项 1
- 无序列表项 2
  - 嵌套项

1. 有序列表 1
2. 有序列表 2
```

### 链接与图片

```markdown
[链接文字](https://example.com)
![图片描述](/images/foo.png)
```

### 引用

```markdown
> 这是一段引用。
> 可以跨多行。
```

### 代码

````markdown
行内 `code` 用反引号。

代码块用三个反引号：

```python
def hello():
    print("Hello, World!")
```
````

### 表格

```markdown
| 列 1 | 列 2 |
|------|------|
| A    | B    |
| C    | D    |
```

## 高级功能

### 数学公式（MathJax）

```markdown
行内公式：$E = mc^2$

块级公式：

$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$
```

### 提示框

```markdown
> [!NOTE]
> 强调提示

> [!WARNING]
> 警告提示
```

### Emoji

本站启用了 [Jemoji](https://github.com/jekyll/jemoji) 插件，可以直接写：

```markdown
:rocket: :heart: :+1: :smile:
```

效果：🚀 ❤️ 👍 😄

## 调试技巧

- **本地预览**：`bundle exec jekyll serve`，浏览器打开 `http://localhost:4000`
- **构建错误**：看 GitHub Pages 的 build log，绿色对勾 = 成功，红色 X = 错误
- **修改 `_config.yml` 不生效**：必须重启 Jekyll 服务
- **中文路径报错**：项目根目录用纯 ASCII 路径

## 推荐资源

- [Markdown 官方教程](https://www.markdownguide.org/zh-hans/)
- [GitHub Flavored Markdown 规范](https://github.github.com/gfm/)
- [Jekyll 文档](https://jekyllrb.com/docs/posts/)
- [Liquid 模板语法](https://shopify.github.io/liquid/)
