# 产品设计规范

本规范用于静态 HTML 原型生成，单文件可双击直接在浏览器打开。
融合了设计原则（ProductDesign.md）与实现参数（design-spec.md）。

---

## 一、设计原则

### 1.1 核心设计原则

#### 列表驱动设计
- **页面结构**：以列表为主体，所有操作围绕列表展开
- **层级划分**：页面级操作（新增、导入、批量）在列表上方，行级操作（编辑、删除、详情）在列表内部
- **操作闭环**：CRUD操作完成后自动更新列表状态
- **状态驱动**：基于数据状态控制操作按钮显示

#### 用户体验优化
- **流程直观**：符合用户习惯，减少跳转和学习成本
- **反馈及时**：操作后给予明确反馈
- **简化任务**：通过引导和默认值简化复杂操作
- **信息分层**：重要信息优先显示，次要信息可隐藏

#### 系统健壮性
- **功能完整**：提供完整的CRUD功能和批量操作
- **异常处理**：处理空状态、错误状态、权限不足等情况
- **设计一致**：界面风格和交互模式保持统一
- **响应式布局**：适配不同设备

### 1.2 流程设计原则

#### 流程完整性
- **主流程**：覆盖用户的主要操作路径
- **异常流程**：处理错误、权限不足、数据为空等情况
- **状态管理**：清晰的状态定义和流转规则
- **边界处理**：首次使用、极限情况的处理方案

#### 数据流设计
- **单一数据源**：每个数据项有唯一的权威来源
- **流向清晰**：明确输入源头、处理节点、输出目标
- **状态同步**：页面状态与后端数据保持一致
- **错误追溯**：提供清晰的错误反馈机制

---

## 二、界面设计规范

### 2.1 页面布局规范

- **导航结构**：顶部导航栏 + 面包屑 + 页面标题
- **垂直tab页布局**（如有）：垂直标签栏在页面导航栏下方最左侧，主体内容在右侧区域
- **水平tab页布局**（如有）：水平标签栏在导航栏下方，主体内容上方
- **主体内容**：查询筛选区 + 数据列表 + 分页组件
- **操作层级**：页面级操作在列表上方，行级操作在列表内部

### 2.2 弹窗设计规范

#### 基本弹窗结构
- **标准结构**：弹窗标题 + 主体内容 + 操作按钮
- **表单设计**：必填标识，实时校验，清晰的错误提示

#### 多步骤弹窗规范

**步骤展示要求**：
- 每个步骤都必须绘制独立的 ASCII 示意图
- 步骤间的导航关系必须清晰标识
- 进度指示器必须准确反映当前步骤和总步骤数

**多步骤弹窗结构**：
```
+-------------------------------------------------------------+
| 步骤标题 (步骤X/总步骤数)                                [×] |
+-------------------------------------------------------------+
| [●基本信息] → [●列映射] → [○项目背景] → [○预览确认]         |
+-------------------------------------------------------------+
| 当前步骤的具体内容                                           |
| [表单字段、选项、说明文字等]                                 |
+-------------------------------------------------------------+
|                    [上一步]     [下一步]        [取消]       |
+-------------------------------------------------------------+
```

**步骤导航按钮规范**：
- 第一步：只显示"下一步"和"取消"按钮
- 中间步骤：显示"上一步"、"下一步"和"取消"按钮
- 最后一步：显示"上一步"、"完成"和"取消"按钮
- 进度条：使用●表示已完成步骤，●表示当前步骤，○表示未完成步骤

#### 弹窗中的子tab页规范

**子tab页结构**：
```
+-------------------------------------------------------------+
| 弹窗标题                                                [×] |
+-------------------------------------------------------------+
| [**基本信息**] [高级配置] [权限设置] [操作日志]              |
+=============================================================+
| 当前激活tab页的具体内容                                      |
| [表单字段、列表、配置选项等]                                 |
+=============================================================+
|                       [取消]          [确认]                |
+-------------------------------------------------------------+
```

---

## 三、视觉参数

### 3.1 主题色

