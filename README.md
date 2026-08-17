# AI 学习站（ai_study_page）

把 AI 讲解视频 / 产业资料，整理成可反复阅读、图文并茂的**学习 HTML**，自动部署到 GitHub Pages。

## 站点结构
- `index.html` —— 落地页，链接各份学习文档
- `study-*.html` —— 各份学习文档（先进封装专题）
- `.nojekyll` —— 关闭 Jekyll，确保 HTML 原样发布
- `.github/workflows/pages.yml` —— push 即自动部署

## 自动部署原理
仓库的 GitHub Pages 已设为 **从 `main` 分支根目录构建（legacy 模式）**。任何 push 到 `main` 分支，
GitHub 都会自动重新构建并发布站点。因此**新增/更新学习文档 = 提交即上线**，零构建、零额外配置。

## 如何新增一份学习文档
1. 把生成的 HTML 放到仓库根目录（建议用 `study-xxx.html` 命名）。
2. 在 `index.html` 里加一张卡片链接它。
3. `git add . && git commit -m "add xxx" && git push`。
4. 几十秒后站点自动更新（GitHub 会自动构建并部署）。

## 运维提醒
- 部署方式：仓库 **Settings → Pages → Build and deployment → Source = "Deploy from a branch"（分支选 main / 根目录）**。已启用，无需改动。
- 根目录的 `.nojekyll` 用于关闭 Jekyll，确保 HTML 原样发布。
- 文档里的图若是外链文件，请一并放入仓库；本专题三份文档均为单文件内联 SVG，无需额外资源。
- 内容仅供学习，不构成投资建议。
