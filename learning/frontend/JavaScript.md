# JS 基础教程

## js

控制网页的行为：用户与浏览器交互、浏览器与服务器的交互
js = ECMAScript + DOM + BOM

> `alert()` > `console.log()`

### 变量与数据类型

`var x = *;` 声明变量
`var x = *, y = "";` 多个变量用**,**隔开
**命名规则**：字母、数字(_不能作为开头_)、$、下划线

> 驼峰：首字母小写，第二个单词首字母大写

**数据类型**：String, Number, Boolean, Object 对象, NUll, Undefined 未定义

> `var x;` x 值为未定义
> Undefined 一般不用于赋值；变量尽量不要不定义

### 运算符

> ++x 值为 x + 1
> x++ 的输出是 x,但 x 稍后会自增
> (java 中运算过程也有先后，但输出值相同)

`==` 只比较数值，自动转换类型
`===` 比较值和数据类型(最佳实践，为了性能尽量用`===` `!==`)

**简化条件运算**
`条件表达式` ? `值1` : `值2`;
例：`z` = `x` > `y` ? `true情况的值` : `false情况的值`;

### 条件语句

```js
switch (*) {
    case *: ...;break;
    case *: ...;break;
    case *: ...;break;
    default *: ...;break;
}
```

```js
do {
//必定执行一次
}while ();
```

### 函数

```js
function name() {}
```

- 声明提升(**赋值形式的表达式除外**)
- 参数可以设置默认值

特殊函数

- 匿名函数用于回调函数(_作为参数_)
- 递归函数(_函数体能调用自己_)

### 对象

属性的无序集合

```js
var name = {
    x = *,
    y = "*"
    z:function(){}
    /* this.x内部调用 */
}
```

`var name = null;` 定义空对象，对象暂无属性

#### 对象的分类

- 自定义对象：封装
- 内置对象：例 Date
- 宿主对象：Document
- 第三方库的对象：jQuery，Vue

### 数组

遍历数组的特殊方法

```js
//特殊循环法
for(var i in list){
    console.log(list[i]);
}
for(var i of list){
    console.log(i);
}
//数组的map方法+回调函数
list.map(function(value,index)){
    console.log(value);
    console.log(index);
}
```

数值常用方法
`list.push(*)` 结尾增加值
`list.sort()` 排序
`list.filter()` 列表过滤

```js
var newList = list.filter(function(item)){
    if (item 条件){
        return item;
    }
}
```

`list.join("连接符")` 打印数组(_字符串_)

> `string.split("识别符")` 字符串分割为数组(_不填则为单个元素，填参数则按识别符分割_)

## js 常用内置对象

### Math

- `Math.floor()` **向下**取整
- `Math.random()` **0-1**随机数
- `Math.abs(*)` 求绝对值
- `Math.sqrt(*)` 开方
- `Math.pow(*,^)` 乘方

**获取 1-10 的整数随机数**(1-x 替换 \* x)
`result = Math.floor(Math.random() * 10 + 1);`

### Date

定义一个新的时间(_无参数则为当前时间_)
`var d = new Date("xxxx-xx-xx xx:xx:xx");`

- `.getFullYear()`
- `.getMonth()` 0~11
- `.getDate()` 日期
- `.getDay()` 星期
- `.getHours()`
- `.getMinutes()`
- `.getSeconds()`
- `.getTime()` 时间戳（格林威治时间 1970.01.01.00.00.00 到现在的总毫秒数）

## 正则表达式

用途：匹配字符串；字符串截取、替换、验证

`var reg = /.../;`
`reg.test(str)` 匹配是否正确，返回 _true/false_
`reg.exec(str)` 返回符合的匹配内容**数组**格式
`/.../g` 全局匹配
`^` 限定匹配内容开头
`$` 限定匹配内容结尾
`[]` 指定内容限制范围

