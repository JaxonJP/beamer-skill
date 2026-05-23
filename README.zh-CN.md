# Beamer Skill 中文说明

[English](README.md) | [简体中文](README.zh-CN.md)

## 仓库定位

本仓库是一个面向学术 **Beamer LaTeX** 幻灯片工作流的 AI skill 仓库，用于辅助完成学术幻灯片的创建、编译、审阅、校对、排版检查与质量验证。

核心流程为：**create → compile → review → polish → verify**。

## 推荐使用方式

本二改版本优先推荐在 **OpenCode** 中使用。模型方面，建议搭配 GPT 等先进多模态模型；如果使用国产模型，目前更推荐 **Kimi**，在论文阅读、中文讲解材料组织和长上下文处理上通常更适合这一类工作流。

推荐做法是先将本仓库 `git clone` 到本地，然后把 `beamer/` 目录配置为 OpenCode 的全局 skill。这一步也可以直接交给 AI 编码助手完成。

典型的全局 skill 目标路径为：

```text
~/.config/opencode/skills/beamer
```

## 示例提示词

```text
使用 beamer-skill 对 "C:\Users\server02\Desktop\2502.15260v2.pdf" 做一个论文讲解性质的 beamer，要求把架构和技术细节讲清楚（幻灯片页数不限制，适当加入论文关键图片，讲解要图文并茂，不过要注意图片比例不要有过界的情况，文字不要过于精简，不是面向汇报的那种幻灯片），观看对象是一个业内有一点知识储备的研究生。
```

## 维护者与来源

- 维护者：**USTC_Jaxon-JP(最闲的下饭菜)**
- 上游项目：[`Noi1r/beamer-skill`](https://github.com/Noi1r/beamer-skill)
- 本仓库基于上游项目进行二次开发，并在工作流设计、PDF/Python 工具选型、多环境适配、编译分支与平台集成等方面做了实质性扩展。

## 这个仓库解决什么问题

相比只给出一份 Beamer 模板或几条零散提示，这个仓库更关注一整套可执行的幻灯片工作流，包括：

- 从论文或讲义材料出发，组织 Beamer 讲解结构
- 约束内容密度、图文比例、TikZ 质量和引用完整性
- 为不同 AI 编码助手提供可直接使用的规则文件
- 在本地编译和在线平台编译之间切换，保持一致的质量检查流程

## 本仓库相对上游的主要增量

- 增加了 **本地编译优先 / 在线平台编译兜底** 的双分支工作流
- 明确支持 **USTC LaTeX** 平台的 Git 同步方式，包括平台常见项目地址格式：
  `git clone https://git@latex.ustc.edu.cn/git/****************`
- 推送到在线平台后，会提醒用户确认启用 **XeLaTeX**，有些界面中也可能显示为 `xelatex` 或 `xlatex`
- 对 PDF/Python 工具链的选型做了调整，更强调实际可用的论文解析、图像抽取与 PDF 可视化检查路径
- 保留并整理了多环境封装，而不是只服务单一助手或单一平台

## 支持的平台与封装形式

本仓库当前包含以下几类规则文件：

- `beamer/SKILL.md`：适用于使用 `SKILL.md` 机制的环境
- `beamer/AGENTS.md`：适用于 Codex CLI 风格环境
- `.github/copilot-instructions.md`：适用于 GitHub Copilot
- `.clinerules/beamer.md`：适用于 Cline
- `.cursor/rules/beamer.mdc`：适用于 Cursor

## 说明

- 本文件属于 **仓库级中文自述**，用于介绍仓库定位、来源和改动方向
- 它不会直接改变 skill 的实际执行逻辑
- 真正影响行为的仍然是各平台使用的规则文件，例如：
  - `beamer/SKILL.md`
  - `beamer/AGENTS.md`
  - `.github/copilot-instructions.md`
  - `.clinerules/beamer.md`
  - `.cursor/rules/beamer.mdc`
