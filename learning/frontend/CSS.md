# CSS

CSS: `Cascading Style Sheets` 层叠样式表，用于定义网页的样式。

CSS规则 = 选择器 + 声明块

> 声明块： `{` `}` 中, 包含多个声明（_属性_），每个声明（_属性_）表达了某一方面的样式。

## CSS 代码位置

- 内部样式：写在 `<style>` 元素中，通常放在 `<head>` 元素中，保证浏览器最先加载样式。
  - 样式很少时，放在内部样式中用来性能优化；浏览器只读取一个文件，提高网页的加载速度。
- 内联样式：直接写在元素的 `style` 属性中。
- 外部样式表：将样式表放在单独的 CSS 文件中，通过 `<link>` 元素引入，通常放在 `<head>` 元素中。
  - 可以解决多页面样式复用的问题。
  - 有利于浏览器缓存，提高网站的加载速度。
  - 有利于代码分离，便于维护。

## 选择器

用于选中元素（_样式应用的范围_）

### 简单选择器

- 元素选择器：选中对应名称的所有元素 `div`
- ID选择器：选中对应id值的元素 `#id`
- 类选择器：选中对应class值的元素 `.class`
- 通配符选择器：`*` 选中所有元素
- 属性选择器：选中具有特定属性的元素
  - `[attr]` 选中具有以 `attr` 命名属性的元素
  - `[attr=value]` 选中具有 `attr` 命名的属性且属性值等于 `value` 的元素
  - `[attr~=value]` 选中带有以 `attr` 命名的属性的元素，且属性值是一个以空格分隔的列表，其中至少有一个值为 `value`
  - `[attr*=value]` 选中带有以 `attr` 命名的属性的元素，且属性值包含 `value` 字符
- 伪类选择器：选中某些元素的某种状态
  - `:link` 超链接未访问过的状态
  - `:visited` 超链接已访问过的状态
  - `:hover` 鼠标悬停
  - `:active` 激活状态，鼠标按下
  - **注意多个伪类的书写顺序**，_爱恨法则(按以上顺序)_
- 伪元素选择器：定位 HTML 中未包含的实体以及无法以其他方式定位的内容部分（_伪元素：文档树中不存在的抽象元素_）
  - `::before` _创建一个伪元素_，它是所选元素的第一个子元素。
  - `::after` _创建一个伪元素_，它是所选元素的最后一个子元素。

### 更多选择器

更多伪类选择器：

- `:first-child` 选中第一个子元素(_可以直接使用，但一般配合元素选择器使用_)
  - `p:first-child` 选中是 `p` 元素**且**为父元素第一个子元素的元素
- `:first-of-type` 选中子元素中第一个为某类型的元素
  - `a:first-of-type` 选中父元素的子元素中第一个 `a` 元素
- `:last-child` 选中最后一个子元素
- `:last-of-type` 选中子元素中最后一个为某类型的元素
- `:nth-child(n)` 选中父元素的第 `n` 个子元素，`n = 0,1,2,3...`
  - `p:nth-child(2n+1)` / `p:nth-child(odd)` 选中父元素的**奇数**子元素且为 `p` 元素的元素
  - `p:nth-child(2n)` / `p:nth-child(even)` 选中父元素的**偶数**子元素且为 `p` 元素的元素
- `:nth-of-type(n)` 选中父元素的子元素中第 `n` 个为某类型的元素
  - `a:nth-of-type(2)` 选中父元素的子元素中第二个 `a` 元素

更多伪元素选择器：

- `::first-letter` 选中元素中的第一个字母
- `::first-line` 选中元素中的第一行文字
- `::selection` 选中被用户选中的文本

### 选择器的组合

1. 并且 `selector1selector2`
   - `a:hover`
   - `div::after`
   - `p.class-1`
   - `a[href="http://www.example.com"]`
2. 后代选择：选择选中元素的后代元素中的某些元素 `selector1 selector2`
   - `div ul`
   - `.red li`
   - `.class *` _选择所后代_
