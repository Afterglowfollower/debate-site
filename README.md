# 舆论监督权四重证成 — AI 多智能体辩论实录

一个交互式网页,展示 Claude + 3 个 Hermes agent 扮演四位思想家(汉娜·阿伦特、尤尔根·哈贝马斯、杰里米·边沁、迈克尔·舒德森)就"舆论监督是否是一项权利"进行的四轮辩论,并对接五位国内学者(石毕凡、侯健、李洋、郭道晖、刘练军)的学理综述。

## 内容

- 四位思想家 × 四轮讨论 = 16 篇原始发言
- 完整课程论文(≤3000 字,核心论证)
- 写作手记(约 1200 字)
- 国内学理综述(5 篇实时检索)

## 本地预览

直接双击 `index.html` 即可在浏览器中打开。无需任何依赖。

## 发布到 GitHub Pages

### 零命令行:浏览器上传(最简)

1. 登录 github.com,点右上角 `+` → `New repository`,仓库名随意(例:`debate-arendt-habermas`),**公开**(Public),勾选 "Add a README",创建。
2. 进入新仓库,点 `Add file` → `Upload files`,把这个目录里的 **`index.html`** 和 **`data.js`** 拖进去,`Commit changes`。
3. 到 `Settings` → `Pages`,`Source` 选 `Deploy from a branch`,`Branch` 选 `main` / `(root)`,`Save`。
4. 等 1-2 分钟,刷新 Pages 页面,顶部会出现公开链接 `https://<用户名>.github.io/<仓库名>/`,复制分享。

### 用 gh CLI(更快,如果你装了)

```bash
# 一次性配置
brew install gh
gh auth login

# 发布
cd /Users/bytedance/Desktop/cooking/debate-site
gh repo create debate-site --public --source=. --push
# 到 GitHub 仓库 Settings → Pages → Source: main, / (root) → Save
```

## 文件说明

- `index.html` — 单文件页面,嵌入所有 CSS + JS,无外部依赖
- `data.js` — 预先把 markdown 转成 HTML 的数据(16 篇辩论 + 汇总 + 手记 + 学理综述)
- 两个文件都在同目录即可,`index.html` 通过 `<script src="data.js">` 加载

## 制作过程

- Claude Code (Opus 4.7) 作为协调者,扮演阿伦特
- 3 个 Hermes agent (glm-5.2) 分别加载 jurgen-habermas / jeremy-bentham / michael-schudson Skill
- 四轮讨论通过 herdr(terminal workspace manager)跨 pane 协调
- 国内学理检索通过 Hermes 的 web_search 工具
