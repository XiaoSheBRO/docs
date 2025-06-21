# SVG

_scalable vector graphics_，可缩放矢量图

svg 使用 xml 格式定义

## 特点

1. svg 图片使用代码书写而成，所以内容轻量
2. 缩放不会失真

## 使用方式

1. 直接嵌入浏览器
   - 浏览器直接打开
   - 嵌入 html
2. 作为单独的文件使用
   - `<img src="image.svg">`
   - `<object data="image.svg" type="image/svg+xml"></object>`
   - `<embed src="image.svg" type="image/svg+xml">`
   - `<iframe src="image.svg"></iframe>`
   - `background-image: url("image.svg")`

## 基本语法

<!-- @include: @demo/SVG-1-Demo.md#demo -->

### `<svg>`

根节点

- `xmlns`: 命名空间
- `width`: 宽度
- `height`: 高度
  - 默认宽高：300x150
