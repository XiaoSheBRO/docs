# HTML

HTML: `HyperText Markup Language` 超文本标记语言，用于定义网页内容。

> 由 w3c （_互联网标准组织_） 定义 HTML 语言标准。

## 元素 `element`

元素 = 起始标记（_begin tag_） + 元素内容 + 结束标记（_end tag_） + 元素属性

> 元素的嵌套：元素不能相互嵌套
> 元素关系：父元素、子元素、兄弟元素、祖先元素、后代元素

_空元素_：没有结束标记

> `<br>` & `<br />`：
> `<br>` 是 HTML 写法,是 XHTML1.1 的写法, 也是 XML 写法。（_XHTML：HTML 严格遵守 XML 语法规范的一个版本_）
> `<br />` 是 XHTML 为兼容 HTML 的写法,也是 XML 写法。
> HTML5 因为兼容 XHTML，所以两种写法都可以使用。
> 早期发布的 HTML 规范当中，`<br>` 与 `<img>` 等元素是不用封闭自身的，但是这种元素造成了 HTML 规范的不严谨，于是在之后发布的 XHTML 语言中，参考了更为严谨的 XML 规范，在这些不用自身封闭的元素后加 / 来表示自行封闭。

### 属性的分类

- **全局属性**：所有元素都可用的属性
- **局部属性**：某些原色特有的属性

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

根元素：一个页面最多存在一个根元素，且该元素是所有其他元素的父元素或祖先元素。

> HTML5 规范中， `<html>` 作为根元素不具有强制性。

`lang`：**全局属性**，用于定义页面的自然语言。

> 简体中文最新表示：`zh-CN` ==> `cmn-hans`

### `head` 元素

文档头，_文档头内部的内容不会显示在页面内_。

#### `meta` 元素

文档的元数据：附加信息。

```html
<head>
  <!-- charset 指定网页内容编码，局部属性 -->
  <meta charset="UTF-8" />
  <!-- viewport 设置网页视口 -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <!-- 解决IE兼容问题 -->
  <meta http-equiv="X-UA-Compatible" content="ie=edge" />
  <!-- 网页标题 -->
  <title>Document</title>
</head>
```

### `body` 元素

文档体，_所有要参与显示的内容都放在这里_。
