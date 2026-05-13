---
name: product-prototype
description: 产品原型构建专家。根据用户需求生成 PC 端或 H5 端产品原型 demo（静态 HTML 单文件，可直接在浏览器打开）。当用户提到"PC端原型"、"H5原型"、"移动端原型"、"产品demo"、"添加菜单"、"新建页面"、"PC端页面"、"H5页面"等关键词时触发此 skill。
---

# 产品原型构建专家

根据需求**直接生成静态 HTML 原型**，单文件可双击在浏览器打开，无需安装依赖、无需构建。

---

## 产物

| 终端 | 输出路径 | 示例 |
|------|----------|------|
| PC 端 | `SmartStar_PM/workspace/04_prototype/PC-{功能名称}.html` | `PC-用户管理.html` |
| H5 端 | `SmartStar_PM/workspace/04_prototype/H5-{功能名称}.html` | `H5-首页.html` |

---

## 设计规范

| 规范 | 文件 |
|------|------|
| 产品原型设计规范 | [references/design-spec.md](./references/design-spec.md)（核心） |
| Mock 数据参考 | [references/mock-data.md](./references/mock-data.md) |

---

## 工作流

1. **确认需求**：终端类型、页面数量、核心功能、交互需求
2. **生成 HTML**：直接输出单文件 HTML，包含完整 CSS/JS/交互
3. **交付产物**：输出到 `SmartStar_PM/workspace/04_prototype/`

---

## 主题色

#FF6B00（橙白主色调），PC 端与 H5 端保持一致

---

## 验收标准

1. 双击 HTML 文件可直接在浏览器打开
2. Tab 切换、弹窗、表单提交等交互正常
3. PC 端在 1200px+ 显示正常，H5 端在 430px 模拟手机显示正常
4. 主色调 #FF6B00，样式统一
5. 控制台无 JS 报错