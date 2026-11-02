---
title: 标签插件使用
date: 2025-01-22
---

# 标签插件使用

> 用标签把相关文章组织起来

## 启用标签插件

在 `zensical.toml` 中配置：

```toml
[project.plugins.tags]
tags_file = "tags.md"
```

`tags_file` 指向标签索引页面，本站对应 `docs/tags.md`。

## 给文章添加标签

在文章 front matter 中写入 `tags`：

```markdown
---
title: Rust 学习记录
date: 2026-01-09
tags:
  - Rust
  - 学习笔记
---
```

同一篇文章可以有多个标签，标签名建议保持简洁并统一大小写。

## 标签图标

主题允许为标签配置图标：

```toml
[project.theme.icon.tag]
default = "lucide/hash"
html = "fontawesome/brands/html5"
js = "fontawesome/brands/js"
css = "fontawesome/brands/css3"
```

也可以在 `[project.extra.tags]` 中把标签名映射到样式：

```toml
[project.extra.tags]
HTML5 = "html"
JavaScript = "js"
CSS = "cs"
```

## 标签索引页

`docs/tags.md` 是标签的聚合入口，使用 `<!-- material/tags -->` 指令渲染标签列表：

```markdown
---
title: 标签
---

# 标签

按标签浏览站内文章。

<!-- material/tags -->
```

构建后访问 `/tags/` 即可查看所有标签及对应文章。

## 使用建议

- 标签用于横向关联主题，分类用于纵向归档，两者不要完全重复
- 控制标签数量，避免出现大量只包含一篇文章的标签
- 修改标签名时同步检查旧文章，避免同一概念出现多种写法
