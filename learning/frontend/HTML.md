# HTML

HTML: `HyperText Markup Language` 超文本标记语言，用于定义网页内容。

> 由 w3c（_互联网标准组织_） 定义 HTML 语言标准。

## 元素 `element`

元素 = 起始标记（_begin tag_） + 元素内容 + 结束标记（_end tag_） + 元素属性

> _空元素_：没有结束标记

- 元素不能相互嵌套
- 元素关系：父元素、子元素、兄弟元素、祖先元素、后代元素

> `<br>` & `<br />`：
> `<br>` 是 HTML4 写法，`<br />` 是 XHTML 为兼容 HTML 的写法,也是 XML 写法。（_XHTML：HTML 严格遵守 XML 语法规范的一个版本_）
> HTML5 因为兼容 XHTML，所以两种写法都可以使用。
> 早期发布的 HTML 规范当中，`<br>` 与 `<img>` 等元素是不用封闭自身的，但是这种元素造成了 HTML 规范的不严谨，于是在之后发布的 XHTML 语言中，参考了更为严谨的 XML 规范，在这些不用自身封闭的元素后加 `/` 来表示自行封闭。

### 属性的分类

1. 全局属性：所有元素都可用的属性
2. 局部属性：某些元素特有的属性

> _布尔属性_：不写或取值为属性名，HTML5 中可以省略属性值

## 标准文档结构

```html
<!DOCTYPE html>
```

文档声明：告诉浏览器使用 HTML5 标准（_最新版本_）解析文档。

> 不写文档声明将导致浏览器进入怪异渲染模式。

### 根元素

```html
<html lang="en"></html>
```

根元素：一个页面最多存在一个根元素，且该元素 `<html>` 是所有其他元素的父元素或祖先元素。

> HTML5 规范中， `<html>` 作为根元素不具有强制性。

`lang` 属性：**全局属性**，用于定义页面的自然语言。

> 简体中文最新表示值：`lang="zh-CN"` ==> `lang="cmn-hans"`

### `<head>` 元素

文档头，_文档头内部的内容不会显示在页面内_。

#### `<meta>` 元素

文档的元数据：附加信息。

```html
<head>
  <!-- charset 指定网页内容编码，局部属性 -->
  <meta charset="UTF-8" />
  <!-- viewport 设置网页视口 -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <!-- 解决IE兼容问题 -->
  <meta http-equiv="X-UA-Compatible" content="ie=edge" />
  <!-- 网页关键词，用于SEO优化 -->
  <meta name="keywords" content="WEB 前端, HTML, CSS, JavaScript" />
  <!-- 网页作者 -->
  <meta name="author" content="Shaw" />
  <!-- 网页描述，出现在搜索引擎搜索结果中 -->
  <meta name="description" content="This is a web page." />
  <!-- 网页标题 -->
  <title>Document</title>
</head>
```

#### `<link>` 元素

用于链接外部资源：CSS、JavaScript、图标等。

```html
<head>
  <link rel="stylesheet" type="text/css" href="style.css" />
  <!-- 网站图标，也可之间取名为 favicon.ico 放在网站根目录下 -->
  <link rel="icon" type="image/x-icon" href="favicon.ico" />
</head>
```

- `rel` 属性：_relationship_，描述当前文档与被链接的资源之间的关系
  - `stylesheet` 样式表
- `type` 属性：描述被链接资源的 MIME 类型，_可省略_
- `href` 属性：被链接资源的路径

### `<body>` 元素

文档体，所有要参与显示的内容都放在这里。

## 语义化

1. 每一个HTML元素都有具体的含义
2. 所有元素与展示效果无关(_展示由CSS决定，元素只决定含义_)，**应该根据内容的含义选择要使用的元素**。

==（为了语义化）HTML5 标准已经弃用 `行级元素` 和 `块级元素` 的定义==

> 所有纯样式元素在 HTML4 中被废弃，有些又被赋予语义并在 HTML5 中被恢复。

### 语义化的必要性

