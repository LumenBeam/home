<p>
<strong><h2>本明の主页</h2></strong>
个人主页 · <a href="https://lumenbeam.dpdns.org">lumenbeam.dpdns.org</a>
</p>

---

## 功能

- 载入动画
- 站点简介
- Hitokoto 一言
- 日期及时间
- 时光进度条
- 本地壁纸随机切换
- 移动端适配

> 天气模块需自备高德 Key，未配置时自动隐藏；音乐播放器已移除。

## 技术栈

- [Vue 3](https://cn.vuejs.org/)
- [Vite](https://cn.vitejs.dev/)
- [Pinia](https://pinia.vuejs.org/zh/)
- [Swiper](https://swiperjs.com/)
- [Element Plus](https://element-plus.org/zh-CN/)
- [IconPark](https://iconpark.oceanengine.com/official) / [xicons](https://xicons.org/)

## 本地开发

需要 Node.js 18+ 与 pnpm。

```bash
# 安装依赖
pnpm install

# 启动开发服务器（默认 http://localhost:3000）
pnpm dev

# 构建静态文件到 dist/
pnpm build
```

构建完成后，将 **`dist` 目录下的文件**上传至服务器即可。也可使用 Vercel、Cloudflare Pages 等平台导入仓库自动部署。

## 配置

所有站点信息集中在 `.env` 中（该文件不入库，请参考 `.env.example` 创建）：

```bash
# 站点信息
VITE_SITE_NAME = "站点名称"          # 浏览器标签页标题
VITE_SITE_ANTHOR = "作者名"          # 页脚作者
VITE_SITE_KEYWORDS = "关键词,个人主页"
VITE_SITE_DES = "站点简介"
VITE_SITE_URL = "example.com"       # 站点域名（用于页脚链接与 Logo）
VITE_SITE_START = "2026-11-11"      # 建站日期，留空则不显示
VITE_SITE_ICP = ""                  # ICP 备案号，留空则不显示

# 天气（留空则隐藏天气模块）
VITE_WEATHER_KEY = ""
```

### 网站链接

在 `src/assets/siteLinks.json` 中配置，`link` 留空则卡片点击无效：

```json
[
  {
    "icon": "Compass",
    "name": "起始页",
    "link": "https://lumenbeam.dpdns.org"
  }
]
```

`icon` 的图标名称需在 `src/components/Links.vue` 中引入，可前往 [xicons](https://xicons.org) 挑选。

### 社交链接

在 `src/assets/socialLinks.json` 中配置。列表为空时不显示社交栏：

```json
[
  {
    "name": "Github",
    "icon": "/images/icon/github.png",
    "tip": "去 Github 看看",
    "url": "https://github.com/yourname"
  }
]
```

### 壁纸与图标

- **背景图**：放入 `public/images/`，命名为 `background1.jpg` ~ `backgroundN.jpg`，并同步修改 `src/components/Background.vue` 中的随机数范围
- **站点图标**：放入 `public/images/icon/`，包括 `favicon.ico`、各尺寸 PWA 图标与 `logo.png`

### 字体

- **正文**：`HarmonyOS Sans`，通过 `index.html` 中的 CDN 引入
- **Logo**：`Pacifico`，位于 `public/font/Pacifico-Regular.ttf`（完整字形，支持任意域名）
- **时钟数字**：`UnidreamLED`，位于 `public/font/UnidreamLED.ttf`

## 目录结构

```
├─ public/              # 静态资源（原样复制到 dist）
│  ├─ font/             # 字体
│  └─ images/           # 背景图与图标
├─ src/
│  ├─ assets/           # 站点/社交链接配置
│  ├─ components/       # 组件
│  ├─ utils/            # 工具函数
│  ├─ views/            # 页面区块
│  ├─ App.vue
│  └─ main.js
├─ index.html
└─ vite.config.js
```

## 授权

本项目以 [MIT 协议](LICENSE) 发布，欢迎二次创作与学习使用。

> **可以**：下载、修改、分发，或在此基础上制作自己的主页，无需事先征得同意。
>
> **不可以**：将本项目（或其主体）打包成付费模板、商品或服务对外售卖。如需商业合作，请先与作者联系。

## 致谢

本项目基于 [imsyy/home](https://github.com/imsyy/home) 修改，遵循 MIT 协议。

<a title="Template" target="_blank" href="https://github.com/imsyy/home"><img src="https://img.shields.io/badge/Template-imsyy%2Fhome-blue"></a>

