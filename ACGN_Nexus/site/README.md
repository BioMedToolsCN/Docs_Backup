# 期刊网页快照 / Website snapshots

本目录保存 ACGN Nexus 官网（`journal.scihorizon.org`，OJS 3.5）在 **2026-10-17** 的静态 HTML 快照。抓取脚本见 [`../scripts/fetch_site.py`](../scripts/fetch_site.py)，逐页的源 URL、字节数与 SHA-256 见 [`manifest.csv`](manifest.csv)。

## 为什么保留网页

PDF 能证明"文章写了什么"，网页能证明"文章确实在这一期发表过、属于哪个栏目、当时如何被引用"。停刊期刊的页面通常在站点关闭后彻底消失，而 DOI 只保存元数据，不保存版面。这 19 个页面不到 1 MB，却是最便宜的一份证据。

## 收录页面

| 文件 | 内容 |
| --- | --- |
| `2026-10-17_home.html` | 首页：当期目录、期刊简介、栏目设置、APC 说明 |
| `2026-10-17_issue-1-1.html` | Vol. 1, No. 1 目录页 |
| `2026-10-17_issue-archive.html` | 过刊列表 |
| `2026-10-17_announcement-cessation.html` | 停刊公告（2026-10-17） |
| `2026-10-17_about.html` | 关于本刊：范围、审稿方式、语言政策 |
| `2026-10-17_about-masthead.html` | 编辑名单 |
| `2026-10-17_about-submissions.html` | 投稿说明与栏目 |
| `2026-10-17_about-contact.html` | 联系方式 |
| `2026-10-17_article-e0001.html` … `e0011.html` | 11 篇文章页：题录、作者、摘要、引用格式、DOI |

`/issue/current` 会 302 跳转到 `/issue/view/4`，内容与 `issue-1-1.html` 相同，故未重复保存。

## 说明与限制

- **不含 CSS、图片与 JavaScript**。页面只保留 HTML 文本与结构，直接打开是朴素的无样式版本；标题、作者、摘要、DOI 等文字信息完整可读。这是有意的取舍：样式文件随时可重建，题录文字不行。
- **链接是绝对地址**，指向原站。站点下线后这些链接会失效，属于预期行为；需要时可对照 Internet Archive 的存档。
- 页面由 OJS 服务端渲染，抓取时只接受以 `</html>` 结尾的完整响应；服务器会保持连接不关闭，抓取器因此设置了超时并在收到完整正文后落盘。
- 快照是"某一天的样子"，不是实时镜像。站方在 2027 年 5 月前如修改页面，本目录不会跟随更新。

## 校验

```bash
shasum -a 256 -c SHA256SUMS          # 仓库根目录
```

`manifest.csv` 同时记录了每页的源地址与哈希，可用于逐页核对。
