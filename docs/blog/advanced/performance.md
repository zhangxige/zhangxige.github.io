---
title: 性能优化
date: 2025-01-22
---

# 性能优化

> 让 Zensical 站点加载更快、交互更流畅

## 即时导航与预加载

```toml
[project.theme]
features = [
    "navigation.instant",
    "navigation.instant.prefetch",
]
```

`navigation.instant` 让页面切换不刷新，`navigation.instant.prefetch` 会在鼠标悬停时预加载目标页面。即时导航依赖 `site_url`，请确保已经配置：

```toml
[project]
site_url = "https://zhangxige.github.io"
```

## 图片优化

- 优先使用 WebP 或 AVIF，必要时再提供 PNG/JPG 回退
- 在 Markdown 中显式设置宽度，避免布局抖动
- 首屏之外的图片使用懒加载
- 上传前压缩图片，避免直接使用几 MB 的原图

```markdown
![示例图片](assets/example.webp){ width="640" loading="lazy" }
```

## 字体与第三方资源

字体通常是中文站点最大的资源之一：

- 不要同时加载多套完整中文字体
- 优先使用系统字体或按需子集化字体
- 将 KaTeX、统计脚本等第三方资源改为本地托管或延迟加载

本站通过 `docs/stylesheets/ziti.css` 引入在线中文字体，如果更在意首屏速度，可以移除该文件并改用系统字体。

## 减少不必要的脚本

`docs/javascripts/` 下的脚本会随页面加载。只保留真正需要的功能，避免在 `document$` 回调中执行重计算或同步网络请求。

## 构建与检查

```bash
zensical build --clean
du -sh site
```

使用 Chrome DevTools 的 Lighthouse 面板检查：

- Performance
- Accessibility
- Best Practices
- SEO

重点关注 LCP、CLS 和第三方资源的加载时间。
