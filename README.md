# HTML-First
破站

# 轻小说展示页 项目结构解析

## 一、HTML 核心内容拆解

### 1.1 文档元数据与资源引用
- `<!DOCTYPE html>`：声明文档类型为标准 HTML5
- `<meta charset="utf-8">`：设置字符编码，保证中文字符正常显示
- `<link rel="stylesheet" href="novel.css">`：引入外部样式文件，统一样式管理

### 1.2 页面结构化组件
- 导航头部 `<header id="header">`
  - 固定在页面顶部，不随滚动条移动
  - 使用 `<ul>` + `<li>` 构建导航菜单，包含「动画区」「轻小说」等跳转链接
- 内容主体 `<section class="lightnovel">`
  - 嵌套 `<section class="novel1">`、`<section class="novel2">` 分组展示小说
  - 每部小说使用唯一 ID（`angal`、`yuemei`）标识，方便样式与脚本控制

### 1.3 数据展示与交互元素
- 图像组件 `<img>`
  - 双图片机制：小封面图（常驻显示）+ 放大预览图（默认隐藏）
- 信息表格 `<table>`
  - `<th>`：定义属性表头（名称、Tag、角色）
  - `<td>`：展示小说具体信息
  - `<p>`：在单元格内编写小说简介文本
- 基础交互：绑定点击事件，实现图片放大查看

---

## 二、CSS 样式核心要点

### 2.1 全局与背景设计
- 全局样式重置：`* { margin: 0; padding: 0; }` 消除浏览器默认边距
- 固定背景：`background-attachment: fixed` + `background-size: cover`，背景全屏且不随滚动移动

### 2.2 核心布局技术
- Flexbox 布局
  - `.novel1` / `.novel2` 设置 `display: flex`，实现小说横向并排展示
  - 小说容器用 `margin: auto` 水平居中
- 定位体系
  - `position: fixed`：导航栏固定顶部
  - `position: absolute`：导航列表精确定位
  - `position: fixed` + `transform: translate(-50%, -50%)`：实现图片居中弹出

### 2.3 视觉交互效果
- 悬停动画：`td` 设置 `transition: 1s`，鼠标悬浮平滑切换背景色
- 图片预览：
  - 预览图默认 `display: none` 隐藏
  - 添加 `.active` 类时显示，实现全屏放大查看效果

---

## 三、JavaScript 交互逻辑

- 核心功能：**轻量级图片放大预览**
- 实现方式：原生 DOM 操作，无外部依赖
- 执行流程：
  1. 为小封面图绑定点击事件
  2. 点击后给预览图添加 `.active` 类，显示全屏大图
  3. 点击大图时移除 `.active` 类，关闭预览