| 用途 | 颜色 | 说明 |
|------|------|------|
| 主题色 | #FF6B00 | 按钮、选中状态、主强调 |
| 成功色 | #07c160 | 正向数据、分红收益 |
| 警告色 | #FF6B00 | 业绩、待处理 |
| 信息色 | #1989fa | 信息提示、链接 |
| 错误色 | #f5222d | 错误提示、失败状态 |
| 背景色 | #f5f5f5（PC）/ #f7f8fa（H5） | 页面背景 |
| 卡片背景 | #fff | 卡片、容器背景 |
| 边框色 | #eee | 分割线、边框 |
| 文字主色 | #323233 | 主标题、重要文字 |
| 文字辅助色 | #969799 | 辅助说明 |
| 文字占位色 | #bfbfbf | 输入框占位符 |

### 3.2 字体规范

| 层级 | 字号 | 字重 | 行高 | 用途 |
|------|------|------|------|------|
| 页面标题 | 18px | 600 | 1.4 | 页面大标题 |
| 卡片标题 | 16px | 500 | 1.4 | 卡片标题、区段标题 |
| 正文 | 14px | 400 | 1.5 | 正文内容 |
| 辅助文字 | 12px | 400 | 1.5 | 辅助说明、时间戳 |
| 按钮文字 | 14px | 500 | 1 | 按钮内文字 |
| 标签文字 | 12px | 400 | 1.3 | 标签、徽章 |

**字体family**：`font-family: -apple-system, BlinkMacSystemFont, "PingFang SC", "Helvetica Neue", sans-serif;`

### 3.3 间距系统

基于 8px 网格系统，所有间距为 8 的倍数。

| 名称 | 数值 | 用途 |
|------|------|------|
| xs | 4px | 紧凑元素间的最小间距 |
| sm | 8px | 表单项内部、标签与输入框 |
| md | 16px | 卡片内边距、元素间距 |
| lg | 24px | 区块间距、容器内边距 |
| xl | 32px | 大区块间距 |
| xxl | 48px | 页面级区块间距 |

**常用组合**：
- 卡片内边距：16px
- 区块间距：24px
- 页面容器边距：24px（PC）、16px（H5）

### 3.4 阴影规范

| 层级 | CSS 值 | 用途 |
|------|--------|------|
| 轻微 | `0 1px 2px rgba(0,0,0,0.06)` | 卡片悬浮、列表项 |
| 轻度 | `0 2px 8px rgba(0,0,0,0.08)` | 卡片、弹窗 |
| 中度 | `0 4px 16px rgba(0,0,0,0.12)` | 弹窗、浮层 |
| 重度 | `0 8px 32px rgba(0,0,0,0.16)` | 模态框 |

### 3.5 动效规范

**时长**：
| 类型 | 时长 | 用途 |
|------|------|------|
| 瞬间 | 100ms | 颜色变化、hover 效果 |
| 快速 | 200ms | 按钮点击反馈、开关切换 |
| 正常 | 300ms | 弹窗出现、滑入/滑出 |
| 缓慢 | 400ms | 页面转场、大型模态框 |

**缓动函数**：
- 标准：`cubic-bezier(0.4, 0, 0.2, 1)`
- 进入：`cubic-bezier(0, 0, 0.2, 1)`
- 退出：`cubic-bezier(0.4, 0, 1, 1)`
- 弹性：`cubic-bezier(0.68, -0.55, 0.27, 1.55)`（用于按钮点击反馈）

---

## 四、组件规范

### 4.1 按钮

**主要按钮**（主色调填充）：
```css
.btn-primary {
  background: #FF6B00;
  color: #fff;
  border: 1px solid #FF6B00;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
}
```

**次要按钮**（边框透明）：
```css
.btn-default {
  background: #fff;
  color: #323233;
  border: 1px solid #d9d9d9;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
}
```

**文字按钮**（无边框）：
```css
.btn-link {
  background: transparent;
  color: #FF6B00;
  border: none;
  padding: 4px 8px;
  cursor: pointer;
}
```

### 4.2 表格

