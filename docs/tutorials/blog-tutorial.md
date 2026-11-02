---
title: Zensical 博客系统完全指南
date: 2025-01-22
authors:
  - name: zhangxige
    email: daxuekanshijie@sina.cn
categories:
  - Zensical
  - 教程
---

# Zensical 博客系统完全指南

> 本教程将详细讲解如何在 Zensical 中创建和管理博客

## 概述

Zensical 的博客系统是一个强大的内置功能，无需额外插件即可开箱即用。它支持：

- 📝 **文章管理** - 自动生成博客索引和存档
- 🏷️ **标签系统** - 按标签分类文章
- 📅 **日期管理** - 自动按日期排序
- 👥 **作者信息** - 显示文章作者和联系方式
- ⏱️ **阅读时间** - 自动计算文章阅读时间
- 📄 **草稿功能** - 支持草稿和发布状态

## 项目结构

```
docs/
├── blog/
│   ├── index.md              # 博客首页（必需）
│   ├── .authors.yml          # 作者信息文件（可选）
│   ├── posts/                # 博客文章目录
│   │   ├── 2025-01-22-first-post.md
│   │   ├── 2025-01-23-second-post.md
│   │   └── ...
│   └── archive.md            # 博客存档页面（可选）
└── index.md                  # 网站首页
```

!!! warning "重要"
    - `blog/index.md` 文件是必需的，没有这个文件博客功能无法正常工作
    - `blog/posts/` 目录可以不存在，但建议创建以组织文章

## 配置博客插件

在 `zensical.toml` 中配置博客插件：

```toml
[project.plugins.blog]
# 日期格式：full（完整）、medium（中等）、short（简短）
post_date_format = "full"

# 显示阅读时间
post_readtime = true
post_readtime_words_per_minute = 265  # 中文适配（推荐值）

# 启用草稿功能
draft = true

# 自动将未来日期的文章标记为草稿
draft_if_future_date = true

# 文章 URL 格式
post_url_format = "{date}/{slug}"

# 分页设置
pagination_per_page = 10
pagination_url_format = "page/{page}"

# 作者信息文件（可选）
authors_file = "blog/.authors.yml"
```

!!! tip "快速启用"
    只需在 `zensical.toml` 中添加 `[project.plugins.blog]` 即可启用博客功能，所有配置都有合理的默认值。

## 创建博客文章

### 基础文章结构

创建一个新的 Markdown 文件，例如 `docs/blog/posts/2025-01-22-my-first-post.md`：

```markdown
---
title: 我的第一篇博客文章
date: 2025-01-22
authors:
  - zhangxige
categories:
  - 技术
  - Python
---

# 我的第一篇博客文章

这是文章的内容...
```

### Front Matter 详解

| 字段 | 类型 | 说明 |
|------|------|------|
| `title` | 字符串 | 文章标题（必需） |
| `date` | 日期 | 发布日期，格式：YYYY-MM-DD（必需） |
| `authors` | 数组 | 作者 ID 列表，需在 `docs/blog/.authors.yml` 中定义 |
| `categories` | 数组 | 文章分类 |
| `tags` | 数组 | 文章标签 |
| `draft` | 布尔值 | 是否为草稿（默认：false） |
| `comments` | 布尔值 | 是否启用评论（默认：true） |

### 完整示例

