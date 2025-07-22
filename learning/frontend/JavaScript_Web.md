# JavaScript Web Api

标准库：ECMAScript 中的对象和函数

Web Api：浏览器宿主环境提供的对象和函数

Web Api 主要包含：

1. BOM：_Browser Object Model_，浏览器对象模型，用于控制浏览器本身的功能
2. DOM：_Document Object Model_，文档对象模型，控制 HTML 文档

> Web Api 标准由 w3c 组织制定

## DOM

DOM 是将一个 HTML 或 XML 文档，用对象模型表示，每个对象称为 DOM 对象，也称 DOM 节点（_Node_）。

DOM 树：文档中不同的节点形成的树形结构。

::: details 📚 节点的类型

- DocumentType：文档节点
- Document：整个文档
- Comment：注释节点
- Element：元素节点
- Text：文本节点
- Attribute：属性节点
- DocumentFragment：文档片段节点

:::

### 获取 DOM 节点

即获取 DOM 对象

全局对象 `window` 中 `document` 属性代表整个文档的节点。

旧的获取方式：

- `document.body` 获取 `body` 元素节点
- `document.head` 获取 `head` 元素节点
- `document.links` 获取所有 `a` 元素节点，_伪数组_
- `document.documentElement` 获取根元素

> 具有 `id` 属性的元素会自动成为 `window` 的属性，且为一个实时更新的对象，不推荐使用。

#### 通过方法获取

1. `document.getElementById('id')` 根据 `id` 获取，返回单个节点
2. `document.getElementsByTagName('tag')` 通过元素名称获取，返回类数组
3. `document.getElementsByClassName('class')` 通过类样式名获取，返回类数组
4. `document.getElementsByName('name')` 通过 `name` 属性获取，返回类数组
5. `document.querySelector('selector')` 通过 CSS 选择器获取，返回单个节点
6. `document.querySelectorAll('selector')` 通过 CSS 选择器获取，返回类数组

::: tip

- `getElementById` 得到元素的执行效率最高。
- 在所有获取结果为类数组的方法中，除 `querySelectorAll` 外，其他方法的类数组都都是**实时更新**的，**注意使用时的变化，如果不想变化可以转换为真数组**。
- `getElementsByTagName`, `getElementsByClassName`, `querySelector`, `querySelectorAll` 可以作为其他元素节点对象的方法使用。

:::

#### 根据节点关系获取

- `node.parentNode` 获取父节点
- `node.previousSibling` 获取前一个兄弟节点
- `node.nextSibling` 获取后一个兄弟节点
- `node.firstChild` 获取第一个子节点
- `node.lastChild` 获取最后一个子节点
- `node.childNodes` 获取所有子节点，_类数组，实时更新_

> 未获取到节点时，返回 `null`

仅获取元素节点：

- `element.parentElement` 获取父元素
- `element.previousElementSibling` 获取前一个兄弟元素
- `element.nextElementSibling` 获取后一个兄弟元素
- `element.firstElementChild` 获取第一个子元素
- `element.lastElementChild` 获取最后一个子元素
- `element.children` 获取所有子元素，_类数组_

#### 节点信息

- `node.nodeName` 获取节点名称
  - 元素节点的节点名称为全大写
- `node.attributes` 获取节点的所有属性，返回类数组
- `node.nodeValue` 获取节点的值
- `node.nodeType` 获取节点类型，返回一个数字

<!-- TODO 获取一个元素节点子节点中第一个div-->

### 操作 DOM 节点

::: details 📚 元素与事件

元素事件：某个元素发生的特定事件，如点击、输入、移动等。

事件处理程序：发生事件过后，执行的函数。

注册事件：将事件处理程序与某个事件关联。

```html
<button id="btn">Click me</button>
<script>
  var btn = document.getElementById('btn')
  btn.onclick = function () {
    // do something
  }
</script>
```

==`this` 关键字在事件处理程序中指代触发事件的元素对象==

:::

#### 获取和设置元素属性

可识别属性（_正常的 HTML 标签属性_）：

- 获取属性：`DOM对象.属性名`
- 设置属性：直接赋值

::: tip

- 正常的可识别属性即使没有赋值，也会有默认值
- 布尔属性在 DOM 对象中的值为 Boolean 类型
- 某些表单元素可以获取到不存在的属性
- 某些属性名与 JavaScript 关键字冲突，需要使用变更的名称

:::

通用方式（不推荐用于可识别属性，仅用于自定义属性）：

