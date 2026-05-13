# HTML-First
破站

# 轻小说文件
1. HTML5 结构化标签
这些标签用于定义页面的不同区块，使代码语义化（让机器和人都能看懂网页的结构）。

<header>: 定义页面的头部区域，包含标题和导航栏。

<section>: 定义文档中的节。代码中嵌套了多层 section（如 lightnovel, novel1, novel2）来对小说卡片进行布局和分组。

<div>: 通用的容器标签。用于包裹具体的小说内容（如 id="angal", id="yuemei"），方便通过 CSS 进行样式控制。

2. 文本与链接
<ul> 和 <li>: 无序列表。用于构建头部的导航菜单。

<a>: 超链接。

内部链接: 指向本地其他页面（如 ../輕小說/novel.html）。

外部链接: 指向 Steam 和 Bilibili 个人主页。

<p>: 段落标签。用于展示每一部小说的详细简介内容。

3. 多媒体标签 (图像)
<img>: 图像嵌入。

页面为每部小说使用了两张图（例如 imgA1 和 imgA2）。

属性: 使用了 src 指向图片路径，width 和 height 设置初始尺寸，alt 提供替代文本。

4. 数据展示 (表格)
页面使用了 <table> 结构来整齐地排列小说的元数据（名称、标签、角色）：

<tr>: 定义表格行。

<th>: 定义表头单元格（通常加粗显示），用于显示“名称”、“tag”等类目。

<td>: 定义标准单元格，用于填充具体的小说信息。

5. 交互与脚本链接
<script>: 在 HTML 底部直接嵌入了 JavaScript 代码。

通过 document.getElementById 获取元素。

通过 onclick 事件监听点击动作。

通过 classList.add/remove 动态修改类名，配合 CSS 实现图片的“放大/遮罩”效果。
6. CSS 核心内容 (补充)
在配套的 novel.css 中，使用了以下关键技术：

背景处理: background-attachment: fixed; 实现了背景图固定不随滚动条移动的效果。

Flexbox 布局: display: flex; 用于让小说封面和表格左右并排显示。

固定定位: position: fixed; 用于让头部导航栏始终留在屏幕顶端，以及让点击后的放大图片居中显示。

伪类选择器: a:hover 和 td:hover 增加了鼠标悬停时的变色和过渡动画（transition）。

层级控制: z-index 确保导航栏和放大后的图片能够浮在其他内容之上。
