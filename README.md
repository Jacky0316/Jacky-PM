# Jacky-PM-Agent

产品经理的 Claude Code AI 工作空间，用于需求分析、PRD 撰写和产品原型开发。

## 项目简介

这是一个基于 Claude Code 的产品经理工作空间，集成了多种 AI 技能，支持从需求分析到产品原型开发的完整流程。

## 核心功能

| 功能 | 说明 |
|------|------|
| 需求分析 | 需求调研、分析和确认，生成需求沟通记录 |
| PRD 撰写 | 根据标准模板输出专业产品需求文档 |
| 产品原型 | 构建 PC 端/H5 端静态 HTML 原型 Demo |
| 头脑风暴 | 产品方案讨论和评审 |

## 目录结构

```
Jacky-PM-Agent/
├── CLAUDE.md                    # Claude Code 工作目录指南
├── SmartStar_PM/                 # 星马特 S2B2C 平台项目
│   ├── content/                  # 产品内容（功能模块、业务场景）
│   └── workspace/
│       ├── 01_discussions/       # 需求沟通记录
│       ├── 02_spec/              # 功能方案文档
│       ├── 03_prd/               # PRD 文档
│       ├── 04_prototype/         # 原型文件（HTML）
│       └── 05_draft/             # 设计规范、业务流程图
└── .claude/
    └── skills/                   # Claude Code 技能
        ├── requirements-analysis/   # 需求分析技能
        ├── prd-writer/               # PRD 撰写技能
        ├── product-prototype/       # 产品原型技能
        ├── brainstorming/           # 头脑风暴技能
        ├── frontend-design/        # 前端设计技能
        └── ui-ux-pro-max/          # UI/UX 设计技能
```

## 工作流程

```
需求分析 → PRD 撰写 → 原型开发
```

## 技能触发规则

| 技能 | 触发关键词 |
|------|-----------|
| 需求分析 | "需求分析"、"分析需求"、"撰写需求分析" |
| PRD 撰写 | "写PRD"、"撰写需求"、"产品需求" |
| 产品原型 | "PC端原型"、"H5原型"、"产品demo" |

## 技术说明

- **AI 工具**：Claude Code (Anthropic)
- **原型格式**：静态 HTML 单文件，可直接在浏览器打开
- **文档规范**：使用 Mermaid 语法绘制业务流程图
- **语言约束**：默认使用简体中文
