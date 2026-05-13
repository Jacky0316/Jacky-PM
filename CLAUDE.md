# CLAUDE.md

本文件为 Claude Code 工作目录指南。

## 语言约束

本项目默认使用简体中文，新增/更新的 skill、规则、记忆等文件应该使用简体中文（可允许部分必须要英文字母的表述，如 API、URL、ID 等）。

## 项目概述

这是一个产品经理的 Claude Code 工作空间，用于：
- 需求分析（requirements-analysis）
- 撰写 PRD（prd-writer）
- 构建 PC 端供应链管理后台 Demo（pc-demo）

**工作流程**：需求分析 → PRD 撰写 → PC 端 Demo 开发

## 目录结构

```
pm_agent/
├── CLAUDE.md              # 本文件
├── prd/                   # PRD 文档目录
├── pc/                    # PC 端供应链管理后台 Demo
│   ├── CLAUDE.md          # PC 项目指南
│   └── src/               # 项目源码
└── .claude/
    └── skills/            # Claude Code 技能目录
        ├── prd-writer/           # PRD 撰写技能
        ├── requirements-analysis/ # 需求分析技能
        └── pc-demo/              # PC 端 Demo 构建技能
```

## 技能说明

### requirements-analysis（需求分析）
当用户提到"需求分析"、"分析需求"、"撰写需求分析"、"需求调研"时使用。在 PRD 撰写前进行需求调研、分析和确认。

### prd-writer（PRD 撰写）
当用户提到"写PRD"、"撰写需求"、"产品需求"、"需求背景"、"功能设计"、"撰写产品需求文档"时使用。根据标准模板输出，包含需求背景、目标、流程图、功能清单、系统改造等章节。

### pc-demo（PC 端 Demo）
当用户提到"PC后台"、"供应链后台"、"后台页面"、"新增页面"、"添加菜单"、"PC端开发"、"后台列表"、"后台详情"、"管理后台"、"新建页面"、"开发页面"、"页面模板"等关键词时使用。即使用户只是简单提到要做一个后台页面或管理界面，也应该触发此 skill。



## 工作流程

```
需求分析 → PRD 撰写 → 原型开发
requirements-analysis → prd-writer → product-prototype/pc-demo
```

## 目录结构

```
Jacky-PM-Agent/           # 工作空间根目录
├── CLAUDE.md             # 本文件
├── SmartStar_PM/         # 星马特项目目录
│   ├── content/          # 产品内容（功能模块、业务场景等）
│   ├── workspace/
│   │   ├── 01_discussions/    # 需求沟通记录
│   │   ├── 02_spec/           # 需求分析文档/功能方案
│   │   ├── 03_prd/            # PRD 文档
│   │   ├── 04_prototype/      # 原型文件（HTML）
│   │   ├── 05_draft/          # 设计规范、业务流程图等草稿
│   │   └── 06_old_template/    # 历史模板
├── .claude/
│   └── skills/           # Claude Code 技能目录
│       ├── requirements-analysis/  # 需求分析技能
│       ├── prd-writer/          # PRD 撰写技能
│       ├── product-prototype/    # 产品原型构建技能
│       ├── brainstorming/        # 头脑风暴技能
│       ├── frontend-design/      # 前端设计技能
│       ├── ui-ux-pro-max/       # UI/UX 设计技能
│       └── skill-creator/       # 技能创建工具
```

## 技能触发规则

| 技能 | 触发关键词 | 产出物 |
|------|-----------|--------|
| requirements-analysis | 需求分析、分析需求、撰写需求分析、需求调研 | 需求沟通记录 → 需求分析文档 |
| prd-writer | 写PRD、撰写需求、产品需求、功能设计、撰写产品需求文档 | PRD 文档 |
| product-prototype | PC端原型、H5原型、移动端原型、产品demo、添加菜单、新建页面、PC端页面、H5页面 | HTML 原型文件 |
| frontend-design | 前端设计、UI 设计、界面设计 | 设计方案 |
| brainstorming | 头脑风暴、方案讨论、方案评审 | 讨论记录 |
| ui-ux-pro-max | UI检查、UX优化、设计评审 | 设计建议 |

## 核心约束

1. **语言**：本项目默认使用简体中文，skill、规则、记忆等文件使用简体中文
2. **需求流程**：必须先完成需求分析（requirements-analysis），才能撰写 PRD
3. **PRD 模板**：完整产品用 `prd-template-full.md`，功能迭代用 `prd-template-iteration.md`
4. **Mermaid 强制**：业务流程必须使用 Mermaid 语法绘制
5. **原型规范**：product-prototype 输出静态 HTML 单文件，可直接在浏览器打开