# Zhangxige's Website

> 个人技术博客 + Zensical 中文教程，基于 [Zensical](https://zensical.org/) 构建，自动部署到 GitHub Pages。

- 在线访问：<https://zhangxige.github.io>
- 博客文章：图像处理、Rust、Python、AI 编程工具
- 教程内容：Zensical 安装、配置、主题、博客、插件与部署

## 技术栈

| 组件 | 说明 |
|------|------|
| Zensical `0.0.74` | 静态站点生成器，使用 `zensical.toml` 配置 |
| Python `3.11+` | 运行 Zensical 所需环境 |
| Markdown | pymdown-extensions、PyGments |
| KaTeX | 数学公式渲染 |
| GitHub Actions | 自动构建并部署到 GitHub Pages |

## 本地开发

```bash
# 1. 创建并激活虚拟环境
python3 -m venv .venv
source .venv/bin/activate        # macOS / Linux
# .venv\Scripts\activate         # Windows

# 2. 安装依赖
pip install -r requirements.txt

# 3. 启动本地预览
zensical serve
```

打开 <http://127.0.0.1:8000> 查看效果。

构建静态文件：

```bash
zensical build --clean
```

构建结果输出到 `site/`，该目录不会提交到 Git。

## 项目结构

```text
.
├── docs/                       # 文档源文件
│   ├── index.md                # 首页
│   ├── about.md                # 关于
│   ├── faq.md                  # 常见问题
│   ├── showcase.md             # 案例展示
│   ├── assets/                 # Logo 等静态资源
│   ├── getting-started/        # 快速开始与迁移
│   ├── tutorials/              # 核心教程
│   ├── blog/
│   │   ├── index.md            # 博客首页（博客插件必需）
│   │   ├── posts/              # 博客文章
│   │   ├── plugins/            # 插件文档
│   │   ├── deployment/         # 部署文档
│   │   └── advanced/           # 高级主题
│   ├── javascripts/            # 自定义脚本
│   └── stylesheets/            # 自定义样式
├── zensical.toml               # Zensical 配置
├── requirements.txt            # Python 依赖
└── .github/workflows/docs.yml  # GitHub Pages 部署工作流
```

## 写一篇博客

在 `docs/blog/posts/` 下新建 Markdown 文件：

```markdown
---
title: 文章标题
date: 2026-11-01
authors:
  - zhangxige
categories:
  - Rust
tags:
  - Rust
  - 学习笔记
---

# 文章标题

正文内容……
```

作者 ID 需要先在 `docs/blog/.authors.yml` 中定义。博客插件会自动生成文章列表、日期归档、阅读时间和 RSS。文章默认按
`blog/{date}/{slug}` 生成 URL；设置为 `draft: true` 的文章不会出现在生产构建中。

## 配置说明

主要配置集中在 `zensical.toml`：

- `[project]`：站点名称、URL、作者、仓库信息
- `[project.theme]`：主题、语言、配色、导航特性
- `[project.plugins.blog]`：博客、分页、阅读时间与草稿
- `[project.plugins.rss]`：RSS 订阅
- `[project.markdown_extensions]`：Markdown 扩展

修改配置后执行 `zensical serve` 即可热更新预览。

## 部署

推送到 `main` 分支后，GitHub Actions 会自动执行：

```text
pip install -r requirements.txt
zensical build --clean
上传 site/ 并部署到 GitHub Pages
```

也可以在 Actions 页面手动触发 `Documentation` 工作流。

## 常见问题

**`zensical: command not found`**

确认虚拟环境已激活，并且执行过 `pip install -r requirements.txt`。

**依赖安装失败**

确认 Python 版本不低于 3.11：

```bash
python3 --version
```

**本地 8000 端口被占用**

```bash
zensical serve -a 127.0.0.1:8080
```

更多问题见 [常见问题](docs/faq.md)。

## 致谢

教程结构与部分文档来自
[Wcowin/Zensical-Chinese-Tutorial](https://github.com/Wcowin/Zensical-Chinese-Tutorial)，
感谢原作者的开源工作。

## License

MIT License，详见 [LICENSE](LICENSE)。
