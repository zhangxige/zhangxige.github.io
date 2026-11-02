---
title: 从 MkDocs 迁移到 Zensical
date: 2025-01-22
authors:
  - name: zhangxige
    email: daxuekanshijie@sina.cn
categories:
  - 迁移指南
---

# 从 MkDocs 迁移到 Zensical

> 完整的迁移指南，让你轻松从 MkDocs 过渡到 Zensical

## 为什么要迁移？

### MkDocs 的现状

- ⚠️ **已停止更新** - MkDocs 和 Material for MkDocs 不再积极开发
- ⚠️ **功能受限** - 缺少现代化功能（即时导航、博客系统等）
- ⚠️ **性能一般** - 加载速度和渲染性能有待提升

### Zensical 的优势

- ✅ **积极维护** - 由 Material for MkDocs 原团队开发
- ✅ **现代化** - 即时导航、博客系统、Modern 主题
- ✅ **高性能** - 优化的渲染引擎，更快的加载速度
- ✅ **向后兼容** - 支持读取 `mkdocs.yml` 配置文件
- ✅ **平滑过渡** - 提供自动迁移工具

## 迁移前准备

### 1. 备份项目

```bash
# 创建项目备份
cp -r my-mkdocs-site my-mkdocs-site-backup

# 或使用 Git
git checkout -b backup-before-zensical
git commit -am "Backup before migrating to Zensical"
```

### 2. 检查当前配置

记录你的 MkDocs 项目中使用的：

- [ ] 主题配置
- [ ] 插件列表
- [ ] 自定义 CSS/JS
- [ ] Hooks 脚本
- [ ] 模板覆盖

### 3. 安装 Zensical

```bash
# 安装 Zensical
pip install zensical

# 验证安装
zensical --version
```

## 迁移步骤

### 第一步：创建 zensical.toml

Zensical 推荐使用 `zensical.toml` 配置文件（虽然也支持 `mkdocs.yml`）。

#### 自动转换（推荐）

```bash
# Zensical 可以自动读取 mkdocs.yml
# 先测试是否能正常工作
zensical serve

# 如果正常，可以继续使用 mkdocs.yml
# 或手动创建 zensical.toml
```

#### 手动创建

**原 mkdocs.yml：**
```yaml
site_name: My Site
site_url: https://example.com
theme:
  name: material
  language: zh
```

**新 zensical.toml：**
```toml
[project]
site_name = "My Site"
site_url = "https://example.com"

[project.theme]
variant = "modern"  # 或 "classic"
language = "zh"
```

### 第二步：配置文件对照表

| MkDocs (YAML) | Zensical (TOML) | 说明 |
|---------------|-----------------|------|
| `site_name: "My Site"` | `site_name = "My Site"` | 网站名称 |
| `site_url: https://example.com` | `site_url = "https://example.com"` | 网站 URL |
| `theme: name: material` | `[project.theme]` | 主题配置 |
| `plugins: - search` | `[project.plugins.search]` | 插件配置 |
| `nav:` | `nav = [...]` | 导航配置 |
| `extra_css:` | `extra_css = [...]` | 额外 CSS |
| `extra_javascript:` | `extra_javascript = [...]` | 额外 JS |

### 第三步：迁移主题配置

#### 主题变体

Zensical 提供两种主题变体：

```toml
[project.theme]
# Modern 主题（推荐）- 全新设计
variant = "modern"

# Classic 主题 - 与 Material for MkDocs 完全一致
variant = "classic"
```

**建议：**
- 如果想要全新体验，选择 `modern`
- 如果想保持原样，选择 `classic`

#### 主题特性

**MkDocs:**
```yaml
theme:
  features:
    - navigation.tabs
    - navigation.sections
    - search.suggest
```

**Zensical:**
```toml
[project.theme]
features = [
    "navigation.tabs",
    "navigation.sections",
    "search.suggest",
]
```

#### 调色板

**MkDocs:**
```yaml
theme:
  palette:
    - scheme: default
      primary: indigo
      accent: indigo
```

**Zensical:**
```toml
[[project.theme.palette]]
scheme = "default"
primary = "indigo"
accent = "indigo"
```

### 第四步：迁移插件配置

#### 搜索插件

