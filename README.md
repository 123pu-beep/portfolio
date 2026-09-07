# 季彦君｜个人作品集（百度网盘链接版）

纯 HTML + CSS + JavaScript 静态网页，可部署到 GitHub Pages。
影片点击后在新标签页打开百度网盘，提取码已包含在链接中。
无需腾讯云、服务器、数据库或构建命令。简历不公开，仅保留邮箱。

## 文件结构

- index.html：页面结构
- style.css：样式
- script.js：根据数据渲染页面
- data/portfolio-data.js：全部个人资料、作品、图片路径及视频链接
- assets/images/：图片与图集
- assets/thumbnails/：视频封面
- .nojekyll：让 GitHub Pages 直接提供静态文件
- .gitignore：排除视频原片、密钥和临时文件

## 修改内容

打开 data/portfolio-data.js，保留引号、逗号和括号，只修改相应字段：

| 内容 | 数据位置 |
| --- | --- |
| 首页文字与地名 | hero |
| 姓名、品牌、年份 | site |
| 人物资料卡 | profile |
| 数据统计 | stats |
| 影片标题、说明、分工 | film[].title / meta / role |
| 影片网盘地址 | film[].link（保留 ?pwd=提取码） |
| 视觉图集封面、标题、图片 | visualAccordion[].image / label / gallery |
| 项目案例图片和多行滚动图片 | caseStudy.image / galleryRows |
| 项目案例介绍及状态 | caseStudy（保持开发中） |
| 经历与荣誉 | experienceGroups |
| 技能 | skills |
| 关于我 | about |
| 邮箱 | site.email 与 contact.email |

selectedWorks、visual、imageFolderImages 为旧版备用数据，目前页面没有直接渲染这些板块。修改当前影片请改 film。
本站没有简历下载入口；不要把简历 PDF 放进发布目录。
图片替换时保留大小写一致的相对路径，图片仍放 assets/images，封面放 assets/thumbnails。
照片及图集保留原文件；不包含 MP4 视频，也不要把百度网盘分享页填写成 video 标签的播放地址。

## 本地预览

解压后双击 index.html。检查影片链接、图集和移动端布局。链接的实际有效期与访问要求以百度网盘为准。

## 用 GitHub Desktop 上传（适合这个图片较多的项目）

1. 登录你自己的 GitHub 账号，在 GitHub Desktop 选择 File → New repository。
2. 新建仓库，例如 portfolio-jyj。打开仓库目录。
3. 将本压缩包解压后的文件和 assets、data 文件夹复制到仓库根目录，让 index.html 位于最外层。不要上传 ZIP 本身，不要复制旧项目的 .git。
4. Commit 后 Publish repository。免费账号使用公开仓库部署 Pages；发布的源码和图片也会公开。
5. 在 GitHub 仓库 Settings → Pages 中选择 Deploy from a branch，选择实际上传分支（通常 main）和 / (root)，Save。
6. 等待部署完成，从 Pages 页面打开显示的网址。常见格式为 https://用户名.github.io/仓库名/。

后续修改数据或图片后 Commit、Push 即会重新部署。
若旧仓库提交历史包含大视频，仅删掉当前文件不一定能解决推送失败；用这个不带历史的文件包建立新仓库更简单。
GitHub Pages 的国内访问速度会随网络变化；此版本不代表已经完成腾讯云大陆部署。

官方指南：https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
