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
- 在所有获取结果为类数组的方法中，除 `querySelectorAll` 外，其他方法的类数组都都是实时更新的。
- `getElementsByTagName`, `getElementsByClassName`, `querySelector`, `querySelectorAll` 可以作为其他元素节点对象的方法使用。

:::

#### 根据节点关系获取

- `node.parentNode` 获取父节点
- `node.previousSibling` 获取前一个兄弟节点
- `node.nextSibling` 获取后一个兄弟节点
- `node.firstChild` 获取第一个子节点
- `node.lastChild` 获取最后一个子节点
- `node.childNodes` 获取所有子节点，_类数组_

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

- `DOM对象.getAttribute(属性名)` 获取属性值
- `DOM对象.setAttribute(属性名, 属性值)` 设置属性值

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

- `DOM对象.dataset.属性名` 获取属性值
- `DOM对象.dataset.属性名 = 属性值` 设置属性值

`Element.dataset` 是一个对象，方便获取元素的自定义属性。

:::

#### 获取和设置元素内容

- `Element.innerHTML` 元素内部的 HTML 文本
- `Element.innerText` 元素内部的纯文本(显示出来的文本)
- `Element.textContent` 元素内部源代码中的纯文本

#### 元素结果重构