- `[a-z0-9A-Z_]`或`\w` 数字&字母&下划线
- `\d` 数字
- `\s` 空格或换行
- `.` 所有内容 (_不为 null_)
- `\` 操作符号转义符

- `{*}` 位数 (_默认 1 位_)
- `{*, *}` 位数范围
- `+` 1 位或多位
- `?` 0 或 1 位

### 用正则表达式进行字符串替换

`str.replace(reg, "...")`

### 用正则表达式进行字符串截取

`()` 对匹配内容进行分组(_配合`exec`方法_)

## ES6+ (_JavaScript 新的版本特性_)

### 变量 `let`

`let` 替换 `var`

- **作用于块级作用域**`{}`，外部无法访问；
- **变量声明提升**：下方定义的 `var` 上方的代码无法访问，`let`则可以；
- 重复声明：`var`会覆盖，`let`不允许重复声明。

### 常量 `const`

声明后值不可改变，对象属性可以改

- 用来声明**函数** `const myFunction = () => {}`
- 用来声明**对象**
- 用来引入**外部模块**

### 模板字符串 \` \`

字符串两边用 \` 替换 "

- 支持换行
- 可在内部使用`${}`嵌入参数

### 解构赋值

数组形式：`let [x, y] = [1, 2];`
`[x, y] = [y, x];` 方便值的调换

对象形式：`let {name, age} = {name:"小米", age:10};`
方便拿到属性，传递参数

```js
function getName({ name }) {
  return name
}
```

## 函数进阶

> NaN (_Not a Number_)

### 作用域链

- 外部无法访问内部作用域的变量
- 同名变量优先为当前作用域的值，否则向上一层作用域寻找值

### 立即执行函数

```js
;(function () {
  //封装函数
})()
```

(_立刻执行一次；不能重复调用_)

### 闭包

- 在一个函数中声明的函数叫做闭包函数
- 闭包：内部函数总是可以访问外部函数的参数或变量；内部函数未执行完则外部函数不会被销毁

当内部函数作为外部函数的返回值；其在最外部被调用时则仍可访问外部函数内定义的参数或变量
**用处：利用闭包实现函数封装，不会暴露不必要的参数**

> 写在立即执行函数内则为 ES5 模块化用法，ES6+ 有模块化语法，导致这种方法现在不常用

### **箭头函数**

基本语法：

- 去掉`function`关键字：`(参数) => {}`
- _函数内只有返回操作时_：(参数) `=>` 返回值

`this`关键字指向：

- 普通函数指向调用该函数的对象
- 箭头函数指向定义的父级对象

## 面向对象的语法

### ES5

没有类的概念，用构造函数代替(_首字母大写_)

```js
//构造对象
function Student(name, age) {
  this.name = name
  this.age = age
}
Student.prototype.sayName = function () {
  console.log(`我的名字叫${this.name}`)
} //通过`.prototype`(原型对象）为对象添加方法

var student = new Student('小米', 10) //实例化

function Boy(name, age) {
  this.name = name
  this.age = age
}
Boy.prototype = new Student() //用原型链实现继承
```

### ES6

支持类 使用`class`关键字

```js
class Student {
  //使用`constructor`关键字构造函数和属性
  constructor (name) {
  this.name = name;
  }
  sayName () {
    //类的方法
  }
}
//继承
class Boy extends class Student{
   constructor (name，age){
       super(name);
       this.age = age;
   }
}
```

> [参考](https://www.yuque.com/istao/inunbi/kt5526)

## DOM 基础

操作 html 元素的标准编程接口

### 获取 dom（元素/节点）

`document` 对象

元素形式(_尽量弃用_)

- `document.getElementById(" * ")`
- `document.getElementByClassName(" * ")` 集合

**选择器形式**(_尽量使用，性能更好_)

- `document.querySelector(" * ")` 只返回第一个
- `document.querySelectorAll(" * ")` 多选

可填入 `#`id `.`className 或网页标签

### 属性设置

- `*.style.css样式(驼峰命名)` 直接设置样式
- `*.src` 设置内容路径
- `*.id` 设置 id
- `*.className` 设置类名(_通常用来改变 css 样式_)

> `inp.value` 输入组件的内容

### `*.innerHTML`

设置网页元素内**所有**html 内容

```js
*.innerHTML = `
    //html内容
`
```

### 节点操作

创建元素节点：`document.createElement("网页元素")`
创建文本节点：`document.createTextNode("文本")`
添加节点：`*.appendChild(*)`
删除节点：`*.removeChild(*)`

## 事件

### 事件监听

监听事件(_多个同样事件会被覆盖，冒泡阶段触发_) `*.on+事件类型`

> `*.onclick` 点击
> `*.onmouseenter` 鼠标移入
> `*.onmouseleave` 鼠标移出
> `*.onmousemove` 鼠标移动

```js
事件 = function () {}
```

### 事件对象

`event` 作为形参放在事件函数内
`事件 = function (event) {};`