3. 子元素选择：选择选中元素的直接子元素 `selector1 > selector2`
4. 相邻兄弟选择：选择选中同一个父元素下的下一个**紧跟**选中的兄弟元素 `selector1 + selector2`
5. 兄弟选择：选择选中元素后的**所有**符合的兄弟元素 `selector1 ~ selector2`

### 选择器的并列

多个选择器可以用逗号 `,` 分隔

## 常用属性

- `width` 元素的宽度
- `height` 元素的高度
- `color` 元素内部文字的颜色
- `background-color` 元素的背景颜色
- `font-size` 字体尺寸大小，可以简单理解为文字的高度
- `font-weight` 字体粗细程度，需要字体适配
  - `normal` = `400` _默认值_
  - `bold` = `700`
- `font-family` 字体，可以使用多个字体以匹配不同环境
  - `sans-serif` 无衬线字体，操作系统自动选择
- `font-style` 字体样式，通常用于设置斜体
  - `normal` 正常
  - `italic` 斜体
- `text-align` 文本对齐方式
- `text-decoration` 文本修饰，如下划线、删除线等
- `text-indent` 首行文本缩进
- `line-height` 每行文本的高度，值越大每行距离越大
  - 直接设置数字值：表示相对于当前元素的字体大小，一般用于多行文字
  - 单行文本垂直居中：`line-height` = **内容盒高度**
- `letter-spacing` 文字间距
- `text-align` 元素内部文字的水平排列方式
  - 对元素内行(行块)盒都生效

### 常见简写属性

- `padding` / `margin`
  1. `-top` `-right` `-bottom` `-left`
  2. `-top` `-left & -right` `-bottom`
  3. `-top & -bottom` `-left & -right`
  4. `-top & -right & -bottom & -left`
- `border`
- `background`: `background-image` `background-repeat` `background-position`/`background-size` `background-attachment` `background-color`
- `font`: `font-style` `font-variant` `font-weight` `font-size`/`line-height` `font-family`

## 层叠

_声明冲突_：同一个样式多次应用到同一个元素

层叠（_权重计算_）：解决声明冲突的过程（_由浏览器处理_）

1. 比较重要性
2. 比较特殊性
3. 比较源次序

### 重要性

作者样式表中的 `!important` 样式 > 作者样式表中的普通样式 > 浏览器默认样式表中的样式

> _作者样式表：开发者书写的样式_

### 特殊性

总体规则：选择器选中的范围越窄越特殊

**具体规则**：通过选择器计算出一个4位数的权重（_满256进位_）

1. 千位：如果是内联样式则记 `1` 否则记 `0`
2. 百位：所有ID选择器的数量
3. 十位：所有类选择器、属性选择器、伪类选择器的数量
4. 个位：所有元素选择器、伪元素选择器的数量

### 源次序

源代码中书写顺序靠后的覆盖代码书写顺序靠前的样式

### 实际应用

- 重置样式表：书写一个（_通用_）作者样式表，覆盖浏览器默认样式
- _爱恨法则_：特殊性相同，按照交互逻辑的效果，利用源次序来达到想要的效果

