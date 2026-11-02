---
title: Zhangxige 的技术博客
hide:
#   - navigation
#   - toc 
  - footer
comments: false
---

<center><font class="custom-font ml3">技术博客 · 图像处理 · Rust · AI 编程</font></center>

<style>
.custom-font {
    font-size: 31px;
    color: #757575;
}
@media (max-width: 768px) {
    .custom-font {
        font-size: 25px;
    }
}
</style>


<div class="grid cards" markdown>

-   :material-rocket-launch:{ .lg .middle } __为什么选择 Zensical？__

    ---
    
    ![Zensical Logo](https://zensical.org/assets/zensical.svg){ class="responsive-image" align=right width="200" style="border-radius: 15px;" }
    
    - [x] MkDocs 已停止更新，Zensical 是官方推荐的新一代
    - [x] 即时导航，无需刷新页面
    - [x] 博客系统，开箱即用
    - [x] 性能优异，加载迅速
    - [x] 𝕙𝕒𝕧𝕖 𝕒 𝕘𝕠𝕠𝕕 𝕥𝕚𝕞𝕖 !
    
    === "Mac/PC端"
        请在上方标签选择分类/左侧目录选择文章
    
    === "移动端"
        请点击左上角图标选择分类和文章

</div>
<style>
    @media only screen and (max-width: 768px) {
        .responsive-image {
            display: none;
        }
    }
</style>

> 这里记录我在图像处理、Rust、Python 和 AI 编程工具方面的学习与实践，同时整理了一份持续更新的 **Zensical 中文教程**。无论你是想阅读技术笔记，还是第一次接触 Zensical，都可以从这里开始。𝓳𝓾𝓼𝓽 𝓮𝓷𝓳𝓸𝔂 𝓲𝓽～

---

<div class="grid cards" markdown>

-   :simple-zenn:{ .lg .middle } __Zensical 快速开始（必看）__

    ---
    
    - [5 分钟快速开始](getting-started/quick-start.md)
    - [Zensical 博客系统完全指南](tutorials/blog-tutorial.md)
    - [zensical.toml 配置详解](tutorials/configuration.md)
    - [从 MkDocs 迁移到 Zensical](getting-started/migration.md)
    - [常见问题解答](faq.md)

-   :material-palette:{ .lg .middle } __主题定制__

    ---
    
    - [主题配置指南](tutorials/theme-customization.md)
    - [配置详解](tutorials/configuration.md)

-   :material-puzzle:{ .lg .middle } __插件系统__

    ---
    
    - [博客插件详解](blog/plugins/blog.md)
    - [搜索插件配置](blog/plugins/search.md)
    - [标签插件使用](blog/plugins/tags.md)
    - [RSS 插件配置](blog/plugins/rss.md)

-   :material-rocket:{ .lg .middle } __部署指南__

    ---
    
    - [GitHub Pages 部署（推荐）](blog/deployment/github-pages.md)
    - [Netlify 部署](blog/deployment/netlify.md)
    - [GitLab Pages 部署](blog/deployment/gitlab-pages.md)
    - [自托管部署](blog/deployment/self-hosted.md)

</div>

<!-- ## 🆚 Zensical vs MkDocs

| 特性 | Zensical | MkDocs |
|------|----------|--------|
| **维护状态** | ✅ 积极开发 | ⚠️ 已停止更新 |
| **即时导航** | ✅ 原生支持 | ❌ 需要插件 |
| **博客系统** | ✅ 开箱即用 | ⚠️ 需要插件 |
| **性能** | ✅ 优异 | ⚠️ 一般 |
| **现代化** | ✅ 现代设计 | ⚠️ 传统设计 |
| **配置文件** | TOML | YAML |
| **中文支持** | ✅ 完整 | ✅ 完整 | -->

## 📚 推荐学习路径

### 初学者路线

1. **第一步**：阅读 [5 分钟快速开始](getting-started/quick-start.md)
2. **第二步**：学习 [zensical.toml 配置详解](tutorials/configuration.md)
3. **第三步**：掌握 [博客系统完全指南](tutorials/blog-tutorial.md)
4. **第四步**：尝试 [主题定制](tutorials/theme-customization.md)
5. **第五步**：部署到线上 [GitHub Pages 部署](blog/deployment/github-pages.md)

### 从 MkDocs 迁移

1. **第一步**：阅读 [从 MkDocs 迁移到 Zensical](getting-started/migration.md)
2. **第二步**：了解 [配置文件差异](tutorials/configuration.md)
3. **第三步**：测试和调整
4. **第四步**：重新部署

### 高级用户路线

1. **性能优化**：阅读 [性能优化指南](blog/advanced/performance.md)
2. **SEO 优化**：学习 [SEO 优化](blog/advanced/seo.md)
3. **多语言支持**：配置 [多语言支持](blog/advanced/i18n.md)
4. **自定义 404 页面**：学习 [自定义 404 页面](blog/advanced/custom-404.md)
5. **自定义字体**：配置 [自定义字体](blog/advanced/custom-fonts.md)
6. **添加评论系统**：配置 [评论系统](blog/advanced/comment-system.md)
7. **扩展开发**：等待 Zensical 模块系统发布

## 🎯 核心特性

### 即时导航

Zensical 的即时导航功能让你的网站像单页应用一样流畅：

```toml
[project.theme]
features = [
    "navigation.instant",      # 即时导航
    "navigation.instant.prefetch",  # 预加载
]
```

!!! warning "重要"
    即时导航需要设置 `site_url` 才能正常工作：
    
    ```toml
    [project]
    site_url = "https://example.com"
    ```

### 博客系统

博客文章按日期归档，支持分类、标签和 RSS 订阅：

- [浏览全部文章](blog/index.md)
- [OpenSpec + OpenCode：高效 Vibe Coding](blog/posts/OpenSpec_OpenCode_VibeCoding.md)
- [图像清晰度解析](blog/posts/Image_Clarity.md)

### Modern 主题

全新的 Modern 主题变体，更现代、更美观：

```toml
[project.theme]
variant = "modern"  # 或 "classic"
```

## 🚀 快速开始

```bash
# 创建虚拟环境
python3 -m venv .venv
source .venv/bin/activate  # macOS/Linux
# 或 .venv\Scripts\activate  # Windows

# 安装 Zensical
pip install zensical

# 创建新项目
zensical new .

# 启动开发服务器
zensical serve
```

打开浏览器访问 [http://localhost:8000](http://localhost:8000)

详细步骤请阅读 [5 分钟快速开始](getting-started/quick-start.md)

## 📖 文档结构

```
zhangxige.github.io/
├── docs/
│   ├── index.md                    # 本页面
│   ├── about.md                    # 关于页面
│   ├── faq.md                      # 常见问题
│   ├── showcase.md                 # 案例展示
│   ├── tags.md                     # 标签索引
│   ├── assets/                     # Logo 等静态资源
│   ├── getting-started/            # 快速开始
│   │   ├── quick-start.md          # 5 分钟快速开始
│   │   └── migration.md            # 从 MkDocs 迁移
│   ├── tutorials/                   # 核心教程
│   │   ├── blog-tutorial.md        # 博客系统完全指南
│   │   ├── configuration.md        # 配置详解
│   │   ├── theme-customization.md  # 主题定制
│   │   └── markdown-extensions.md  # Markdown 扩展
│   ├── blog/
│   │   ├── index.md                # 博客首页
│   │   ├── .authors.yml            # 作者信息
│   │   ├── posts/                  # 博客文章
│   │   ├── plugins/                # 插件文档
│   │   ├── deployment/             # 部署指南
│   │   └── advanced/              # 高级主题
│   ├── javascripts/                # 自定义脚本
│   └── stylesheets/                # 自定义样式
├── zensical.toml                   # 配置文件
├── requirements.txt                # Python 依赖
└── .github/workflows/docs.yml      # GitHub Pages 部署
```

## 💡 实用技巧

!!! tip "提示"
    - 使用 `zensical serve` 实时预览
    - 使用 `zensical build --clean` 清理构建
    - 查看 [官方文档](https://zensical.org/docs/) 获取最新信息

!!! warning "注意"
    Zensical 不支持 MkDocs hooks，请使用模板覆盖或 JavaScript 替代

!!! info "信息"
    本教程持续更新，与 Zensical 官方版本同步

## 🌟 案例展示

- [Zhangxige's Website](https://zhangxige.github.io) - 本站，使用 Zensical 构建
- [Wcowin 的博客](https://wcowin.work) - 上游中文教程模板作者的个人博客
- [更多案例](showcase.md) - 查看更多精彩案例

## 🤝 参与贡献

欢迎参与本站的完善：

1. Fork [zhangxige/zhangxige.github.io](https://github.com/zhangxige/zhangxige.github.io)
2. 创建你的特性分支
3. 提交你的修改
4. 推送到分支
5. 创建 Pull Request

## 📞 联系方式

- **GitHub**: [zhangxige](https://github.com/zhangxige)
- **Email**: [daxuekanshijie@sina.cn](mailto:daxuekanshijie@sina.cn)

---

<center>
<b>开始你的 Zensical 之旅吧！</b> 🚀

</center>

<!--
  将所有页面级脚本和元数据统一放置在这里
-->
<!-- 访问统计区域 -->
<div style="text-align: center; margin: 2rem 0; font-size: 0.9rem;">
  本站访问量：<script async src="//finicounter.eu.org/finicounter.js"></script><span id="finicount_views" style="font-weight: bold; color: #518FC1;"></span>
</div>

<!-- Umami Analytics -->
<script defer src="https://cloud.umami.is/script.js" data-website-id="061b4dea-9b7b-4ffa-9071-74cde70f3dfb"></script>

<style>
body::before {
  --size: 35px;
  --line: color-mix(in hsl, canvasText, transparent 80%);
  content: '';
  height: 100vh;
  width: 100%;
  position: absolute;
  background: linear-gradient(
        90deg,
        var(--line) 1px,
        transparent 1px var(--size)
      )
      50% 50% / var(--size) var(--size),
    linear-gradient(var(--line) 1px, transparent 1px var(--size)) 50% 50% /
      var(--size) var(--size);
  -webkit-mask: linear-gradient(-20deg, transparent 50%, white);
          mask: linear-gradient(-20deg, transparent 50%, white);
  top: 0;
  transform-style: flat;
  pointer-events: none;
  z-index: -1;
}

@media (max-width: 768px) {
  body::before {
    display: none;
  }
}
</style>