```css
.table {
  width: 100%;
  border-collapse: collapse;
}
.table th,
.table td {
  padding: 12px 8px;
  border: 1px solid #eee;
  text-align: left;
}
.table th {
  background: #fafafa;
  font-weight: 500;
}
.table tr:hover {
  background: #fafafa;
}
```

### 4.3 表单输入

```css
.input {
  width: 100%;
  padding: 8px 12px;
  border: 1px solid #d9d9d9;
  border-radius: 4px;
  font-size: 14px;
}
.input:focus {
  border-color: #FF6B00;
  outline: none;
}
```

### 4.4 卡片

```css
.card {
  background: #fff;
  border-radius: 8px;
  padding: 16px;
  margin-bottom: 16px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.08);
}
```

### 4.5 弹窗

```css
.modal-overlay {
  position: fixed;
  top: 0; left: 0; right: 0; bottom: 0;
  background: rgba(0,0,0,0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}
.modal {
  background: #fff;
  border-radius: 8px;
  min-width: 400px;
  max-width: 600px;
  max-height: 80vh;
  overflow: auto;
}
```

### 4.6 顶部 Tab

```css
.tab-header {
  display: flex;
  border-bottom: 1px solid #eee;
}
.tab-item {
  padding: 12px 16px;
  cursor: pointer;
  color: #666;
}
.tab-item.active {
  color: #FF6B00;
  border-bottom: 2px solid #FF6B00;
}
```

### 4.7 底部 Tab（H5 专用）

```css
.tabbar {
  position: fixed;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  max-width: 430px;
  display: flex;
  background: #fff;
  border-top: 1px solid #eee;
  z-index: 100;
}
.tab-item {
  flex: 1;
  text-align: center;
  padding: 8px 0;
  cursor: pointer;
}
.tab-item.active {
  color: #FF6B00;
}
```

---

## 五、状态规范

### 5.1 按钮状态

```css
/* 默认态 */
.btn { opacity: 1; cursor: pointer; }

/* 悬浮态 */
.btn:hover { opacity: 0.85; }

/* 点击态 */
.btn:active { transform: scale(0.98); opacity: 0.9; }

/* 禁用态 */
.btn:disabled {
  opacity: 0.45;
  cursor: not-allowed;
  pointer-events: none;
}

/* 加载态 */
.btn-loading {
  position: relative;
  color: transparent;
}
.btn-loading::after {
  content: "";
  position: absolute;
  width: 14px; height: 14px;
  border: 2px solid #fff;
  border-top-color: transparent;
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}
@keyframes spin { to { transform: rotate(360deg); } }
```

### 5.2 表单状态

```css
/* 默认 */
.input { border-color: #d9d9d9; background: #fff; }

/* 聚焦 */
.input:focus { border-color: #FF6B00; box-shadow: 0 0 0 2px rgba(255,107,0,0.1); }

/* 错误 */
.input-error { border-color: #f5222d; }
.input-error:focus { box-shadow: 0 0 0 2px rgba(245,34,45,0.1); }

/* 禁用 */
.input:disabled {
  background: #f5f5f5;
  cursor: not-allowed;
  color: #969799;
}

/* 只读 */
.input:read-only {
  background: #fafafa;
  color: #969799;
}
```

### 5.3 加载状态

**骨架屏**（Skeleton）：
```css
.skeleton {
  background: linear-gradient(90deg, #f2f2f2 25%, #e6e6e6 50%, #f2f2f2 75%);
  background-size: 400% 100%;
  animation: skeleton-loading 1.5s ease-in-out infinite;
}
@keyframes skeleton-loading {
  0% { background-position: 100% 50%; }
  100% { background-position: 0 50%; }
}
```

---

## 六、空状态规范

### 无数据空状态

```html
<div class="empty-state">
  <div class="empty-icon">📭</div>
  <div class="empty-title">暂无数据</div>
  <div class="empty-desc">当前没有相关记录，请稍后再试</div>
  <button class="btn btn-primary" onclick="refresh()">刷新试试</button>
</div>
```

```css
.empty-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 48px 24px;
  text-align: center;
}
.empty-icon { font-size: 48px; margin-bottom: 16px; }
.empty-title { font-size: 16px; color: #323233; font-weight: 500; margin-bottom: 8px; }
.empty-desc { font-size: 14px; color: #969799; margin-bottom: 24px; }
```

