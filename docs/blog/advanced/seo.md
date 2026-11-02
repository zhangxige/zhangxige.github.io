---
title: SEO 优化
date: 2025-01-22
---

# SEO 优化

> 让搜索引擎更好地收录你的 Zensical 站点

## 基础信息

在 `zensical.toml` 中配置站点级信息：

```toml
[project]
site_name = "Zhangxige's Website"
site_url = "https://zhangxige.github.io"
site_description = "zhangxige 的技术博客与 Zensical 中文教程"
site_author = "zhangxige"
```

`site_url` 会影响 sitemap、规范链接和即时导航，部署后应填写真实域名。

## 页面级元数据

在每篇文章的 front matter 中补充标题和描述：

```markdown
---
title: 图像清晰度解析
description: 从分辨率、锐度、噪声和压缩四个维度理解图像清晰度。
---
```

- `title` 应唯一，避免多个页面共用同一标题
- `description` 用一两句话概括页面内容
- 正文使用清晰的层级标题（`##`、`###`），不要跳级

## 内容结构

- 每页只保留一个 `#` 一级标题
- 图片添加有意义的 `alt` 文本
- 使用内部链接连接相关文章
- 避免发布重复或空白页面

## sitemap 与 RSS

Zensical 构建时会生成 `site/sitemap.xml`。部署后检查：

```bash
curl https://zhangxige.github.io/sitemap.xml
```

RSS 配置见 [RSS 插件配置](../plugins/rss.md)，它可以帮助读者订阅更新，也能为聚合器提供内容索引。

## 性能与移动端

页面速度、移动端适配和可访问性都会影响搜索表现。参考 [性能优化](performance.md)，并用 Lighthouse 检查移动端得分。

## 上线后的检查

1. 在 Google Search Console 或 Bing Webmaster Tools 中提交 sitemap
2. 检查首页和文章页的 `<title>`、`description`
3. 确认没有 404 的内部链接
4. 观察一段时间的收录和点击数据，再调整内容方向
