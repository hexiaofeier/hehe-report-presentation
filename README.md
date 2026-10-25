# 盒盒商业报告呈现 Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-244C66.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-compatible-82B29B.svg)](https://agentskills.io/)
[![Release](https://img.shields.io/badge/release-2026.10.25-C98B5B.svg)](release-manifest.json)
[![Install](https://img.shields.io/badge/install-standalone-295E78.svg)](#使用与依赖)

将已确认的专业报告制作成可阅读、可演示的HTML、PDF或可编辑PPTX。保留完整论述，按比较、结构、过程与数据关系安排页面。

**让图形承担解释，让正文保留分析。** 适用于商业计划书、行业与企业研究、用户研究和其他专业报告，先根据内容选择图式，再安排完整文字与版式。

## 五种交付选择

| 形式 | 适用场景 |
|---|---|
| 带侧栏目录的下拉HTML | 长报告连续阅读，直接接收Markdown，窄屏折叠目录 |
| 16:9翻页HTML | 横向咨询汇报 |
| 9:16翻页HTML | 手机竖版阅读 |
| A4翻页HTML | 正式阅读与打印 |
| 可编辑PPTX | 由本Skill分页HTML生成原生文字、表格、图表和形状 |

各HTML形态可导出对应PDF。保留蓝白封面与章节样式，并可按报告内容选择其他阅读风格。

## 图形优先，具体怎样落地

| 报告要说明的内容 | 可以采用的视觉表达 |
|---|---|
| 资金、信息或服务在主体间流动 | 带主体和方向的关系图、流程图 |
| 不同条件对应不同选择 | 条件分支、决策树 |
| 多方分工和阶段推进 | 泳道图、时间轴、甘特图 |
| 收入、成本与利润的形成 | 瀑布图、构成图 |
| 企业或业务的数量差异 | 柱状图、条形图 |
| 需要精确查阅的数据与条款 | 表格，并附必要分析 |

每个正文页记录具体关系和图形方案。生成器检查方案是否有对应图形对象，帮助避免将普通文字卡片或表格当成关系图。制作后仍需看实际页面，检查阅读顺序、换行、信息密度和整稿节奏。

完整解释留在可见正文。空间不足时先调整图文比例和布局，再按完整主题拆页；保留数据口径、条件、来源及原稿中的分析。

## 制作流程

```text
已确认正文／逐页脚本
        ↓
确认读者与交付形态 → 选择图式 → 制作代表页
        ↓
生成完整报告 → 对照原稿 → 检查实际页面 → 导出并核验PDF／PPTX
```

随包提供 [基础对象示例](skills/hehe-report-presentation/assets/example.json)、[商业版式示例](skills/hehe-report-presentation/assets/business_layouts.json) 和 [封面与章节样式](skills/hehe-report-presentation/assets/cover_chapter.json)，方便用真实报告内容制作样张。

## 使用与依赖

将 `skills/hehe-report-presentation/` 放入客户端的 Skills 目录，新开会话。示例：

> 使用 $hehe-report-presentation 将这份Markdown报告制作成带侧栏目录的下拉HTML，保留全部正文和表格。

制作横向汇报版：

```text
使用 $hehe-report-presentation，将这份报告制作成16:9翻页HTML和PDF。
保留完整分析和来源，先识别适合图形表达的流程、结构、分支和数量关系。
使用蓝白封面与章节页，检查实际页面，并交付可修改的页面源文件。
```

制作可编辑演示文件：

```text
使用 $hehe-report-presentation，将这份已确认的逐页报告制作成可编辑PPTX。
文字、表格、图表和流程形状使用原生对象；保留完整分析。
完成实际打开、编辑、保存重开和渲染核验。
```

**安装方法：** 下载本仓库，将整个 `skills/hehe-report-presentation/` 文件夹放入客户端的 Skills 目录，保留 `scripts/`、`assets/`、`references/` 和调用配置。例如 Codex 的 `~/.codex/skills/` 或 Claude Code 的 `~/.claude/skills/`。新开会话后调用 `hehe-report-presentation`。已通过组合包安装同名Skill的用户直接更新原目录。

可独立使用，不要求安装写作或行业研究Skill。JSON转HTML只需Python标准库；Markdown直转、PDF和PPT按 [依赖清单](skills/hehe-report-presentation/依赖清单.md) 准备相应环境，不必一次安装所有依赖。

| 本次要做什么 | 需要的环境 |
|---|---|
| JSON页面源转HTML | Python标准库 |
| Markdown直转下拉HTML | Python、markdown、beautifulsoup4 |
| 导出并检查PDF | Playwright、PyMuPDF、Chrome或Chromium |
| 生成可编辑PPTX | Playwright、python-pptx、Chrome或Chromium |
| 检查PPT的实际编辑与排版 | PowerPoint或LibreOffice，以及报告字体 |

依赖安装在实际制作报告的电脑或服务器上。接收成品的人只需要浏览器、PDF阅读器或演示软件。无需显卡或本地大模型，浏览器与办公软件可复用已有安装。

PPTX转换针对本Skill生成的分页HTML；文字、表格、图表和支持的流程形状可编辑，独立插图的编辑范围需在交付时说明。HTML阅读版同时保留。

文字需专业编辑时，可搭配 [hehe-report-writing](https://github.com/hexiaofeier/hehe-report-writing)。收到合格Markdown可直接制作下拉HTML，收到合格逐页脚本可直接制作分页报告。

## 2026-10-25 更新

首次独立公开发布，加入图形优先的页面方案与生成检查；资金流、流程、分支、结构和数值关系优先采用对应图式。保留完整分析、封面、章节和多形态交付能力。

生成 HTML 时自动检查本地 PDF 是否存在，避免出现失效下载入口；PDF 导出核验成功后自动补回链接。包外 Skill 引用纳入发布校验。

## 2026-10-24 更新

正式运行资源去除_CO文件后缀；补齐依赖不足时的替代路径，保留现有组件、封面、章节、三种分页画布、下拉目录及可编辑PPT能力。

## 校验与来源

运行 `python scripts/validate_release.py` 检查包内文件与链接。独立版和行业研究组合版从同一维护源导出，同名Skill只需安装一份。本项目采用MIT许可证。