### 网络错误状态

```html
<div class="error-state">
  <div class="error-icon">⚠️</div>
  <div class="error-title">网络不给力</div>
  <div class="error-desc">请检查网络连接后重试</div>
  <button class="btn btn-primary" onclick="retry()">重新加载</button>
</div>
```

---

## 七、轻提示规范

### Toast（操作反馈）

```css
.toast {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: rgba(0,0,0,0.75);
  color: #fff;
  padding: 12px 24px;
  border-radius: 8px;
  font-size: 14px;
  z-index: 9999;
  animation: toast-in 0.3s ease;
}
@keyframes toast-in {
  from { opacity: 0; transform: translate(-50%, -50%) scale(0.9); }
  to { opacity: 1; transform: translate(-50%, -50%) scale(1); }
}
```

**自动消失时间**：2000ms

### 操作成功/失败反馈

```javascript
function showToast(message, type = 'info') {
  const toast = document.createElement('div');
  toast.className = `toast toast-${type}`;
  toast.textContent = message;
  document.body.appendChild(toast);
  setTimeout(() => toast.remove(), 2000);
}
```

---

## 八、导航规范

### 返回导航

```css
.nav-back {
  display: flex;
  align-items: center;
  padding: 12px 16px;
  font-size: 16px;
  color: #323233;
  cursor: pointer;
}
.nav-back::before {
  content: "←";
  margin-right: 8px;
  font-size: 18px;
}
.nav-back:active { opacity: 0.7; }
```

### 面包屑（PC）

```css
.breadcrumb {
  display: flex;
  align-items: center;
  font-size: 14px;
  color: #969799;
}
.breadcrumb-item:not(:last-child)::after {
  content: "/";
  margin: 0 8px;
  color: #d9d9d9;
}
.breadcrumb-item:last-child { color: #323233; }
```

---

## 九、下拉刷新与上拉加载

### 下拉刷新（H5）

```javascript
function initPullToRefresh() {
  const content = document.querySelector('.content');
  let startY = 0, currentY = 0;

  content.addEventListener('touchstart', (e) => {
    startY = e.touches[0].clientY;
  });

  content.addEventListener('touchmove', (e) => {
    currentY = e.touches[0].clientY;
    if (currentY - startY > 60 && content.scrollTop === 0) {
      // 显示下拉刷新指示器
      document.querySelector('.refresh-indicator').style.display = 'block';
    }
  });

  content.addEventListener('touchend', () => {
    // 触发刷新逻辑
    setTimeout(() => {
      document.querySelector('.refresh-indicator').style.display = 'none';
    }, 1000);
  });
}
```

### 上拉加载

```javascript
function initInfiniteScroll() {
  const content = document.querySelector('.content');
  content.addEventListener('scroll', () => {
    if (content.scrollTop + content.clientHeight >= content.scrollHeight - 50) {
      loadMoreData();
    }
  });
}
```

---

## 十、Accessibility 无障碍规范

**颜色对比度**：
- 文字与背景对比度 >= 4.5:1（正文）
- 重要文字对比度 >= 3:1（大字号 >= 18px 或粗体 >= 14px）

**可点击区域**：
- 最小点击区域 44px × 44px（H5）
- 按钮之间保持足够间距避免误触

**焦点状态**：
```css
*:focus-visible {
  outline: 2px solid #FF6B00;
  outline-offset: 2px;
}
```

**语义化**：
- 使用 `<button>` 作为可点击元素
- 使用 `<input type="text">` 而非 `<div contenteditable">`
- 图片添加 `alt` 属性

---

## 十一、布局规范

### PC 端管理后台

```
┌────────────────────────────────────────────────────────┐
│  ┌──────────┐  ┌────────────────────────────────────┐ │
│  │          │  │  顶部标签栏                          │ │
│  │  左侧菜单 │  ├────────────────────────────────────┤ │
│  │  (200px) │  │                                    │ │
│  │          │  │  页面内容区                         │ │
│  │          │  │  (白色背景)                        │ │
│  │          │  │                                    │ │
│  └──────────┘  └────────────────────────────────────┘ │
└────────────────────────────────────────────────────────┘
```

