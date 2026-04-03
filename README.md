# 黑森信息科技 官网项目

## 文件结构

```
heisen-website/
├── index.html                   ← 主网页文件（直接用浏览器打开即可预览）
├── README.md                    ← 本说明文件
└── assets/
    ├── icons/                   ← Logo & 图标
    │   ├── logo-heisen-dark.png     黑森主Logo（深色背景用）
    │   ├── logo-heisen-filled.png   黑森Logo（白底填充版）
    │   ├── logo-heisen-outline.png  黑森Logo（描边版）
    │   ├── logo-xiaomu.png          小木广告Logo
    │   └── favicon.png              ← 【待替换】网站小图标（建议32×32或64×64）
    └── images/
        ├── hero/                ← 首屏背景图
        │   └── hero-bg.jpg          ← 【可选】首屏背景图（建议1920×1080，深色）
        ├── brands/              ← 品牌配图
        │   ├── xiaomu-cover.jpg     ← 小木广告品牌图（建议800×600）
        │   └── himi-cover.jpg       ← himi AI 品牌图（建议800×600）
        ├── about/               ← 关于我们配图
        │   └── team.jpg             ← 【可选】团队/办公室照片（建议1200×800）
        ├── works/               ← 作品案例图（核心素材）
        │   ├── work-01.jpg          ← 案例1（任意尺寸，瀑布流自适应）
        │   ├── work-02.jpg
        │   ├── work-03.jpg
        │   ├── work-04.jpg
        │   ├── work-05.jpg
        │   ├── work-06.jpg
        │   ├── work-07.jpg
        │   ├── work-08.jpg
        │   └── work-09.jpg
        └── clients/             ← 客户Logo（可选）
            ├── client-01.png        ← 建议透明背景PNG，高度统一60px左右
            ├── client-02.png
            └── ...
```

---

## 如何替换素材

### 1. 替换作品案例图片

在 `index.html` 找到 JS 中的 `data` 数组，将 `emoji` 字段改为图片引用：

```js
// 原来（占位符）
{ title:'完美日记 618 大促视觉', emoji:'💄', h:280, ... }

// 替换为图片
{ title:'完美日记 618 大促视觉', img:'assets/images/works/work-01.jpg', h:280, ... }
```

同时更新 renderWorks 函数中的图片渲染逻辑（见 index.html 底部注释）。

### 2. 替换品牌封面图

在对应的 `.brand-card` 区块中加入背景图：

```html
<div class="brand-card xiaomu" style="background-image:url('assets/images/brands/xiaomu-cover.jpg');background-size:cover">
```

### 3. 替换 Logo

导航栏 Logo 引用：在 `nav` 中找到 `.nav-logo-box`，替换为：

```html
<img src="assets/icons/logo-heisen-filled.png" width="32" height="32" alt="黑森">
```

### 4. 添加客户 Logo 跑马灯

将客户Logo图片放入 `assets/images/clients/`，在 `.clients-track` 中替换文字为图片：

```html
<span class="ci"><img src="assets/images/clients/client-01.png" alt="天猫" height="32"></span>
```

---

## 图片规格建议

| 位置 | 建议尺寸 | 格式 | 备注 |
|------|---------|------|------|
| 作品案例 | 600×400 ~ 600×800 | JPG/WebP | 高度不同，形成瀑布流效果 |
| 品牌封面 | 800×600 | JPG | 深色系为佳 |
| 客户Logo | 任意宽 × 60px | PNG（透明背景） | 统一高度即可 |
| Hero背景 | 1920×1080 | JPG | 可选，网站有渐变背景 |
| Favicon | 64×64 | PNG/ICO | 浏览器标签图标 |

---

## 本地预览

直接双击 `index.html` 用 Chrome / Safari 打开即可。
如需完整字体效果，需联网（Google Fonts）或将字体文件本地化。

## 上线部署

将整个 `heisen-website` 文件夹上传至服务器或静态托管平台即可：
- 阿里云 OSS 静态托管
- 腾讯云 COS
- Vercel / Netlify（免费）
- GitHub Pages（免费）
