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


1. HTML5 核心内容
文档结构与元数据：

使用 <!DOCTYPE html> 声明文档类型，并通过 <meta charset="utf-8"> 确保中文字符正常显示。

通过 <link> 标签将外部 CSS 样式表（如 novel.css）关联到 HTML 文档。

语义化与结构化标签：

<header>：用于定义页面的头部区域，通常包含导航栏。

<section>：用于对页面内容进行分节（如 lightnovel, novel1, novel2），使文档结构更清晰。

<div>：作为通用的容器，通过 id（如 angal, yuemei）标识特定的小说单元，便于 CSS 精准控制。

文本与多媒体嵌入：

图像 (<img>)：使用了双图片机制（如 imgA1 为常驻显示，imgA2 为隐藏的放大预览层）。

超链接 (<a>)：包含指向本地页面的相对路径（如 ../Gal/gal.html）以及指向外部平台的绝对路径（如 Steam、Bilibili）。

列表 (<ul>, <li>)：用于构建导航菜单。

数据展示 (表格)：

使用 <table> 结构整齐地排列小说属性。

<tr> 定义行，<th> 定义属性名称（表头），<td> 填充具体描述。

2. CSS3 核心内容
背景与布局控制：

背景固定 (background-attachment: fixed)：在 body 中设置，使背景图在页面滚动时保持固定，增强视觉层次感。

Flexbox 布局 (display: flex)：用于实现内容的弹性排列。例如，将小说封面和数据表格左右并排，或者让两部小说在同一行显示。

定位技术 (position)：

fixed：使导航栏 (#header) 始终固定在窗口顶部，以及让放大的图片预览层在屏幕正中央弹出。

absolute：在 header 内部对标题和列表进行精确定位。

视觉美化与交互：

悬停效果 (:hover)：当鼠标移至表格单元格或链接时，通过修改颜色提供即时反馈。

过渡动画 (transition)：为颜色改变或透明度切换设置平滑的时间曲线（如 transition: 1s;）。

层级管理 (z-index)：确保导航栏和弹出大图能够覆盖在普通内容之上。

响应式基础：使用 rem 单位（如 margin-top: 3.125rem）替代部分固定像素，使布局更具弹性。

3. JavaScript 交互内容
DOM 元素获取：使用 document.getElementById 和 document.querySelectorAll 选取页面中的特定元素。

事件监听与处理：

点击事件 (onclick)：点击小图时激活大图显示，再次点击大图时将其关闭。

滚动监听 (window.addEventListener('scroll', ... ))：在其他关联文件中，通过监听滚动条位置来实现“触顶激活”或“触底变色”的效果。

类名动态操作 (classList)：

通过 add("active") 和 remove("active") 动态切换样式类，配合 CSS 实现弹出层、幻灯片切换或状态高亮。

定时器功能：在幻灯片组件（777.html）中使用 setInterval 和 clearInterval 控制图片的自动循环播放。

总结
该项目是一个综合性的静态网页。HTML 负责内容和骨架（文本、图片、表格），CSS 负责视觉呈现和布局控制（背景固定、弹性盒、层级管理），而 JavaScript 赋予了页面交互能力（点击放大、滚动检测、自动切换）。

---------------