**MkDocs:**
```yaml
plugins:
  - search:
      separator: '[\s\-]'
```

**Zensical:**
```toml
[project.plugins.search]
separator = '[\s\u200b\-]'
```

#### 博客插件

**MkDocs (需要 mkdocs-material-blog 插件):**
```yaml
plugins:
  - blog:
      blog_dir: blog
```

**Zensical (内置):**
```toml
[project.plugins.blog]
post_date_format = "full"
draft = true
post_readtime = true
post_readtime_words_per_minute = 265
```

#### 标签插件

**MkDocs:**
```yaml
plugins:
  - tags
```

**Zensical:**
```toml
[project.plugins.tags]
```

### 第五步：处理 Hooks

⚠️ **重要：Zensical 不支持 MkDocs hooks**

Zensical 正在开发模块系统来替代 hooks。目前的解决方案：

#### 1. 评论系统

**原 MkDocs Hook:**
```python
# hooks/comments.py
def on_page_markdown(markdown, page, **kwargs):
    # 添加评论代码
    pass
```

**Zensical 替代方案:**
在 `overrides/partials/comments.html` 中配置：

```html
{% if page.meta.comments %}
<div id="comments">
  <!-- 你的评论系统代码 -->
</div>
{% endif %}
```

#### 2. 阅读时间

**原 MkDocs Hook:**
```python
def calculate_reading_time(markdown):
    # 计算阅读时间
    pass
```

**Zensical 替代方案:**
使用博客插件的内置功能：

```toml
[project.plugins.blog]
post_readtime = true
post_readtime_words_per_minute = 265
```

#### 3. 相关文章

**原 MkDocs Hook:**
```python
def get_related_posts(page):
    # 获取相关文章
    pass
```

**Zensical 替代方案:**
等待模块系统发布，或使用 JavaScript 实现。

### 第六步：迁移自定义样式

#### CSS 文件

**MkDocs:**
```yaml
extra_css:
  - stylesheets/extra.css
```

**Zensical:**
```toml
extra_css = [
    "stylesheets/extra.css",
]
```

CSS 文件内容通常不需要修改，但注意：

- Modern 主题可能需要调整一些样式
- Classic 主题完全兼容原有样式

#### JavaScript 文件

**MkDocs:**
```yaml
extra_javascript:
  - javascripts/extra.js
```

**Zensical:**
```toml
extra_javascript = [
    "javascripts/extra.js",
]
```

**即时导航兼容性：**

如果使用即时导航，需要监听 `document$` 事件：

```javascript
// 原 MkDocs
document.addEventListener('DOMContentLoaded', function() {
    // 初始化代码
});

// Zensical 即时导航
document$.subscribe(function() {
    // 初始化代码
});
```

### 第七步：迁移导航配置

#### 简单导航

**MkDocs:**
```yaml
nav:
  - Home: index.md
  - About: about.md
```

**Zensical:**
```toml
nav = [
    { "Home" = "index.md" },
    { "About" = "about.md" },
]
```

#### 嵌套导航

**MkDocs:**
```yaml
nav:
  - Home: index.md
  - Blog:
      - blog/index.md
      - Posts:
          - blog/post1.md
          - blog/post2.md
```

**Zensical:**
```toml
nav = [
    { "Home" = "index.md" },
    { "Blog" = [
        "blog/index.md",
        { "Posts" = [
            "blog/post1.md",
            "blog/post2.md",
        ]},
    ]},
]
```

### 第八步：迁移 Markdown 扩展

#### 基础扩展

**MkDocs:**
```yaml
markdown_extensions:
  - abbr
  - attr_list
  - admonition
```

**Zensical:**
```toml
[project.markdown_extensions]
abbr = {}
attr_list = {}
admonition = {}
```

#### PyMdown 扩展

**MkDocs:**
```yaml
markdown_extensions:
  - pymdownx.superfences:
      custom_fences:
        - name: mermaid
          class: mermaid
          format: !!python/name:pymdownx.superfences.fence_code_format
```

**Zensical:**
```toml
[project.markdown_extensions."pymdownx.superfences"]
custom_fences = [
    { name = "mermaid", class = "mermaid", format = "!!python/name:pymdownx.superfences.fence_code_format" }
]
```

### 第九步：测试和验证

