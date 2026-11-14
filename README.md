# WebNav Hub - PornNav

# WebNav Hub - LinkHub PornNav导航

[English](#english) | [中文](#中文)

<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/bbylw/PicGo@master/20241220015300647.png" alt="WebNav Hub Preview" width="100%">
</div>

<a name="english"></a>

## 🎨 Design Inspiration

This project's UI design and color scheme is directly inspired by Pornhub's iconic black and orange theme. The choice was deliberate, leveraging the instantly recognizable color palette that has become a cultural phenomenon and internet meme, often referenced in various UI design discussions and parodies.

- Primary Theme Color: `#ff9000` (Pornhub Orange)
- Background: `#0d0d0d` (Dark Black)
- Card Background: `#1a1a1a`
- Text: `#ffffff` (White)

## 🌟 Features & Modern Web Guidance

This project introduces **[Modern Web Guidance](https://developer.chrome.com/docs/modern-web-guidance)** standards to audit and modernize [index.html](index.html) while keeping the visual UI completely unchanged.

### Modern Design

- Responsive grid layout with signature black-and-orange cards
- Smooth animations and transitions respecting `prefers-reduced-motion`
- Native dark color scheme (`<meta name="color-scheme" content="dark">` + `:root { color-scheme: dark; }`) for browser scrollbars and FOUC prevention
- Optimized for both desktop and mobile devices

### Modern Web Guidance Enhancements

- **Semantic Markup & Accessibility (`html` / `accessibility`)**:
  - Semantic `<ul class="link-grid" role="list">` / `<li class="link-card">` structure with `<h3><a>` stretched links (via `::after`), eliminating duplicate screen-reader announcements
  - Decorative icons marked with `aria-hidden="true"`
  - Keyboard skip link (`跳到主内容`) targeting `<main id="main-content" tabindex="-1">`
  - High-contrast `:focus-visible` outlines powered by `:has(> h3 > a:focus-visible)` and `scroll-padding-top` so the sticky `<nav>` never obscures headings or focused cards
- **Native Scrollspy (`scrollspy`)**:
  - CSS `scroll-target-group: auto` and `:is(:target-current, .active)` with an `IntersectionObserver` fallback and synchronized `aria-current="true"`
- **Rendering & Load Performance (`defer-rendering-heavy-content` / `performance`)**:
  - Below-the-fold sections deferred with `content-visibility: auto` and per-section `contain-intrinsic-block-size`
  - `<link rel="preconnect" href="https://cdn.jsdelivr.net" crossorigin />` and non-blocking scripts placed at the end of `<body>`
- **External Subresource Security (`secure-external-subresources`)**:
  - CDN stylesheets hardened with Subresource Integrity (`integrity="sha384-..."`), `crossorigin="anonymous"`, and `referrerpolicy="no-referrer"`, alongside `<meta name="referrer" content="strict-origin-when-cross-origin" />`
- **Color, High Contrast & Motion (`color` / `motion`)**:
  - `@media (forced-colors: active)` boundaries for cards, active navigation links, skip link, and dialogs
  - Motion transitions and smooth scrolling gated behind `@media (prefers-reduced-motion: no-preference)`
- **Native Modals (`declarative-dialog-popover-control` / `light-dismiss-a-dialog`)**:
  - Footer info modals powered by declarative `commandfor` / `command="show-modal"` buttons and `<dialog closedby="any">` with feature-detected fallbacks (`commandForElement` and `closedBy`)

## 🚀 Deployment Options

### GitHub Pages Deployment

1. Fork this repository
2. Go to repository Settings > Pages
3. Select main branch as source
4. Your site will be available at `https://[username].github.io/[repo-name]`

### Cloudflare Pages Deployment

1. Connect your GitHub repository to Cloudflare Pages
2. Set build settings:
   - Build command: `N/A` (static site)
   - Build output directory: `/`
3. Deploy and access via Cloudflare's URL

### Custom Domain Setup

1. Register at [dynv6](https://dynv6.com)
2. Add a new domain and configure DNS settings
3. Point domain to your deployment URL
4. Update DNS settings in your deployment platform

## 🛠 Customization

### Adding New Links

Add new links inside the appropriate `<ul class="link-grid" role="list">` using this format:

```html
<li class="link-card">
  <i class="[ICON-CLASS]" aria-hidden="true"></i>
  <h3><a href="[URL]" target="_blank" rel="noopener noreferrer">[TITLE]</a></h3>
</li>
```

### Modifying Categories

Categories are defined by `<section>` elements with `tabindex="-1"` and `<h2 class="category-title">`:

```html
<section id="[CATEGORY-ID]" tabindex="-1">
  <h2 class="category-title">[CATEGORY-NAME]</h2>
  <ul class="link-grid" role="list">
    ...
  </ul>
</section>
```

## 📱 Browser Support

- Modern browsers with CSS Grid, `:has()`, `content-visibility: auto`, and `scroll-target-group` support
- Built-in progressive enhancement and feature-detected fallbacks (`IntersectionObserver`, `commandForElement`, `closedBy`) for older browsers

## 🔒 Security

- **External Links**: All outbound card links include `rel="noopener noreferrer"` to prevent `window.opener` exploitation and referrer leakage
- **External Subresources**: Third-party CDN assets use pinned versions with `integrity` (SRI), `crossorigin="anonymous"`, `referrerpolicy="no-referrer"`, and `<meta name="referrer" content="strict-origin-when-cross-origin" />`

## 📄 License

This project is open-source and available under the MIT License.

---

<a name="中文"></a>

## 🎨 设计灵感

本项目的界面设计和配色方案直接借鉴自 Pornhub 的标志性黑橙配色。这是一个刻意的设计选择，利用了这个已成为文化现象和网络模因的即时可识别配色方案，经常在各种 UI 设计讨论和模仿作品中被引用。

- 主题主色：`#ff9000`（Pornhub 橙）
- 背景色：`#0d0d0d`（深黑色）
- 卡片背景：`#1a1a1a`
- 文字颜色：`#ffffff`（白色）

## 🌟 功能特点与 Modern Web Guidance 规范实践

本项目已引入 **[Modern Web Guidance](https://developer.chrome.com/docs/modern-web-guidance)** 现代 Web 开发最佳实践指南，对 [index.html](index.html) 进行了全面审核与升级，在**完全保持原有视觉 UI 不变**的前提下，全面提升了无障碍访问、渲染性能、安全防护与原生交互体验。

### 现代设计

- 响应式网格布局与标志性黑橙主题卡片
- 顺滑的悬停动效与滚动过渡，并完整尊重系统减弱动态效果偏好
- 原生深色模式适配（`<meta name="color-scheme" content="dark">` 与 `:root { color-scheme: dark; }`），优化原生滚动条并防止加载白屏闪烁
- 针对桌面端与移动端多断点深度适配

### 引入 Modern Web Guidance 带来的核心改进

- **语义化结构与无障碍访问（`html` / `accessibility`）**：
  - 将卡片列表升级为 `<ul class="link-grid" role="list">` 与 `<li class="link-card">`，采用 `<h3><a>` + `::after` 整卡点击模式，消除读屏器重复播报并移除对 JS 注入 `aria-label` 的依赖
  - 为所有纯装饰性图标静态标记 `aria-hidden="true"`
  - 新增键盘跳转链接（`跳到主内容`）直达 `<main id="main-content" tabindex="-1">`
  - 借助 `:has(> h3 > a:focus-visible)` 绘制不被裁剪的卡片焦点框，并通过 `scroll-padding-top` 确保吸顶导航栏不会遮挡标题或聚焦卡片
- **原生 Scrollspy 滚动高亮（`scrollspy`）**：
  - 使用 CSS 原生 `scroll-target-group: auto` 与 `:is(:target-current, .active)` 自动跟踪当前可见分类，并为不支持的浏览器提供 `IntersectionObserver` 降级与 `aria-current="true"` 同步
- **渲染与加载性能优化（`defer-rendering-heavy-content` / `performance`）**：
  - 对首屏以下的分类区块启用 `content-visibility: auto`，并按各分类实际卡片数配置 `contain-intrinsic-block-size`
  - 为第三方 CDN 添加 `<link rel="preconnect" href="https://cdn.jsdelivr.net" crossorigin />`，并将页面脚本统一后置到 `</body>` 前消除解析阻塞
- **外部子资源安全（`secure-external-subresources`）**：
  - 为外链 Font Awesome 样式表配置 SRI 校验（`integrity="sha384-..."`）、`crossorigin="anonymous"` 与 `referrerpolicy="no-referrer"`，并设置文档级 `<meta name="referrer" content="strict-origin-when-cross-origin" />`
- **色彩、高对比度与动态偏好（`color` / `motion`）**：
  - 新增 `@media (forced-colors: active)` 规则，保障 Windows 高对比度模式下卡片、激活导航、跳转链接与弹窗的清晰边界
  - 将位移/缩放动画与平滑滚动统一收敛到 `@media (prefers-reduced-motion: no-preference)`
- **原生声明式弹窗（`declarative-dialog-popover-control` / `light-dismiss-a-dialog`）**：
  - 页脚“隐私政策 / 使用条款 / 联系我们”采用 `commandfor` / `command="show-modal"` 与 `<dialog closedby="any">` 原生模态弹窗，并为旧浏览器提供特性检测降级方案（`commandForElement` 与 `closedBy`）

## 🚀 部署选项

### GitHub Pages 部署

1. Fork 本仓库
2. 进入仓库设置 > Pages
3. 选择 main 分支作为源
4. 您的站点将在 `https://[用户名].github.io/[仓库名]` 可用

### Cloudflare Pages 部署

1. 将您的 GitHub 仓库连接到 Cloudflare Pages
2. 设置构建选项：
   - 构建命令：`N/A`（静态站点）
   - 构建输出目录：`/`
3. 部署并通过 Cloudflare 提供的 URL 访问

### 自定义域名设置

1. 在 [dynv6](https://dynv6.com) 注册
2. 添加新域名并配置 DNS 设置
3. 将域名指向您的部署 URL
4. 在部署平台更新 DNS 设置

## 🛠 自定义设置

### 添加新链接

在对应分类的 `<ul class="link-grid" role="list">` 中按以下格式添加新卡片：

```html
<li class="link-card">
  <i class="[图标类名]" aria-hidden="true"></i>
  <h3><a href="[URL]" target="_blank" rel="noopener noreferrer">[标题]</a></h3>
</li>
```

### 修改分类

分类使用带有 `tabindex="-1"` 的 `<section>` 元素及 `category-title` 标题定义：

```html
<section id="[分类ID]" tabindex="-1">
  <h2 class="category-title">[分类名称]</h2>
  <ul class="link-grid" role="list">
    ...
  </ul>
</section>
```

## 📱 浏览器支持

- 支持 CSS Grid、`:has()`、`content-visibility: auto` 与 `scroll-target-group` 的现代浏览器
- 为旧版浏览器提供基于特性检测的渐进增强与降级方案（`IntersectionObserver`、`commandForElement`、`closedBy`）

## 🔒 安全性

- **外部链接安全**：所有卡片外链均配置 `rel="noopener noreferrer"`，防止 `window.opener` 漏洞并避免引用来源泄露
- **外部子资源校验**：第三方 CDN 样式表启用固定版本 + SRI 完整性校验（`integrity`）、`crossorigin="anonymous"`、`referrerpolicy="no-referrer"` 与文档级 `<meta name="referrer" content="strict-origin-when-cross-origin" />`

## 📄 许可证

本项目采用 MIT 许可证开源。

---

Created with ❤️ by AI, enhanced by humans
由 AI 创建，人类优化
