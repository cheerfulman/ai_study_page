# AI 学习站（ai_study_page）

把产业资料、研报与讲解视频，整理成可反复阅读、图文并茂的**学习 HTML**，自动部署到 GitHub Pages。

🌐 站点地址：<https://cheerfulman.github.io/ai_study_page/>

---

## 内容分类

站点按**专题**归档，主页提供分类筛选（点击顶部标签即可只看某一专题）。

| 专题 | 篇数 | 内容 |
|---|---|---|
| **医药 · 创新药与上游** | 2 | 创新药板块驱动逻辑、AI 制药上游八模块（含化学药/生物药区分、龙头与增量判断） |
| **半导体 · 先进封装** | 3 | 图文详解、产业链图谱、视频学习笔记 |
| **AI 算力 · 光互连** | 1（+2 份研究底稿） | 从可插拔光模块到 CPO 的技术演进与产业链标的 |
| **AI 算力 · PCB 产业链** | 1 | 玻纤/电子布/Q布、树脂、铜箔与可剥铜 → CCL → mSAP → PCB/IC 载板 → 玻璃基板全链路拆解 |

---

## 目录结构

```
.
├── index.html                              # 落地页：分类导航 + 文档卡片 + 筛选
├── .nojekyll                               # 关闭 Jekyll，确保 HTML 原样发布
├── README.md
│
├── study-innovative-drug-sector.html       # 医药 · 创新药板块与近岸蛋白上涨逻辑
├── study-ai-pharma-upstream.html           # 医药 · AI 制药上游八模块与龙头拆解
│
├── study-advanced-packaging-illustrated.html  # 半导体 · 先进封装图文详解
├── study-advanced-packaging-chain.html        # 半导体 · 先进封装产业链图谱
├── study-advanced-packaging-notes.html        # 半导体 · 先进封装视频笔记
│
├── study-ai-optical-interconnect.html      # AI 算力 · 光互连
├── study-pcb-industry-chain.html           # AI 算力 · PCB 上下游产业链全景
├── AI光互连产业链深度研究_20260901.md          # 研究底稿
└── AI光互连价值迁移标的梳理_20260901.md        # 研究底稿
```

---

## 如何新增一份文档

1. **放文件**：把生成的 HTML 放到仓库根目录，命名建议 `study-<topic>.html`（用英文短横线命名，避免中文文件名导致 URL 编码后不可读）。
2. **加卡片**：在 `index.html` 里对应专题的 `<section data-cat="...">` 下加一张卡片：

   ```html
   <a class="card" href="study-xxx.html">
     <div class="top"><span class="badge b-blue">类型标签</span><span class="date">2026-09-18</span></div>
     <h3>标题</h3>
     <p>一句话摘要（讲清这篇解决什么问题）</p>
     <div class="foot">阅读全文 →</div>
   </a>
   ```

   同时更新顶部筛选标签里的篇数 `<span class="n">N</span>` 和头部的统计数字。

3. **提交上线**：

   ```bash
   git add . && git commit -m "add: xxx" && git push
   ```

   约 30 秒后站点自动更新。

### 新增一个专题

在 `index.html` 中：
1. 顶部 `.chips` 里加一个 `<button class="chip" data-filter="新专题key">专题名<span class="n">N</span></button>`
2. `<main>` 里加 `<section data-cat="新专题key">…</section>`

筛选逻辑会自动接管，无需改 JS。

---

## 自动部署原理

仓库的 GitHub Pages 已设为 **从 `main` 分支根目录构建（legacy 模式）**。任何 push 到 `main`，
GitHub 都会自动重新构建并发布。**新增/更新文档 = 提交即上线，零构建、零额外配置。**

---

## 运维提醒

- **部署设置**：仓库 Settings → Pages → Build and deployment → Source = *Deploy from a branch*，分支选 `main`、目录选 `/ (root)`。已启用，无需改动。
- **`.nojekyll`**：关闭 Jekyll，确保 HTML 原样发布（Jekyll 会忽略下划线开头的文件/目录）。
- **单文件优先**：本仓库所有学习文档均为单文件内联 CSS/SVG/JS，无外部依赖，便于迁移与离线阅读。
  少数文档从 CDN 引入 ECharts（`cdn.jsdelivr.net`），离线时图表不显示但正文完整。
- **命名规范**：新增文档用 `study-` 前缀 + 英文短横线命名，保持仓库整洁。
- **内容性质**：全部内容仅供学习与研究参考，**不构成投资建议**。

---

## 维护记录

| 日期 | 变更 |
|---|---|
| 2026-09-18 | 新增「医药 · 创新药与上游」专题（2 篇）；主页重构为分类筛选布局；README 补充目录结构与新增文档规范 |
| 2026-09-19 | 新增「AI 算力 · PCB 产业链」专题（1 篇）：PCB 上下游全链路梳理，含定位矩阵与玻璃基板 TGV 流程图 |
