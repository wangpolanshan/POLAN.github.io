# POLAN ASCII ART 网页逻辑梳理

## 页面结构

- `index.html`：首页入口，包含品牌 Hero、18 个设计分类、设计方法和联系方式。
- `category-*.html`：18 个分类详情页，形成一条线性浏览链。
- `assets/`：AI 生成图和三张绘图素材；AI 分类页通过相对路径加载 `assets/ai-text-generated.png`。
- `styles.css`：全站共享视觉系统。原压缩包缺失，本次补齐。
- `critique.json`：设计评审记录，描述了深色网格、字符密度、等宽字体、扫描线和运动系统。

## 导航逻辑

1. 首页顶部导航锚定到 `#works`、`#method`、`#contact`。
2. 18 个分类行通过普通 HTML 链接进入对应详情页。
3. 详情页底部提供“上一个分类 / 返回全部分类 / 下一个分类”三级导航。
4. 每个页面按相对路径引用 `styles.css` 和 `assets/`，适合 GitHub Pages 静态托管。

## 交互逻辑

- `pointermove` 持续更新 `--cx` / `--cy`，驱动页面十字光标和背景微光。
- `Escape` 会跳回 `index.html`。
- AI 分类页保留 WebGL 场景接口，但当前 Three.js 脚本被显式禁用，实际显示生成图和 `WEBGL / READY` 状态。
- 当前内容以占位为主，详情页尚未接入 CMS、后端 API 或表单提交逻辑。

## GitHub Pages 注意事项

- 这是纯静态多页面，不需要 Node.js、Python 或数据库运行时。
- 发布时必须保留全部 `category-*.html`、`assets/` 和共享 `styles.css`。
- 不应上传压缩包内的 `Python/` 目录；它是随原型打包的本地运行时，不属于网页部署依赖。