- `dom.getAttribute(属性名)` 获取属性值
- `dom.setAttribute(属性名, 属性值)` 设置属性值

```html
<input type="text" value="abc" />
<div value="123"></div>
<script>
  var input = document.querySelector('input[type="text"]')
  console.log(input.value) // "abc"
  var div = document.querySelector('div')
  console.log(div.value) // undefined
  console.log(div.getAttribute('value')) // "123"
</script>
```

::: info
HTML 5 规范建议使用 `data-` 前缀作为自定义属性的命名；如果遵从该规范可以使用：

- `dom.dataset.属性名` 获取属性值；属性名自动使用驼峰命名法
- `dom.dataset.属性名 = 属性值` 设置属性值

`Element.dataset` 是一个对象，方便获取元素的自定义属性。

删除自定义属性：

- `dom.removeAttribute(属性名)`
- `delete dom.dataset.属性名`

:::

#### 获取和设置元素内容

- `Element.innerHTML` 元素内部的 HTML 文本
- `Element.innerText` 元素内部的纯文本(显示出来的文本)
- `Element.textContent` 元素内部源代码中的纯文本

#### 元素结果重构

- `Element.appendChild(node)` 向元素（内部）末尾添加一个节点
- `Element.insertBefore(newNode, referenceNode)` 在元素内部的 referenceNode 节点之前插入一个新的节点
- `Element.replaceChild(oldNode, newNode)` 在元素内部用一个新的节点替换旧的节点

同一个节点对象只存在于页面一个位置。

更改元素结构效率较低，尽量少用；如需使用，尽量一次性完成。

#### 创建元素

- `document.createElement('tagName')` 创建一个元素对象
- `document.createTextNode('text')` 创建一个文本节点
- `document.createDocumentFragment()` 创建一个文档片段对象，用于将多个节点放入后，一次性插入文档

```js
var fragment = document.createDocumentFragment()
for (var i = 0; i < 10; i++) {
  var li = document.createElement('li')
  li.textContent = 'Item ' + i
  fragment.appendChild(li)
}
document.querySelector('ul').appendChild(fragment)
```

同一个节点对象只存在于页面一个位置。

#### 克隆元素

`Element.cloneNode()` 将该对象格隆并返回一个新的对象

参数 `deep`

- `true` 深度克隆内部的对象
- `false` 只克隆该对象本身，_默认值_

#### 删除元素

- `Element.removeChild(node)` 从元素内部移除一个节点
- `Element.remove()` 从文档中移除该元素

移除只是页面结构上的变化，不会影响节点对象。

<!-- @include: @demo/JS-15-DomDelete.md#demo -->

<!-- TODO 数字输入框（使用 data- 属性） -->

### DOM 元素样式

#### 控制 DOM 的类样式

- `Element.className` 元素的类名（所有）
- `Element.classList` 类名列表，_类数组_
  - `classList.add(className)` 添加一个类名
  - `classList.remove(className)` 移除一个类名
  - `classList.contains(className)` 判断是否包含一个类名
  - `classList.toggle(className)` 切换一个类名

#### 获取样式

- `dom.style` 元素的**行内样式**，_样式对象_
- `window.getComputedStyle(dom)` 得到元素的**计算样式**，_样式对象_
  - 第二个参数可以指定伪元素的样式，如 `'before'`

> CSS 中的 `-` 命名需要使用驼峰命名获取对应的值

#### 设置样式

- `dom.style.样式名` 设置**行内样式**

<!-- TODO 拼图游戏 -->

## DOM 事件

事件：发生一件事
事件类型：发生事情的类型，如点击、鼠标移动等
事件处理程序：一个函数，当某个事件发生时运行
事件注册：将事件处理程序挂载到某个事件上

### 事件流

当某个事件发生时，哪些元素会监听到该事件发生，**这些元素监听到事件的顺序称为事件流**。

==当一个元素发生某个事件时，该元素的所有祖先都发生了该事件（发生但不一定有处理）。==

- 事件冒泡：先触发最里层的元素，然后逐级向上传播
- 事件捕获：先从最外层的元素开始触发，然后逐级触发里层元素

目前的标准规定：**事件默认是冒泡的**

![事件流](../../assets/images/JS-1-DomEvent.jpg)

事件源 / 事件目标：事件目标阶段的元素。

### 事件注册

也称事件绑定

注册方式：

- 将事件名称前加 `on` 的单词作为属性名，然后直接给 DOM 对象的该属性赋值为函数，即为注册事件