#### 1. 本地测试

```bash
# 启动开发服务器
zensical serve

# 检查以下内容：
# - 页面是否正常显示
# - 导航是否正确
# - 样式是否正常
# - 搜索是否工作
# - 博客是否正常
```

#### 2. 构建测试

```bash
# 清理并构建
zensical build --clean

# 检查 site/ 目录
ls -la site/

# 检查是否有错误或警告
```

#### 3. 功能检查清单

- [ ] 所有页面都能正常访问
- [ ] 导航菜单正确显示
- [ ] 搜索功能正常
- [ ] 博客文章正确显示
- [ ] 自定义样式生效
- [ ] JavaScript 功能正常
- [ ] 图片和资源正确加载
- [ ] 移动端显示正常

### 第十步：部署

#### GitHub Pages 部署（推荐）

```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - uses: actions/configure-pages@v5
      - uses: actions/checkout@v5
      - uses: actions/setup-python@v5
        with:
          python-version: 3.x
      - run: pip install zensical
      - run: zensical build --clean
      - uses: actions/upload-pages-artifact@v4
        with:
          path: site
      - uses: actions/deploy-pages@v4
        id: deployment
```

详细步骤请参考 [GitHub Pages 部署指南](../blog/deployment/github-pages.md)。

#### Netlify 部署

```toml
# netlify.toml
[build]
command = "zensical build"
publish = "site"

[build.environment]
PYTHON_VERSION = "3.11"
```

#### GitHub Pages 部署

```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: 3.11
      - run: pip install zensical
      - run: zensical build
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./site
```

## 常见问题

### Q: 必须使用 zensical.toml 吗？

A: 不是必须的。Zensical 完全支持 `mkdocs.yml`，但推荐使用 `zensical.toml` 以获得更好的体验。

### Q: 我的自定义 CSS 还能用吗？

A: 大部分情况下可以。如果使用 Classic 主题，完全兼容。如果使用 Modern 主题，可能需要微调。

### Q: Hooks 怎么办？

A: Zensical 不支持 hooks。大部分功能可以通过：
- 模板覆盖
- JavaScript
- 内置插件
- 等待模块系统

### Q: 迁移需要多长时间？

A: 取决于项目复杂度：
- 简单项目：10-30 分钟
- 中等项目：1-2 小时
- 复杂项目：半天到一天

### Q: 可以同时保留 MkDocs 吗？

A: 可以。你可以在不同分支维护两个版本，或使用不同的配置文件。

## 完整示例

### 迁移前（MkDocs）

```yaml
# mkdocs.yml
site_name: My Blog
site_url: https://example.com
theme:
  name: material
  language: zh
  features:
    - navigation.tabs
    - search.suggest
  palette:
    - scheme: default
      primary: indigo

plugins:
  - search
  - tags

markdown_extensions:
  - abbr
  - attr_list
  - pymdownx.superfences

nav:
  - Home: index.md
  - Blog: blog/index.md
```

### 迁移后（Zensical）

```toml
# zensical.toml
[project]
site_name = "My Blog"
site_url = "https://example.com"

[project.theme]
variant = "modern"
language = "zh"
features = [
    "navigation.tabs",
    "search.suggest",
]

[[project.theme.palette]]
scheme = "default"
primary = "indigo"

[project.plugins.search]
[project.plugins.tags]
[project.plugins.blog]

[project.markdown_extensions]
abbr = {}
attr_list = {}

[project.markdown_extensions."pymdownx.superfences"]

nav = [
    { "Home" = "index.md" },
    { "Blog" = "blog/index.md" },
]
```

## 总结

迁移到 Zensical 的步骤：

1. ✅ 备份项目
2. ✅ 安装 Zensical
3. ✅ 创建 zensical.toml
4. ✅ 迁移配置
5. ✅ 处理 Hooks
6. ✅ 迁移样式和脚本
7. ✅ 测试验证
8. ✅ 部署上线

**恭喜！你已经成功迁移到 Zensical！** 🎉

---

**需要帮助？**
- 查看 [常见问题](../faq.md)
- 访问 [Zensical 官方文档](https://zensical.org/docs/)
- 加入 [GitHub Issues](https://github.com/zhangxige/zhangxige.github.io/issues)
