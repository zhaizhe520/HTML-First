# HTML-First
破站

网页项目结构解析：轻小说展示页
1. HTML 核心内容拆解
1.1 文档元数据与资源引用
<!DOCTYPE html>: 声明文档类型为 HTML5。

<meta charset="utf-8">: 指定字符编码，确保中文字符正常显示。

<link>: 引入外部样式表 novel.css。

1.2 页面结构化组件
导航头部 (<header>):

包含一个 id="header" 的容器。

使用 <ul> 和 <li> 构建了包含“動畫區”、“輕小說”等跳转链接的导航菜单。

内容主体 (<section class="lightnovel">):

采用嵌套 section 结构（novel1, novel2）来组织不同的小说行。

每个小说单元由一个唯一的 id（如 angal, yuemei）标识，便于精准定位样式。

1.3 数据展示与交互元素
图像组件 (<img>):

采用双图片机制（如 imgA1 为常驻封面，imgA2 为隐藏的放大层）。

信息表格 (<table>):

使用 <th>（表头）标识属性名（名称、Tag、角色）。

使用 <td>（单元格）展示具体内容。

文本段落 (<p>): 在表格内详细描述小说简介。

2. CSS 样式核心要点
2.1 全局与背景设计
通配符重置: 使用 * { margin: 0; padding: 0; } 消除浏览器默认边距。

固定背景: 通过 background-attachment: fixed; 配合 background-size: cover; 实现背景图随窗口拉伸且不随滚动条滚动的视觉效果。

2.2 布局技术
Flexbox 布局:

.novel1, .novel2 设置为 display: flex;，使两部小说横向并排。

小说容器（如 #angal）使用 margin: auto; 实现水平居中对齐。

定位 (Positioning):

Fixed (固定定位): #header 固定在顶部，不受滚动影响。

Absolute (绝对定位): 导航列表 ul 相对于 header 精确定位。

2.3 交互视觉效果
悬停反馈 (Hover): 给表格单元格 td 设置了 transition: 1s;。当鼠标悬浮时，背景颜色会平滑切换。

弹出层实现:

默认情况下，大图（如 #imgA2）为 display: none;。

当 JS 激活 .active 类时，使用 position: fixed; 配合 transform: translate(-50%, -50%); 使图片在屏幕正中心弹出。

3. JavaScript 交互逻辑简述
代码通过简单的 DOM 操作 实现了图片的放大查看功能：

监听点击: 为小图片绑定 onclick 事件。

状态切换: 点击时通过 classList.add("active") 显示隐藏的大图。

关闭预览: 再次点击大图时，通过 classList.remove("active") 将其重新隐藏。