**样式规范**：
- 整体宽度：固定 1200px，居中
- 左侧菜单：固定宽度 200px，浅色背景
- 标签栏高度：48px
- 内容区内边距：24px
- 卡片圆角：8px

### H5 端移动端

```
┌────────────────────────┐
│     顶部导航栏  44px     │
├────────────────────────┤
│                        │
│     页面内容区          │
│   (可滚动区域)          │
│                        │
├────────────────────────┤
│     底部 Tab 栏  50px   │
│     安全区域    34px     │
└────────────────────────┘
总高度：667px / 896px
```

**样式规范**：
- 容器最大宽度：430px，居中（模拟手机屏幕）
- 整机高度：667px（iPhone SE/8）、896px（iPhone 11/12/13）、926px（Pro Max）
- 内容区：`overflow-y: auto`，超出整机高度时页面整体可滚动
- 顶部导航：固定高度 44px，白色背景，文字居中（不滚动）
- 底部 Tab：固定高度 50px + 安全区域 34px（刘海屏），不滚动
- 触摸友好：按钮高度 >= 44px

---

## 十二、页面类型

### 列表页

```
┌─────────────────────────────────────────┐
│  页面标题                                │
├─────────────────────────────────────────┤
│  筛选区：输入框 [查询] [重置]            │
├─────────────────────────────────────────┤
│  操作区：[新增] [批量导出]               │
├─────────────────────────────────────────┤
│  表格区                                 │
│  ┌─────┬────────┬────────┬────────┐      │
│  │勾选 │订单号  │客户名  │金额    │...   │
│  ├─────┼────────┼────────┼────────┤      │
│  │  □ │001     │张三    │¥100    │编辑  │
│  └─────┴────────┴────────┴────────┘      │
├─────────────────────────────────────────┤
│                          分页组件       │
└─────────────────────────────────────────┘
```

**H5 列表页**（卡片式）：
```
┌────────────────────────┐
│ [🔍 搜索框]            │
├────────────────────────┤
│ ┌──────────────────┐  │
│ │ 卡片 1           │  │
│ └──────────────────┘  │
│ ┌──────────────────┐  │
│ │ 卡片 2           │  │
│ └──────────────────┘  │
└────────────────────────┘
```

### 详情页

```
┌─────────────────────────────────────────┐
│  ← 返回    订单详情            [编辑]   │
├─────────────────────────────────────────┤
│  ┌─────────────────────────────────┐   │
│  │ 基本信息卡片                     │   │
│  │ 订单号：001  金额：¥100         │   │
│  └─────────────────────────────────┘   │
├─────────────────────────────────────────┤
│  [基本信息] [操作记录] [关联单据]        │
├─────────────────────────────────────────┤
│  Tab 内容区                             │
│  ...                                   │
└─────────────────────────────────────────┘
```

### 表单页

```
┌─────────────────────────────────────────┐
│  ← 返回    新增订单                      │
├─────────────────────────────────────────┤
│  ┌─────────────────────────────────┐   │
│  │ 表单区域                         │   │
│  │                                 │   │
│  │  客户名：[输入框________]        │   │
│  │  金额：  [输入框________]        │   │
│  │                                 │   │
│  └─────────────────────────────────┘   │
├─────────────────────────────────────────┤
│  [取消]                    [保存]       │
└─────────────────────────────────────────┘
```

---

## 十三、交互实现

### Tab 切换

```javascript
function switchTab(tabId) {
  // 隐藏所有 tab 内容
  document.querySelectorAll('.tab-content').forEach(el => {
    el.style.display = 'none';
  });
  // 显示选中的 tab 内容
  document.getElementById(tabId).style.display = 'block';
  // 更新 tab 样式
  document.querySelectorAll('.tab-item').forEach(el => {
    el.classList.remove('active');
  });
  event.target.classList.add('active');
}
```

### 弹窗打开/关闭