> 常用的CSS重置样式表： [normalize.css](https://github.com/necolas/normalize.css/) [reset.css](https://www.joshwcomeau.com/css/custom-css-reset/) [meyer.css](https://meyerweb.com/eric/tools/css/reset/)

## 继承

子元素会继承父元素的**某些**属性，通常和字体、文字内容相关的属性都会被继承。

## 属性值的计算过程

- 浏览器渲染每个元素的前提条件：该元素的**所有css属性**都必须有值
- 浏览器渲染页面时，按照页面文档的树型目录结构，从上到下，从左到右依次渲染

一个元素从所有css属性都没有值到全部有值的过程叫属性值的**计算过程**：

1. 确定声明值：将样式表（_作者样式表，浏览器样式表_）中**没有声明冲突**的声明，作为CSS属性的值
2. 层叠冲突：对样式表中**有声明冲突**的声明，按**层叠**规则，确定CSS的属性值
3. 继承：对仍然没有值的CSS属性，若可以继承，则**继承**父元素的属性值
4. 使用默认值：如果仍然没有值，则使用默认值(_每个CSS属性都有默认值_)

## 常用属性值

### 颜色值表示

1. 预设值：定义好的单词，如 `red`
2. 三原色（_红、绿、蓝_）色值：
   - RGB (_十进制_): `rgb(red, green, blue)` 每个颜色取值范围为 `0~255`
   - HEX (_十六进制_): `#RRGGBB` 每个颜色取值范围为 `00` ~ `FF`, 如果每种颜色两位都相同，可以简写为 `#RGB`
3. 三原色+透明通道(_alpha_)：
   - RGBA: `rgba(red, green, blue, alpha)` 透明通道取值范围为 `0~1`，`0` 为完全透明，`1` 为完全不透明
   - HEXA: `#RRGGBBAA` 透明通道取值范围为 `00` ~ `FF`

### 特殊取值

- 强制继承：`inherit`
  - 可使不能继承的属性强制使用父元素的值
- 初始值：`initial` 将该属性设置为默认值

生效时间：**在层叠时确定值为特殊值，并不会使用后续步骤**

### 尺寸单位

- `px` 像素
- `em` _相对单位_，相对于父元素的字体大小的倍数，

> 每个元素必须有字体大小，如果一个元素没有声明字体大小，则会继承其父元素；
> 如果没有父元素，则使用基准字号（_浏览器设置的默认字号_，通常是16px）。

### 百分比取值

- `padding`, `margin`, `width` 所有百分比（**所有方向**）相对于**包含块**的宽度
- `height` 的百分比：
  - 包含块的高度取决于子元素，设置高度百分比无效
  - 包含块的高度不取决于子元素，高度百分比相对于父元素高度

## 盒模型

box(_CSS3 概念_): 盒子，每个元素在页面中都会生成一个矩形区域（盒子）

盒模型：规定单个盒子的规则

### 盒子类型

1. 行盒：`display:inline` 的元素，在页面中不换行
2. 块盒：`display:block` 的元素，在页面中独占一行

- `display` 属性默认值为 `inline`
- 浏览器默认样式表设置为块盒的元素：`容器元素`、`<H1>~<H6>`、`<p>`
- 浏览器默认样式表设置为行盒的元素：`<span>`、`<a>`、`<img>`、`多媒体元素`
- 文字一定在行盒中，如果文字没有在行盒中，浏览器会直接生成一个行盒包裹文字，该行盒叫 _匿名行盒_

### 盒子的组成部分

无论是行盒还是块盒，都由下面几个部分组成，从内到外分别是：

1. 内容 _content_
   - `width` 和 `height` 设置内容的宽高
   - 通常叫做整个盒子的**内容盒** （_content-box_）
2. 填充 _padding_：盒子边框到盒子内容的距离
   - `padding` 设置内边距
   - 填充区 + 内容区 = **填充盒** （_padding-box_）
3. 边框 _border_
   - `border` : `border-width` `border-style` `border-color`
   - 边框颜色默认为字体颜色
   - 边框区 + 填充区 + 内容区 = **边框盒** （_border-box_）
4. 外边距 _margin_：边框到其他盒子的距离
   - `margin` 设置外边距

### 相关属性的应用

#### 改变宽高范围

默认情况下，`width` 和 `height` 设置的是内容盒的宽高，但衡量设计稿是往往是边框盒的宽高。

解决方案：

1. 精确计算
2. (_CSS3中_)可以使用 `box-sizing` 属性改变宽高的影响范围
   - `box-sizing:content-box` (_默认值_)，宽高影响内容盒
   - `box-sizing:border-box` 改变宽高的影响范围为边框盒

> `outline` 外边框，不占据空间

#### 改变背景覆盖范围

默认情况下，背景覆盖边框盒。

(_CSS3中_)通过 `background-clip` 属性可以改变背景覆盖范围。

- `background-clip:border-box` (_默认值_) 背景覆盖边框盒
- `background-clip:padding-box` 背景覆盖填充盒
- `background-clip:content-box` 背景覆盖内容盒

#### 溢出处理

当设置宽高时，内容超出盒子范围时默认可见，(_CSS3中_)可以通过 `overflow` 属性（_简写属性_）设置溢出处理。

- `overflow:visible` (_默认值_) 超出内容可见
- `overflow:hidden` 超出内容隐藏
- `overflow:scroll` 生成滚动条
- `overflow:auto` 自动生成滚动条

> 网站标题为图片时，`H1` 元素的伪元素中用文字填写标题内容，再利用 `overflow:hidden` 隐藏文字，即实现了语义化，优化了SEO，又不影响图片的显示。

当一个元素垂直方向上存在滚动条时，其最后一个子元素的 `margin-bottom` 可能存在于不可见区域内，因为父元素没有足够的内容来滚动到那个位置。

#### 断词规则

(_CSS3中_) `word-break` 属性影响文字在**什么位置**被截断换行

- `word-break:normal` (_默认值_) 对于 `CJK` 字符在文字截断，非 `CJK` 字符在单词截断
- `word-break:break-all` 截断所有；对于所有字符都在文字截断
- `word-break:keep-all` 保持所有；所有字符都在单词截断

#### 空白处理

(_CSS3中_) `white-space` 属性控制元素内的空白字符（_空格、换行符等_）的处理规则

- `white-space:normal` (_默认值_)
- `white-space:nowrap` 不换行
  - 与 `overflow:hidden; text-overflow:ellipsis;` 结合使用，可以实现**单行文本溢出显示省略号**

> `pre` 元素的 `white-space` 属性值为 `pre`，禁止空白折叠

### 行盒盒模型的特点

1. 盒子沿着内容延伸
2. 宽高由内容决定，直接设置的宽高无效；如果需要调整盒子宽高，需要通过`font-size`, `line-height`, `font-family` 等属性间接设置
3. 水平方向上，盒子的左右边界由内容决定，不受 `padding` 影响；垂直方向上，盒子的上下边界由内容决定，不受 `border` 影响
4. 对于内边距（_填充区_），设置水平方向有效，垂直方向仅会影响背景，不会占据实际空间
5. 边框同上
6. 外边距同上

### 行块盒模型的特点

`display:inline-block` 的盒子

1. 不独占一行，适应行高
2. 盒模型中所有尺寸直接设置都有效

### 行盒的空白折叠

空白折叠发生在行盒（含行块盒）内部或行盒（含行块盒）之间，无法消除

> 除非源代码紧连在一起

## 可替换元素和非可替换元素

- 非可替换元素：大部分元素，页面上显示的结果，取决于元素的内容
- 可替换元素：少部分元素，显示结果取决于元素属性
  - 如 `<img>`, `video`, `audio`, `input`, `button`
  - 绝大部分可替换元素是行盒，但效果类似于行块盒，**所有盒模型中所有尺寸设置都有效**
  - CSS 不能完全控制其中所有的样式

### 调整图片适应盒子的方式

- `object-fit:fill` _默认值_ 拉伸图片，使其完全适应盒子
- `object-fit:contain` 保持图片比例，使其完全显示，可能留有“_黑边_“
- `object-fit:cover` 保持图片比例，裁剪图片，使其完全覆盖盒子
- `object-fit:none` 保持原有尺寸

## 视觉格式化模型

视觉格式化模型（布局规则）：页面中多个盒子的排列规则，大体分为三种：

- 常规流
- 浮动
- 定位

### 包含块 _containing block_

- 每个盒子都有它的包含块，包含块决定了盒子的排列区域。
- 绝大部分情况下，一个盒子的包含块为其父元素的内容盒

### 常规流

又叫文档流、普通文档流、常规文档流

- 所有元素默认属于常规流布局
- 总体规则：块盒独占一行，行盒水平依次排列

#### 块盒规则

1. 每个块盒的盒子总宽度**必须**刚好等于其包含块的宽度
   - `width:auto` _默认值_，将剩余空间吸收；`width` 吸收能力强于 `margin`
   - 水平方向上，若 `width`, `border`, `padding`, `margin` 计算后仍有剩余空间，该剩余空间被 `margin-right` 全部吸收
2. 每个块盒垂直方向上
   - `height:auto` _默认值_，高度由**内容**决定
   - `margin:auto` 垂直方向 `margin` 为 `0`，水平方向吸收剩余空间
3. [百分比取值](#百分比取值)
4. _外边距合并_：两个常规流块盒（_兄弟，父子_），**上下**外边距**相邻**，两个外边距会合并，取最大值。

- _在常规流中，块盒在包含块内水平居中_：定宽且左右 `margin` 为 `auto`
- `margin:0 -100px; width:auto` 宽度超出父元素

### 浮动

- `float:none` _默认值_，常规流
- `float:left` 左浮动，浮动元素靠上靠左依次排列
- `float:right` 右浮动，浮动元素靠上靠右依次排列

#### 浮动的基本特点

1. 当元素设置浮动后，必定为**块盒**(`display:block`)
2. 浮动元素的包含块和常规流一样，为**父元素的内容盒**
3. 浮动元素在包含块中排列时会**避开**上文的常规流**块盒**
4. 常规流**块盒**在排列时**无视**浮动元素
5. 行盒排列时会避开浮动元素
   - 用来实现文字环绕
6. 外边距合并不会发生

#### 浮动盒子规则

- `width:auto` 适应内容宽度
- `height:auto` 适应内容高度
- `margin:auto` 所有方向为 `0`
- [百分比取值](#百分比取值)

#### 应用场景

1. 文字环绕

   ```html
   <style>
     img {
       float: left;
     }
   </style>

   <div>
     <img src="example.png" />
     <p>lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
   </div>
   ```

2. 横向排列

#### 清除浮动

**高度坍塌**：浮动元素脱离了常规流，常规流盒子的自动高度，在计算时不会考虑浮动元素。

- `clear:none` _默认值_
- `clear:both` 清除左右浮动，该元素必须出现在前面所有浮动盒子的下方
- `clear:left` 清除左浮动，该元素必须出现在前面所有左浮动盒子的下方
- `clear:right` 清除右浮动，该元素必须出现在前面所有右浮动盒子的下方

```html
<style>
  .float-left {
    float: left;
  }
  .float-right {
    float: right;
  }
  .clearfix {
    clear: both;
  }
</style>

<div class="container">
  <div class="float-left">float-left</div>
  <div class="float-right">float-right</div>
  <div class="clearfix"></div>
</div>
```

```html
<style>
  .clearfix::after {
    content: '';
    display: block;
    clear: both;
  }
  .float-left {
    float: left;
  }
  .float-right {
    float: right;
  }
</style>
<div class="container clearfix">
  <div class="float-left">float-left</div>
  <div class="float-right">float-right</div>
</div>
```

### 定位

定位：手动控制元素在包含块中的精准位置

1. `position:static` _默认值_，静态定位（不定位）
2. `position:relative` 相对定位
3. `position:absolute` 绝对定位，相对于最近的已定位祖先元素进行定位
4. `position:fixed` 固定定位，相对于浏览器窗口进行定位

- 一个元素只要 `position` 不为 `static`，就认为该元素是**定位元素**
- 除相对定位外，定位元素会脱离文档流
  - 文档流中的元素摆放时，会忽略脱离文档流的元素
  - 文档流中元素计算自动高度时，会忽略脱离文档流的元素

#### 相对定位

元素不脱离文档流，让元素在原位置的基础上进行**偏移**，不会对其他盒子造成任何影响

- `left` 距离原位向右的偏移
- `right` 距离原位向左的偏移
- `top` 距离原位向下的偏移
- `bottom` 距离原位向上的偏移

> 尽量避免设置冲突，出现冲突时，以左和上为准

#### 绝对定位

- 从父元素开始，寻找祖先元素中第一个定位元素，该元素的**填充盒**（_padding-box_）作为包含块
- 如果找不到祖先中的定位元素，则以**整个网页**（_初始包含块 initial containing block_）作为包含块
- 宽高为 `auto` 时, 适应内容宽高
- `margin:auto` 时，自动吸收剩余空间
- 一定为块盒
- 一定不是浮动
- 没有外边距合并

位置设置：

- `left` 距离包含块左边界的距离
- `right` 距离包含块右边界的距离
- `top` 距离包含块上边界的距离
- `bottom` 距离包含块下边界的距离

#### 固定定位

- 固定定位的元素的包含块固定为**视口**（_viewport 浏览器可视窗口_）
- 其他同绝对定位

#### 定位下的居中

某个方向（上下/左右）居中：将左右（上下）距离都设置为 `0`，将 `margin` 设置为 `auto` (_不设置的值会为`auto`, 吸收剩余空间_)

### 堆叠上下文

- 通常情况下，`z-index` 值越大，越靠近用户
- 一个元素的 `z-index` 可以为负值，常规流元素和浮动元素将他会覆盖

## 常见效果

### 设置透明度

- `opacity` 属性：设置整个元素的透明度，取值范围 `0~1`，`0` 为完全透明，`1` 为完全不透明
- [在颜色位置设置 `alpha` 通道](#颜色值表示)

### 鼠标样式

`cursor` 属性：设置鼠标指针的样式

- `cursor:auto` _默认值_ 由浏览器控制
- `cursor:pointer` 手型
- `cursor:url('path/to/image'),auto` 设置鼠标为自定义图片，若浏览器不支持自定义鼠标，则由浏览器控制

### 盒子隐藏

- `display:none` 不生成盒子
- `visibility:hidden` 生成盒子，从视觉上移除盒子，但仍占据空间

### 背景图

背景图使用场景：

- `img` 元素属于 `HTML`概念，而背景图属于 `CSS` 的概念
- 当图片属于网页内容时，必须使用 `img` 元素
- 当图片仅用于美化页面时，必须使用背景图
- 背景图可与背景颜色配合使用

相关属性：

- `background-image:url(image.jpg)` 设置背景图片 _文件路径相对于CSS文件位置_
- `background-repeat` 控制背景图重复方式，默认情况下，背景图会在横坐标和纵坐标中进行重复
  - `background-repeat:repeat` _默认值_ 重复
  - `background-repeat:no-repeat` 不重复
- `background-size` 控制背景图的尺寸
  - `background-size:auto` _默认值_ 背景图的尺寸由图片本身决定
  - `background-size:cover` 背景图完全覆盖元素，比例不变，可能裁剪部分图片
  - `background-size:contain` 完整显示背景图，比例不变，可能不完全覆盖元素
  - `background-size:100px 100%` 宽度为 `100px`，高度为 `100%`
- `background-position` 控制背景图的位置
  - 预设值：`top` `center` `bottom` `left` `right`
  - `background-position:center` 横向纵向居中
  - `background-position:top left` 纵向靠上 横向靠左
  - `background-position:10px 20px` 背景图左边距离左边界为 `10px`，上边距离上边界为 `20px`
- `background-attachment` 控制背景图是否固定
  - `background-attachment:scroll` _默认值_ 背景图随元素一起滚动
  - `background-attachment:fixed` 背景图相对于视口固定

雪碧图（精灵图 _sprites_）：

- 将多个小图片拼接合并成一张图片，减少文件和请求次数，提高渲染效率
- 调整 `background-position` 属性和容器宽高，将小图标取出，放置在合适的位置

## Demo

<!-- @include: @demo/CSS-1-Carousel.md#demo -->