```markdown
---
title: 深入理解 Python 装饰器
date: 2025-01-22
authors:
  - zhangxige
  - zhangsan
categories:
  - 技术
  - Python
tags:
  - 装饰器
  - 函数式编程
draft: false
comments: true
---

# 深入理解 Python 装饰器

## 什么是装饰器？

装饰器是 Python 中一个强大的特性...

## 基础用法

```python
def my_decorator(func):
    def wrapper():
        print("Something before the function is called.")
        func()
        print("Something after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
```

## 高级用法

...更多内容...
```

## 文章命名规范

推荐使用以下命名规范：

```
YYYY-MM-DD-article-slug.md
```

例如：
- `2025-01-22-python-decorators.md`
- `2025-01-23-zensical-tutorial.md`
- `2025-01-24-web-development-tips.md`

**优点：**
- 便于按日期排序
- 清晰的文章标识
- 自动生成 URL 时更友好

## 草稿管理

### 标记为草稿

```markdown
---
title: 未完成的文章
date: 2025-01-22
draft: true
---
```

**草稿特性：**
- 在开发环境（`zensical serve`）中可见
- 在生产环境（`zensical build`）中隐藏
- 适合保存未完成的文章

### 自动草稿

如果文章日期是未来日期，会自动标记为草稿：

```markdown
---
title: 计划中的文章
date: 2025-12-31  # 未来日期，自动标记为草稿
---
```

## 作者信息

### 作者 ID 与 .authors.yml

Zensical 的博客 `authors` 字段必须是**作者 ID 字符串**，不能直接写 `name` / `email` 对象。先在 `docs/blog/.authors.yml` 中定义作者：

```yaml
authors:
  zhangxige:
    name: zhangxige
    description: 图像处理 / Rust / AI 编程
    avatar: https://github.com/zhangxige.png

  zhangsan:
    name: 张三
    description: 技术博主
    avatar: https://example.com/zhangsan.png
```

然后在文章 front matter 中引用作者 ID：

```markdown
---
title: 文章标题
authors:
  - zhangxige
  - zhangsan
---
```

!!! tip "作者信息文件"
    使用 `.authors.yml` 可以：

    - 统一管理作者信息
    - 避免重复定义
    - 方便更新作者信息
    - 支持作者头像和描述

## 分类和标签

### 分类

分类用于组织文章的主题：

```markdown
---
title: 文章标题
categories:
  - 技术
  - Python
  - Web 开发
---
```

### 标签

标签用于更细粒度的分类：

```markdown
---
title: 文章标题
tags:
  - 装饰器
  - 函数式编程
  - 高级特性
---
```

## 博客首页

创建 `docs/blog/index.md`：

```markdown
---
title: 博客
hide:
  - toc
---

# 博客

欢迎来到我的博客！这里分享技术、生活和思考。

## 最新文章

<!-- 博客文章会自动列出 -->

## 分类

- [技术](../blog/)
- [生活](../blog/)
- [思考](../blog/)
```

## 高级配置

### 自定义阅读时间

根据你的读者群体调整每分钟阅读字数：

```toml
[project.plugins.blog]
# 英文：200-250 字/分钟
# 中文：250-300 字/分钟
post_readtime_words_per_minute = 265
```

### 自定义 URL 格式

```toml
[project.plugins.blog]
# 默认格式：{date}/{slug}
# 结果：/2025/01/22/my-article/
post_url_format = "{date}/{slug}"

# 其他选项：
# {slug} - 仅文章名称
# {categories}/{slug} - 分类/文章名称
```

### 分页配置

```toml
[project.plugins.blog]
# 每页显示文章数
pagination_per_page = 5

# 分页 URL 格式
pagination_url_format = "page/{page}"
```

## 最佳实践

### 1. 文件组织

```
docs/blog/posts/
├── 2025-01-22-getting-started.md
├── 2025-01-23-advanced-tips.md
├── 2025-01-24-best-practices.md
└── ...
```

### 2. 文章摘要

在文章开头添加摘要，会自动显示在博客列表中：

```markdown
---
title: 文章标题
date: 2025-01-22
---

这是文章的摘要，会显示在博客列表中。

<!-- more -->

这部分内容只在点击"阅读更多"后显示。
```

### 3. 使用 Front Matter 优化

```markdown
---
title: 优化的文章标题
date: 2025-01-22
authors:
  - zhangxige
categories:
  - 主分类
tags:
  - 标签1
  - 标签2
  - 标签3
draft: false
comments: true
---
```

### 4. 定期更新

- 每周发布 1-2 篇文章
- 定期审查和更新旧文章
- 保持内容的相关性和准确性

## 常见问题

### Q: 如何删除文章？

A: 直接删除对应的 Markdown 文件，重新构建网站即可。

### Q: 如何修改已发布的文章？

A: 编辑 Markdown 文件，保存后自动更新。

### Q: 如何改变文章发布日期？

A: 修改 Front Matter 中的 `date` 字段，文章会自动重新排序。

### Q: 如何隐藏某篇文章？

A: 将 `draft: true` 添加到 Front Matter，或删除该文件。

### Q: 如何为文章添加评论？

A: 在 Front Matter 中设置 `comments: true`，并在 `overrides/partials/comments.html` 中配置评论系统。

## 总结

Zensical 的博客系统提供了强大而灵活的功能：

✅ **开箱即用** - 无需额外配置即可开始写博客  
✅ **功能完整** - 支持分类、标签、作者、阅读时间等  
✅ **易于管理** - 简单的 Markdown 文件结构  
✅ **高度可定制** - 灵活的配置选项  

现在你已经掌握了 Zensical 博客系统的全部知识，开始写你的第一篇文章吧！

---

**更多资源：**
- [Zensical 官方文档](https://zensical.org/docs/)
- [Markdown 语法指南](https://zensical.org/docs/authoring/markdown/)
- [主题定制指南](https://zensical.org/docs/customization/)