> 由于是形参所以可以任意改名，一般简写作`e`

- `e.clientX` 鼠标点击时的 x 坐标
- `e.clientY` 鼠标点击时的 y 坐标

### 事件绑定

可以同时绑定多个函数(_不会被覆盖_)，便于添加功能；可设置在捕获阶段触发

```js
*.addEventListener("事件类型", function () {

}, true/false(_默认，一般不写_))
```

### 事件流

![1658989747466](../../assets/images/1658989747466.png)

- `false` 绑定事件默认为冒泡阶段触发(_从内到外_)
- `true` 改为捕获阶段触发

**阻止继续冒泡，避免重复触发外层事件** `e.stopPropagation();`
**取消 html 元素默认行为** `e.preventDefault();`/`return false;`

### 事件委托

根据事件的捕获和冒泡顺序，在父级元素下通过 `e.target`(_选中子级_)，将子元素的事件委托给父级处理

### 事件类型

- 鼠标事件
- 键盘事件
  - `keydown` 按下键盘
- 触屏事件
  - `touchstart` 触摸开始
  - `touchend` 触摸抬起
  - `touchmove` 按住滑动

> `e.keyCode` 键盘按键的键码

## BOM

浏览器对象模型

### `window` 对象

_全局对象_：可以不用加 `window.`

#### 计时器方法

- `setInterval` 循环执行
- `clearInterval` 暂停执行

```js
let * =setInterval(function () {
  // 功能
}, 间隔毫秒数);
clearInterval(*)
```

- `setTimeout` 延迟执行
- `clearTimeout` 取消执行

```js
let * =setTimeout(function () {
  // 功能
}, 开始延迟);
clearTimeout(*)
```

#### 防抖与节流

**防抖**：阻止高频触发

```js
let timer = null;
高频触发事件 = function() {
  if(timer !== null) {
    clearTimeout(timer);
  }
  timer = setTimeout(()=>{
    // 业务功能
    timer = null;
  },触发延迟)
```

**节流**：阻止高频，缓慢间隔触发

```js
let mark = true
事件 = function () {
  if (mark) {
    setTimeout(() => {
      // 业务功能
      mark = true
    }, 执行间隔)
  }
  mark = false
}
```

#### 弹出框

- `alert("");` 弹出消息，只能确定
- `prompt("提示", "文本框默认内容");` 文本框；值为输入内容，点取消则为 `null`
- `confirm("");` 值为布尔值，确定为 `true`,取消为 `false`

### `location` 对象

用于获得当前页面的止(URL)，并把浏览器重定向到新的页面。

- `location.href` 返回当前页面 url
  - `location.href = "..."` 页面跳转
- `location.hostname` 返回当前主机域名
- `location.pathname` 返回当前页面所在路径和文件名
- `location.port` 返回当前端口
- `location.protocol` 返回当前协议

### `navigator` 对象

包含有关访问者浏览器的信息

- `navigator.userAgent` 当前访问设备

### `screen` 对象

包含有关用户屏幕的信息

### `history` 对象

包含浏览器的历史

## 原始类型与引用类型

![1659080264172](../../assets/images/1659080264172.png)

### 赋值区别

- 引用类型会随着被引用的属性的改变而改变

### 比较区别

- 原始类型只比较值
- 引用类型比较指向的内存空间；所以值相同却不指向同一个对象，则不等

### 传参区别

- 原始类型内部作用域的值不影响外部
- 引用类型外部会受到影响，因为内部作用域操作了其引用空间

### 类型检测

- `typeof(原始类型)` (_除了`null`，`引用类型`全检测为`object`_)
- `变量 instanceof 类型` 引用类型检测**是否**在某一类型内

> `null` 为原始类型
> 所有对象都继承于 `object`

## 异步编程

不会因为某一操作的卡顿使整体卡顿

```js
// 假数据
let target = 'hello world'
// 模拟延迟
function getData() {
  setTimeout(() => {
    return target
  }, 500)
}
// 解法1：回调函数
function getData1(fn) {
  setTimeout(() => {
    fn(target)
  }, 3000)
}
getData1((x) => {
  console.log(x)
})
//解法2：promise ES6内置对象
let p = new Promise((resolve) => {
  setTimeout(() => {
    resolve(target)
  }, 500)
})
p.then((y) => {
  console.log(y)
})
//终极解法3：async函数
async function fun() {
  let z = await getData()
  console.log(z)
}
fun()
```
