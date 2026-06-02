# tiantian0347.github.io

Tian Tian 的个人主页 —— Hugo 工程版。论文自动管理：在 `content/publication/` 下放 markdown，首页自动按年份倒序列出。

## 怎么改内容

绝大多数信息集中在一个文件：[data/site.yaml](data/site.yaml)
- 头像 / 头衔 / 单位 / 社交图标 / 邮箱（`profile`）
- 个人简介、Highlights、研究兴趣、教育经历（`about`）
- 研究方向（`research`）
- News 时间线（`news`）
- 授课（`teaching`）
- 联系方式（`contact`）

论文单独管理，每篇一个文件放在 [content/publication/](content/publication/)：

```bash
hugo new publication/2026-my-paper.md   # 用 archetypes/publication.md 模板生成
```

front matter 字段：`title` / `year`（排序用）/ `authors` / `venue` / `url`（标题链接，可空）/ `buttons`（PDF、arXiv 等按钮）。首页 Publications 版块会自动收集、按 `year` 倒序展示。

## 放资源文件
- 头像：`static/img/portrait.jpg`（建议正方形）
- 研究配图：`static/img/research1.jpg`、`research2.jpg`
- CV：`static/files/cv.pdf`（导航栏 CV 按钮指向它）

## 本地预览
```bash
hugo server -D
# 打开 http://localhost:1314
```

## 构建
```bash
hugo --minify   # 产物输出到 public/
```

## 部署到 GitHub Pages
仓库已含 [.github/workflows/hugo.yml](.github/workflows/hugo.yml)。推到 GitHub 后，在
Settings → Pages → Source 选择 **GitHub Actions** 即可，每次 push 到 `main` 自动构建部署，
访问 https://tiantian0347.github.io 。

## 目录结构
```
hugo.toml                 站点配置（导航顺序、语言、publication 构建规则）
data/site.yaml            个人信息单一数据源
content/publication/      论文，每篇一个 .md
layouts/
  _default/baseof.html    页面骨架（head / 引脚本）
  index.html              首页：按 sections 顺序拼装各版块
  partials/
    navbar.html           导航栏（由 sections + CV 驱动）
    footer.html
    sections/*.html       about / research / news / publications / teaching / contact
static/css/style.css      全部样式（海军蓝学术风）
static/img, static/files  头像、配图、CV
archetypes/publication.md 新论文模板
```

旧的纯静态单页版本备份在 `backup-static/index.html`。
