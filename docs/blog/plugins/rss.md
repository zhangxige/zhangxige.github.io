---
title: RSS 插件配置
date: 2025-01-22
---

# RSS 插件配置

> 为博客生成 RSS/Atom 订阅源

## 当前配置

本站的 RSS 配置位于 `zensical.toml`：

```toml
[project.plugins.rss]
enabled = true
match_path = "blog/posts/.*"
use_git = false
categories = ["tags", "categories"]
image = "https://zhangxige.github.io/assets/logo.svg"
feed_ttl = 1440
length = 20
pretty_print = true
feed_description = "zhangxige 的技术博客与 Zensical 中文教程"
feed_title = "Zhangxige's Blog RSS Feed"

[project.plugins.rss.date_from_meta]
as_creation = "date"
as_update = "update"
datetime_format = "%Y-%m-%d"

[project.plugins.rss.url_parameters]
utm_source = "rss"
utm_medium = "feed"
```

## 关键选项

| 选项 | 说明 |
|------|------|
| `match_path` | 只收录匹配的页面，建议限定为 `blog/posts/.*` |
| `use_git` | 是否从 Git 提交历史读取更新时间；CI 构建建议设为 `false` |
| `length` | 订阅源中保留的最新文章数量 |
| `categories` | 从 front matter 的哪些字段生成分类 |
| `date_from_meta` | 从 `date` / `update` 字段读取时间 |
| `url_parameters` | 给订阅链接附加 UTM 参数，便于统计来源 |

## 文章 front matter

RSS 依赖文章元数据，至少提供标题和日期：

```markdown
---
title: 图像清晰度解析
date: 2026-03-01
categories:
  - 图像处理
tags:
  - 清晰度
---
```

## 验证订阅源

构建后检查 `site/` 根目录下的 feed 文件：

```bash
zensical build --clean
find site -maxdepth 1 -iname '*feed*'
```

部署后可以用浏览器或 RSS 阅读器打开对应地址，也可以使用在线 feed 校验工具检查 XML 是否合法。

## 常见问题

- **订阅源为空**：检查 `match_path` 是否匹配文章路径，以及文章是否被标记为草稿
- **时间不正确**：确认 front matter 中的 `date` 格式为 `YYYY-MM-DD`
- **分类缺失**：确认 `categories` 字段与配置中的 `categories` 选项一致