1. 为了搜索引擎优化（SEO），使搜索引擎更容易理解网页内容，从而提高网站排名
2. 为了让浏览器理解网页，增强浏览器使用体验

## 元素的包含关系

> HTML5 以前：块级元素独占一行，行级元素不换行；块级元素可以包含行级元素，行级元素不能包含块级元素，`<a>` 元素除外。

HTML5 中：为了语义化，元素的包含关系由元素的 _`内容类别`_ 决定。

### 常见包含关系

- 容器元素可以包含任何元素
- `<a>` 元素几乎可以包含任何元素
- 某些元素有固定的子元素
- **标题元素和段落元素不能相互包含**

## 常用元素

> [HTML5 元素周期表](https://www.xuanfengge.com/funny/html5/element/)

### 文本元素

- `<h1>` ~ `<h6>` 标题元素
- `<p>` 段落元素
- `<span>` _无语义元素_，仅用于设置样式
- `<pre>` 预格式化文本元素，内部的内容会按照源代码格式显示，不会出现[空白折叠](#空白折叠)
  - 通常用于显示代码，与 `<code>` 元素 (_代码区域_) 一起使用
  - 功能的本质上是由css决定
  - 理论上是无语义元素，但规范没有提及
- `<i>` 特殊文本，_默认样式为倾斜字体_
  - 实际使用时通常用来制作图标
- `<em>` 用于强调的文本，_默认样式为倾斜字体_
  - 可以嵌套，嵌套层次越深，则强调的程度越深
- `<strong>` 重要的，不能忽略的文本，_默认样式为加粗字体_
- `<b>` 用于强调的文本，_默认样式为加粗字体_
- `<del>` 被删除的文字内容，_默认样式为删除线_
- `<s>` 不再相关，不准确的文字内容，_默认样式为删除线_
- `<ins>` 被添加的文字内容，_默认样式为下划线_
- `<u>` 某种形式的非标准文本注释，_默认样式为下划线_

:::tip
VSCode EMMET: 输入 `LOREM` 快速生成文本内容
:::

### 超链接

`<a>` 元素

```html
<a href="https://www.baidu.com" target="_blank">百度</a>
```

#### `href` 属性 _hyper reference_

- 跳转地址: `href="https://www.baidu.com"`
- 跳转锚点: `href="#id"` 跳转到页面中 id 为 `id` 的元素位置；`href="#"` 空链接，返回顶部
- 功能链接: 点击后触发功能
  - JS代码: `href="javascript:alert('Hello World')"`
  - 发送邮件: `href="mailto:123456789@qq.com"`，_要求用户安装邮箱客户端软件_
  - 拨打电话: `href="tel:12345678910"`，_要求用户安装拨号软件_

#### `target` 属性

表示跳转窗口位置

- `target="_self"` 默认值，在当前页面窗口打开
- `target="_blank"` 在新窗口打开

:::tip
为了SEO优化，当使用图片作为超链接时，通常也会写上文本来描述链接的功能：
`<a href="https://www.baidu.com" target="_blank"><img src="baidu.jpg" alt="百度" />百度</a>`
:::

### 图片元素

`<img>` 元素，_空元素_

```html
<img src="image.jpg" alt="图片" />
```

- `src` 属性 _source_: 图片资源地址
- `alt` 属性 _alternate_: 图片的替代文本，当图片无法显示时显示。

#### `<img>` 和其他元素联动

```html
<!-- 与a元素联动 -->
<a><img src="image.jpg" /></a>
<!-- 与map元素联动，用于图片部分区域点击 -->
<img usemap="#imageMap" src="image.jpg" />
<map name="imageMap">
  <!-- shape形状、coords坐标、href链接 -->
  <area href="#" shape="circle" coords="0,0,100,100" target="_blank" />
</map>
<!-- 与figure元素联动，用于描述图片 -->
<figure>
  <img src="image.jpg" alt="图片" />
  <!-- figure元素的标题 -->
  <figcaption>图片标题</figcaption>
  <p>图片描述</p>
</figure>
```

### 多媒体元素

#### 视频元素

`<video>` 元素，_空元素_

```html
<video src="video.mp4" controls autoplay muted loop poster="poster.jpg" width="640" height="480"></video>
```

- `src` 属性: 视频资源地址
- `controls` 属性: _布尔属性_，显示控件。取值只能为 `controls`
- `autoplay` 属性: _布尔属性_，自动播放，_某些浏览器中不支持非静音自动播放_
- `muted` 属性: _布尔属性_，静音播放
- `loop` 属性: _布尔属性_，循环播放
- `poster` 属性: 视频封面地址
- `width`: 视频宽度
- `height` 属性: 视频高度

#### 音频元素

`<audio>` 元素，_空元素_

```html
<audio src="audio.mp3" controls autoplay loop></audio>
```

属性同 `<video>`

#### 兼容性

1. HTML5 新元素，旧版本浏览器不支持
   - `<video>` 元素中嵌入提示或 flash 播放器
2. 不同的浏览器支持的音视频格式可能不同，网页中通常使用 MP4、WebM
   - 使用子元素 `<source>` 的 `src` 属性用于指定不同格式的视频资源

```html
<video>
  <source src="video.mp4" type="video/mp4" />
  <source src="video.webm" type="video/webm" />
  <p>您的浏览器不支持该视频播放。</p>
</video>
```

### 列表元素

#### `<ol>` 有序列表 _ordered list_

```html
<ol type="a" reversed>
  <li></li>
  <li></li>
  <li></li>
</ol>
```

- 当表示一个有顺序的列表时使用
- `type` 属性: 列表项的编号类型
  - `1` 数字编号，默认值
  - `A` 大写字母编号
  - `a` 小写字母编号
  - `I` 大写罗马数字编号
  - `i` 小写罗马数字编号
- `reversed` 属性：_布尔属性_，列表项倒序

> `type` 属性在 HTML4 中弃用，HTML5 又重新引入，除非列表中序号很重要，如法律条文等，否则建议使用 CSS 中的 `list-style-type` 属性实现。

#### `<ul>` 无序列表 _unordered list_

```html
<ul>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

- 当表示一个无顺序的列表时使用，**和显示序号的效果无关**
- 常用于制作菜单、新闻列表等

:::tip
`<ol>`, `<ul>` 的**子元素只能是 `<li>` 元素（_list item_）**，表示列表项。
:::

#### 定义列表

- 常用于术语定义
- `<dl>` 元素，_definition list_
- `<dt>` 元素：定义标题，_definition title_
- `<dd>` 元素：定义描述，_definition description_

```html
<dl>
  <dt>HTML</dt>
  <dd>超文本标记语言</dd>
  <dt>CSS</dt>
  <dd>层叠样式表</dd>
</dl>
```

### 容器元素

代表一块区域，该元素内部用于放置其他元素

- `<div>` 元素：_无语义元素_
- `<header>` 元素：通常用于表示页头或文章的头部。
- `<footer>` 元素：通常用于表示页脚或文章的尾部。
- `<article>` 元素：通常用于表示文章的正文或整篇文章。
- `<section>` 元素：通常用于表示文章中的一个区域，如文章中的一节。
- `<aside>` 元素：通常用于表示附加信息，如页面的侧边栏。

### 嵌入元素

#### `<iframe>` 元素

_可替换元素_，通常用于在一个页面中嵌入另一个页面，CSS 不能控制其中的样式。

```html
<iframe src="https://www.baidu.com"></iframe>
```

- `allowfullscreen` 属性：设置是否允许全屏显示
- `width` 和 `height` 属性：设置宽高

#### `<iframe>` 应用场景

1. 嵌入无法使用链接播放的视频（如bilibili）
2. 与 `<a>` 元素配合

```html
<!-- 使用a元素切换iframe嵌入网页 -->
<a href="https://www.taobao.com" target="iframe1"></a>
<iframe name="iframe1" src="https://www.baidu.com"></iframe>
```

::: tip
Each embedded browsing context has its own document and allows URL navigations. The navigations of each embedded browsing context are linearized into the session history of the topmost browsing context.
每个嵌入式浏览上下文的导航都会被线性嵌入到顶级浏览上下文的会话历史记录中。
:::

#### `<embed>` 元素和 `<object>` 元素

- `<object>` 元素，_可替换元素_，用于引入外部资源
  - `data` 属性：嵌入资源的路径
  - `type` 属性：嵌入文件的类型(_MIME类型_)
  - `<param name="" value="" />` 子元素：用于传递参数，`name` 属性表示参数名，`value` 属性表示参数值
- `<embed>` 元素，_可替换元素_，用于引入外部资源
  - `src` 属性：嵌入资源的路径
  - `type` 属性：嵌入文件的类型(_MIME类型_)

由于两者的兼容性不同，采用兼容性写法：

```html
<object data="movie.swf" type="application/x-shockwave-flash">
  <embed src="movie.swf" type="application/x-shockwave-flash" />
</object>
```

> MIME：(_Multipurpose Internet Mail Extensions_) 多用途互联网邮件类型，如图片 `image/jpeg`

### 表单元素

一系列元素，主要用于收集用户数据，大部分为**可替换元素**

#### `<input>` 元素

输入框

```html
<input type="text" placeholder="请输入" />
```

- `type` 属性：输入框类型
  - `text` 普通文本输入框
  - `password` 密码输入框
  - `num` 数字输入框
  - `checkbox` 多选框，需要设置 `name` 属性，以确定分组
  - `radio` 单选框，需要设置 `name` 属性，以确定分组
  - `date` 日期选择框 _有兼容性问题_
  - `file` 选择文件
  - `search` 搜索框 _一般用在移动端，有兼容性问题_
  - `range` 滑块，可同时设置 `min`, `max` 属性，_有兼容性问题_
- `value` 属性：输入框的值
- `placeholder` 属性：提示文本，_文本框没有内容时显示_
- `min` 属性：最小值
- `max` 属性：最大值
- `step` 属性：步长
- `checked` 属性：_布尔属性_，表示默认选中

> `<input>` 作为按钮：
>
> - `type="reset"` 重置按钮
> - `type="submit"` 提交按钮
> - `type="button"` 一般按钮
> - 使用 `value` 属性修改按钮中显示的文字

#### `<select>` 元素

下拉选择列表

```html
<select>
  <option value="1">选项1</option>
  <option value="2">选项2</option>
</select>
```

- `multiple` 属性：表示可以选择多个选项
- `<option>` 子元素：选项
  - `value` 属性：选项值
  - `selected` 属性：_布尔属性_，表示默认选中
- `<optgroup>` 子元素：选项分组（_不能选中_）
  - `label` 属性：分组标题

#### `<textarea>` 元素

多行文本域

```html
<textarea cols="10" rows="10">内容</textarea>
```

- `cols` 属性：文字列数
- `rows` 属性：文字行数
- 无空白折叠

#### `<button>` 元素

按钮

```html
<button type="submit">提交</button>
```

- `type` 属性：按钮类型
  - `submit` _默认值_，提交按钮
  - `reset` 重置按钮
  - `button` 普通按钮

> 按钮内容可以是文本或其他元素
>
> `<input>`作为图片按钮：`<input type="image" src="image.jpg" />`

#### 表单元素状态属性

- `readonly` 属性：_布尔属性_，表示是否只读，不会改变表单显示样式
- `disabled` 属性：_布尔属性_，表示是否禁用，会改变表单显示样式

### 配合表单元素的元素

#### `<label>` 元素

普通元素，通常配合单选或多选框使用，表示表单元素的标签文本

```html
<!-- 显式关联：for 属性和 input 元素的 id 属性关联 -->
<label for="male">男</label>
<input type="radio" name="gender" id="male" value="男" checked="checked" />
<label for="female">女</label>
<input type="radio" name="gender" id="female" value="女" />
<!-- 隐式关联 -->
<label><input type="radio" name="gender" value="男" />男</label>
<label><input type="radio" name="gender" value="女" />女</label>
```

#### `<datalist>` 元素

数据列表，不会显示到页面，通常用于与普通文本框配合使用，提供输入提示，_有兼容性问题_

```html
<!-- 通过 id 关联 input 元素的 list 属性 -->
<input type="text" list="fruit" />
<datalist id="fruit">
  <option value="apple">苹果</option>
  <option value="orange">香蕉</option>
</datalist>
```

#### `<form>` 元素

通常会将整个表单的元素放置到 `<form>` 元素中，用于点击提交按钮时，将 `<form>` 元素中的表单数据提交到服务器。

> 若要提交必须设置表单元素 `name` 属性，不设置会被丢弃；提交的值为 `value` 属性

- `action` 属性：提交路径，默认为当前页面地址
- `method` 属性：提交方式

#### `<fieldset>` 元素

表单域，用于将表单元素分组，_有兼容性问题_

```html
<form>
  <fieldset>
    <!-- 分组标题 -->
    <legend>用户信息</legend>
    <label for="name">姓名：</label>
    <input type="text" id="name" name="name" />
  </fieldset>
</form>
```

### 表格元素

在 CSS 技术出现之前，网页通常使用表格布局。表格渲染速度过慢，因此现在不适用于网页布局。

<!-- @include: @demo/HTML-1-Table.md#demo-->

### 其他元素

- `<br>` 用于在文本中换行，_空元素，无语义元素_，无法控制样式
- `<hr>` 用作分割线，_空元素，无语义元素_
- `<abbr title="HyperText Markup Language">HTML</abbr>` 缩写元素
- `<time datetime="2021-01-01">21年元旦</time>` 提供给浏览器或搜索引擎识别的时间元素
- `<b>` 以前是无语义元素，表示加粗字体；HTML5 中表示强调语气，_默认样式为加粗字体_
- `<q>` 一小段引用文本，_默认样式用双引号包裹_
- `<blockquote>` 大段引用文本
  - `cite` 属性：引用的来源

## HTML实体 `HTML Entity`

又叫实体字符，用于在页面中显示一些特殊符号。

### 空白折叠

在 HTML 源码中，连续多个空白符（空格、制表符、换行符）会被自动合并为一个空白符。

### HTML实体表示方式

1. `&`<字母>`;`
2. `&#`<十进制数字>`;`
3. `&#x`<十六进制数字>`;`

### 常用实体

- `&nbsp;` 空格
- `&lt;` 小于
- `&gt;` 大于
- `&copy;` 版权符©
- `&amp;` &符

## _HTML中_ 路径的写法

### 站内资源和站外资源

- 站内资源：当前站点的资源
- 站外资源：当前站点以外的资源

### 相对路径和绝对路径

站内资源建议使用相对路径，站外资源只能使用绝对路径。

**绝对路径**：`协议名`://`主机名`:`端口号`/`路径`；`scheme`://`host`:`port`/`path`

> _url地址_: 绝对路径的一种书写方式

- 协议名（_当目标和当前页的协议相同时可以省略_）
  - `http`
  - `https`
  - `ftp`
  - `file`
- 主机名
  - 域名
  - IP地址
- 端口号（_可省略_）
  - `http` 默认端口号：80
  - `https` 默认端口号：443

**相对路径**：以 `./` 或 `../` 开头的路径（_`./` 可以省略_）。
`.` 表示当前目录，`..` 表示上级目录。

## 数据链接 _data url_

将目标文件的数据直接书写到路径位置

书写方式：`data:<MIME类型>;<数据>`

### 数据链接的意义

1. 减少浏览器请求次数；减少了请求中浪费的时间
2. 有利于动态生成数据
3. 增加了资源的体积；导致传输内容增加，从而增加单个资源的传输时间
4. 不利于浏览器缓存
   - 浏览器通常会缓存图片，CSS, JS 等
5. 会增加原资源的体积（base64 编码后增加 1/3）

### 应用场景

- 当单个图片体积较小，且该图片因为各种原因不适合制作雪碧图
- 图片由其他代码动态生成，且图片较小

> `base64`: 一种编码方式，通常用于将一些二进制数据转变为用字符串可书写的形式。
