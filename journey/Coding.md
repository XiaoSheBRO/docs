# Coding

## (element/element-plus) `el-button` 的 `.focus` 颜色问题

::: tabs
@tab solution

阻止以下事件

```vue
<!-- vue3+js -->
<el-button @mousedown="($event) => $event.preventDefault()"></el-button>
<!-- vue3+ts -->
<el-button @mousedown.prevent></el-button>
```

@tab cause
element 无障碍样式 使点击按钮 focus 无法自动失焦，与禁用效果易混淆
:::

## (element-plus) `el-table` 中使用 `el-image` 预览图片样式失效解决

```css
:deep(.el-table__cell) {
  position: static !important;
}
```

## (CSS) `flex-warp: warp;` 下元素间距优雅方案

```css
.flex-box {
  gap: 20px;
  gap: 20px 10px; /* row column */
}
```

## (CSS) ios 版本过低(小于 14.5)不支持 `flex` 下的 `gap` 属性时，`flex-warp` 动态布局方案

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
  /* 这意味着每列的最小宽度是100px，并自动换行到下一行，1fr表示剩余空间的等分，如果某个项目的宽度超过了100px，它将占据更多的列以适应自身宽度。 */
  /* 也可定宽 */
  gap: 10px;
}
```

## (CSS) `flex-box` 宽度自适应下 `text-overflow: ellipsis` 失效解决方法(单行)

::: tabs
@tab solution

```css
.container {
  display: flex;

  .left {
    flex: 1;
    width: 0;
    white-space: nowrap;
    overflow: hidden;
    word-break: break-all;
    text-overflow: ellipsis;
  }

  .right {
    text-align: right;
    flex-shrink: 0;
  }
}
```

@tab cause
待补充
:::

## (CSS) `flex-warp: warp;` 下 `warp` 行间距会自适应，定宽方案

```css
.flex-box {
  gap: 10px 10px; /* row column */
  align-content: flex-start;
}
```

## (CSS) ios下 Safari/webview 页面上下左右边缘 `margin` 会失效

> 改用 `padding`

## (CSS) 移动端单行文字，多行文字超出显示省略号

### 单行

```css
.box {
  width: 100px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

```css
.box {
  width: 100px;
  height: 100px;
  overflow: hidden;
  text-overflow: ellipsis;
  word-break: break-all;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
```

## (CSS) 滚动条隐藏

```scss
.overflow-x-hide-scroll {
  overflow-x: scroll;
  scrollbar-width: none; /* firefox */
  -ms-overflow-style: none; /* IE 10+ */
  &::-webkit-scrollbar {
    display: none; /* Chrome Safari */
  }
}
```

## (CSS) `line-height = height`的使用场景

`height`一定是内容盒的高度，若为 `box-sizing: border-box` 时，此时的 `height` 为整个盒子的高度，在 `box-sizing: content-box` 的情况下，需要减去 `padding`,`border` 的尺寸才为真实的内容盒的 `height`

## (CSS) 父元素 `flex: 1` 的条件下，子元素宽度与父元素保持一致且不撑开父元素，使文字自动超出隐藏

```css
.icon-banner {
  box-sizing: border-box;
  overflow-x: scroll;
  display: flex;
  margin: 0 24px;
  padding: 32px 10px;
  min-width: 702px;
  height: 180px;
  background-color: red;
  border-radius: 16px 16px 16px 16px;
  gap: 20px;
}

.banner-item {
  position: relative;
  flex-grow: 1;
  flex-shrink: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 148px;
  background-color: #fff;
}

.banner-item .item-icon {
  width: 72px;
  height: 72px;
  margin-bottom: 8px;
}

.banner-item .item-title {
  position: absolute;
  bottom: 0;
  left: 0;
  max-width: 100%;
  min-width: 100%;
  height: 36px;
  font-weight: 400;
  font-size: 26px;
  color: #646466;
  line-height: 36px;
  text-align: center;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```

> 普通文字显示直接在父级加上 `overflow: hidden; text-overflow: ellipsis;` 即可
