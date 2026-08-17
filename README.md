# AI 学习站（ai_study_page）

把 AI 讲解视频 / 产业资料，整理成可反复阅读、图文并茂的**学习 HTML**，自动部署到 GitHub Pages。

## 站点结构
- `index.html` —— 落地页，链接各份学习文档
- `study-*.html` —— 各份学习文档（先进封装专题）
- `.nojekyll` —— 关闭 Jekyll，确保 HTML 原样发布
- `.github/workflows/pages.yml` —— push 即自动部署

## 自动部署原理
仓库已配置 GitHub Actions：任何 push 到 `main` 分支，都会触发 `Deploy to GitHub Pages`，
把仓库根目录作为静态站点发布。因此**新增/更新学习文档 = 提交即上线**，无需手动构建。

## 如何新增一份学习文档
1. 把生成的 HTML 放到仓库根目录（建议用 `study-xxx.html` 命名）。
2. 在 `index.html` 里加一张卡片链接它。
3. `git add . && git commit -m "add xxx" && git push`。
4. 等 Actions 跑完（约 30s~1min），站点自动更新。

## 运维提醒
- 首次需要在仓库 **Settings → Pages → Build and deployment → Source 选 "GitHub Actions"**。
- 文档里的图若是外链文件，请一并放入仓库；本专题三份文档均为单文件内联 SVG，无需额外资源。
- 内容仅供学习，不构成投资建议。