```javascript
function openModal(modalId) {
  document.getElementById(modalId).style.display = 'flex';
}

function closeModal(modalId) {
  document.getElementById(modalId).style.display = 'none';
}

// 点击遮罩关闭
document.querySelectorAll('.modal-overlay').forEach(overlay => {
  overlay.addEventListener('click', function(e) {
    if (e.target === this) {
      this.style.display = 'none';
    }
  });
});
```

### 表单提交

```javascript
document.querySelectorAll('form').forEach(form => {
  form.addEventListener('submit', function(e) {
    e.preventDefault();
    const formData = new FormData(this);
    // 处理提交
    alert('提交成功');
  });
});
```

### H5 底部弹窗（从底部弹出）

```javascript
function openBottomPopup(popupId) {
  document.getElementById(popupId).style.display = 'flex';
}
```

```css
.bottom-popup {
  position: fixed;
  top: 0; left: 0; right: 0; bottom: 0;
  background: rgba(0,0,0,0.5);
  display: none;
  align-items: flex-end;
  justify-content: center;
  z-index: 999;
}
.bottom-popup-content {
  background: #fff;
  width: 100%;
  max-width: 430px;
  max-height: 70vh;
  border-radius: 16px 16px 0 0;
  overflow: auto;
}
```

---

## 十四、Mock 数据格式

```javascript
const mockData = {
  // 列表数据
  list: [
    { id: 1, orderNo: 'DD202401001', customer: '张三', amount: 1000, status: '待审核' },
    { id: 2, orderNo: 'DD202401002', customer: '李四', amount: 2000, status: '已完成' },
  ],

  // 详情数据
  detail: {
    orderNo: 'DD202401001',
    customer: '张三',
    phone: '138****8888',
    amount: 1000,
    createTime: '2024-01-15 10:30',
  },

  // 分页数据
  pagination: {
    page: 1,
    pageSize: 20,
    total: 100,
  }
};
```

---

## 十五、输出位置与文件命名

**输出目录**：`SmartStar_PM/workspace/04_prototype/`

**文件命名**：`{终端}-{功能名称}.html`
- PC 端示例：`PC-用户管理.html`、`PC-订单列表.html`
- H5 端示例：`H5-用户管理.html`、`H5-首页.html`

```
SmartStar_PM/workspace/04_prototype/
├── PC-用户管理.html
├── PC-订单列表.html
├── H5-首页.html
└── H5-我的.html
```

---

## 十六、全局检查

### 设计原则检查结果

| 检查项目           | 检查结果 | 说明                                                         |
| ------------------ | -------- | ------------------------------------------------------------ |
| 列表为中心设计     | ✅ 通过  | 用户列表作为页面核心主体，所有操作围绕列表展开               |
| 页面级操作层级     | ✅ 通过  | 新增、批量操作等页面级功能置于列表上方，层级清晰             |
| 行级操作层级       | ✅ 通过  | 编辑、删除、状态变更等行级操作置于列表内部                   |
| 弹窗围绕业务对象   | ✅ 通过  | 所有弹窗都围绕用户这个核心业务对象设计                       |
| 操作完成后列表更新 | ✅ 通过  | 所有操作完成后都明确了列表状态更新机制                       |
| 交互流程闭环检查   | ✅ 通过  | 所有交互流程均以列表为起点和终点，形成完整闭环               |
| 数据流设计规范检查 | ✅ 通过  | 页面有独立的数据流说明，包含输入、处理、输出                 |
| 用户体验流程       | ✅ 通过  | 操作流程符合管理员心智模型，减少跳转和认知负荷               |
| 设计系统一致性     | ✅ 通过  | 遵循通用布局规范，使用统一的组件和交互模式                   |

---

## 十七、验收标准

1. **双击可打开**：双击 HTML 文件在 Chrome/Edge 等主流浏览器直接打开
2. **交互正常**：Tab 切换、弹窗打开/关闭、表单提交等功能正常
3. **布局正确**：PC 端在 1200px+ 宽度显示正常，H5 端在 430px 宽度模拟手机显示正常
4. **样式一致**：主色调 #FF6B00，间距、圆角等视觉元素统一
5. **无报错**：控制台无 JS 错误