# 季彦君｜一页式个人网页作品集

这是一个纯 HTML + CSS + JavaScript 的静态作品集网页。网页内容由 `data/portfolio-data.js` 驱动，页面结构、样式与数据已经分离。

## 文件结构

```text
index.html                 页面结构，只放 section、容器和导航
style.css                  黑白灰 + 暗红的响应式样式
script.js                  读取数据并渲染页面
data/portfolio-data.js     后续替换内容的唯一入口
assets/images/             项目图集、AI 视觉、分镜与场景图
assets/thumbnails/         所有视频/项目封面图
assets/videos/             本地 mp4 视频
```

## 以后怎么替换内容

打开 `data/portfolio-data.js`，只改 `window.PORTFOLIO_DATA` 里面的值即可。

### 首页文字

修改 `hero`：

```js
hero: {
  kicker: "AIGC / FILM / VISUAL",
  overline: "Digital media artist",
  title: "你的首页主标题",
  intro: "你的首页简介",
  location: "Shanghai / Hangzhou",
  note: "Available for selected projects"
}
```

### Core Data 人物资料卡

修改 `profile` 对象即可替换资料卡中的姓名、身份、网名、状态、头像和三条资料。资料卡使用原生 JavaScript 实现了鼠标跟随高光与轻微 3D 倾斜效果，不需要安装 React。

```js
profile: {
  name: "你的名字",
  title: "你的身份描述",
  handle: "你的网名",
  status: "开放合作",
  contactText: "联系我",
  avatar: "assets/images/头像.jpg",
  facts: ["教育经历", "常用工具", "核心方向"]
}
```

### 作品展示图片墙

修改 `showcaseImages` 数组即可替换三行循环展示的图片。页面加载时会随机打乱图片顺序，并自动分配到三行；鼠标移入时会暂停当前行。

```js
showcaseImages: [
  "assets/images/你的图片.jpg",
  "assets/images/另一张图片.png"
]
```

### 项目标题、简介、角色和分类

修改 `selectedWorks` 数组中的对象：

```js
{
  title: "项目标题",
  en: "PROJECT TITLE",
  category: "Film / AI",
  role: "你的项目职责",
  description: "项目简介",
  thumb: "assets/thumbnails/封面.jpg",
  video: { mode: "local", src: "assets/videos/项目.mp4" }
}
```

### 视频链接 / 视频模式

支持三种模式：

```js
video: { mode: "local", src: "assets/videos/demo.mp4" }
video: { mode: "embed", src: "https://外部平台的-iframe-地址" }
video: { mode: "link", src: "https://外部视频链接", poster: "assets/thumbnails/封面.jpg" }
```

如果暂时没有视频链接，可以删掉 `video` 字段，页面会保留封面并显示 `Coming Soon / 暂未上线`。本地视频放进 `assets/videos/`，封面放进 `assets/thumbnails/`。

### 图片路径和图集

所有项目图片统一放进 `assets/images/`。封面统一放进 `assets/thumbnails/`。修改 `thumb` 或 `image` 为对应相对路径；需要图集时修改 `gallery` 数组：

```js
gallery: [
  "assets/images/image-01.jpg",
  "assets/images/image-02.jpg"
]
```

点击 Visual 卡片会打开图集弹窗；《未写完的航线》的开发中详情图集由 `caseStudy.gallery` 控制。

### 联系方式

修改 `site.email` 和 `contact.email`。当前网页只保留邮箱，不挂载简历下载链接。

### 简历下载链接

如果未来需要放简历，可在 `contact` 中增加 `resume` 字段，并在 `script.js` 中绑定一个按钮；目前按要求没有加入简历入口。

## 本地预览

直接双击 `index.html` 一般即可查看。若浏览器限制本地视频或脚本加载，可以在当前文件夹启动任意静态服务器后访问，例如 VS Code Live Server。网页没有后端、数据库、React 或 ComfyUI 依赖。

## 上传 GitHub

上传整个项目文件夹时，请保留 `index.html`、`style.css`、`script.js`、`data/` 和 `assets/` 的相对位置。GitHub Pages 可以直接发布根目录，进入仓库的 Settings → Pages，选择部署分支和 `/ (root)` 文件夹即可。网页入口是 `index.html`。

## 当前内容说明

- 《未写完的航线》明确标注为 `In Development / 开发中`，没有写成完成项目。
- 《青山医靠》内容强调执行导演、AI 图像生成与剪辑参与；AI 视觉排版部分作为视觉策划图集展示。
- 《显影》标注为导演；《潮汐与尘埃》标注为个人完成；《西溪且留下》标注为拍摄策划与剪辑；微综艺标注为参演。
