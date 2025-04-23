# JavaScript

## JavaScript 起源

网景公司（Netscape Communication Corporation）于 1994 年推出了第一款商用浏览器：网景（Netscape Navigator）。
1995 年，网景公司决定在浏览器中加入一门编程语言，用于实现用户交互效果，提高用户体验。
网景公司聘请 **Brendan Eich** 开发这门语言。10 天后， LiveScript 语言诞生。后来为了商业考虑，更名为 JavaScript（_JS_）。

> Java 与 JavaScript 的关系：周杰 ~ 周杰伦；葡萄 ~ 葡萄牙。

### 第一次浏览器大战

网景公司计划在浏览器中加入网络操作系统，触动了微软的利益；
1995 年微软发布 IE 浏览器，第一次浏览器大战开启。
JS 推出之后，网景取得了极大的竞争优质。
微软对 JS 进行反编译，并借鉴 JS 推出了 JScript、VBScript 两种语言，这两种语言都可以在 IE 中执行。

第一次浏览器大战是**标准之争**。

1997 年，网景将 JavaScript 1.1 版本提交给 ECMA (欧洲计算机制造协会)，希望将其标准化。
ECMA 收录了 JavaScript 并提交给 ISO；经修改成为第一个JavaScript 标准，称为 **ECMAScript**，简称 ES。

IE3 发布，并绑定 Windows 操作系统，网景市场份额不断下滑，于 1998 破产被收购。

### 第二次浏览器大战

微软推出 IE4、IE5、IE6（捆绑 Windows XP）后，微软决定解散浏览器团队。
Brendan Eich 在网景解散后，带领团队成立 Mozilla 基金会，并将网景浏览器和 JS 开源。
长时间内世界技术爱好者们对网景浏览器进行维护和修补。
2002 年 Mozilla 基金会推出 Firefox 浏览器。
2008 年 Google 推出 Chrome 浏览器；2010 年 Apple 推出 Safari 浏览器；2012 年 ASA 推出 Opera 浏览器。
Chrome 浏览器搭载了 JS 引擎 V8，可以将 JS 代码直接转换为字节码；JS 代码的执行速度大幅提升，理论上已经接近汇编语言。从此 JS 具备了编写大型应用的能力，甚至服务器应用。**V8 引擎将 JS 的执行推向了一个新的台阶。**

> Ryan Dahl 直接利用 V8 引擎完成了 node.js，使 JS 语言在服务器端可以运行。

### ES 标准的发展

1997年 -- ES1
1998年 -- ES2
1999年 -- ES3
2009年 -- ES5，从此习惯上不再区分 JavaScrip 和 ECMAScript
2015年 -- ES6 / ES2015，从 ES6 开始，使用年号作为版本号
2016年 -- ES2016
……

==ES 的语言标准不涉及语言的运行环境==；正是因为 ES 避免了运行环境，让 ES 有机会在各种环境中运行，使 ES 成为了一个通用编程语言。

通常把 ES 运行的环境称为**宿主环境**

## JavaScript 语言特性

1. JavaScript 是一种解释型语言
2. JavaScript 是一个弱类型语言；存放的数据类型可变。
3. 单线程：上一件事情没有做完，下一件事情必须等待（_同步现象_）
4. 异步：提高单线程的执行效率

> 编译型语言：C、C++ 等
>
> > 编译型语言会经过一个翻译的过程，负责编译的叫做编译器，翻译的结果叫做编译结果；优点：执行速度快；缺点：某个编译结果，难以适用于各种环境（跨平台障碍），部署繁琐。
>
> 解释型语言：JavaScript、Php 等
>
> > 解释型语言没有编译结果；优点：跨平台，部署简单；缺点：执行速度稍慢。
>
> 强类型语言：存放的数据类型不可变；优点：严谨；缺点：灵活性差，不易上手。
> 弱类型语言：存放的数据类型可变；优点：灵活，易上手；缺点：不严谨。
>
> > 通常将弱类型的解释型语言称为 _脚本语言_ 。

## JS 代码书写位置（_浏览器环境_）

1. 直接书写到页面中的 `<script>` 元素中
2. 写到外部 js 文件中，通过 `<script>` 元素的 `src` 属性引入
   - 有利于浏览器缓存
   - 有利于代码分离（_内容，样式，功能三者分离_），便于维护和阅读

::: tip

- 页面中可以存在多个 `<script>` 元素，执行顺序从上到下。
- 如果一个 `<script>` 元素使用 `src` 引入了外部代码，其内部书写的代码无效。

:::

> `<script>` 元素的 `type` 属性：用于指定代码语言，属性值为 MIME 类型。

## 基本语法规则

- JavaScript 语法部分必须是英文符号
- JavaScript 代码由多条语句构成，语句以 `;` 结尾（_不具有强制性_）
- JavaScript 代码从上到下同步执行
- JavaScript 语言大小写敏感

### 输入输出语句

> 所有的输出输出语句都不是 ES 标准。

#### 输出语句

- `document.write()` 用于将数据输出到页面
- `alert()` 用于将数据以弹窗形式显示到页面
- `console.log()` 用于将数据输出到控制台

#### 输入语句

- `prompt("请输入：")` 用于弹出输入框，获取用户输入的数据

### 代码注释

```js
// 单行注释

/*
多行注释
*/
```

## 数据和数据类型

数据：有用的信息
数据类型：数据的分类

> 直接书写的具体数据，称为**字面量**

### JS 中的数据类型

- 原始类型(_不可再细分的类型_)
  - `number` 数字类型
  - `string` 字符串类型
  - `boolean` 布尔类型
  - `undefined` 未定义类型
  - `null` 空类型
- 引用类型
  - `object` 对象
  - `function` 函数

#### 数字类型

表示小数、整数等；书写方式：直接书写

> 数字类型可以加上前缀，表示不同的进制；不加默认为十进制。
> 前缀 `0` 表示八进制；前缀 `0x` 表示十六进制；前缀 `0b` 表示二进制。

#### 字符串类型

表示一长串文本（_0 个或多个文本_）；书写方式：

1. 单引号包裹 `'some text'`
2. 双引号包裹 `"some text"`
3. 反引号包裹（_模板字符串_）`` `some text` ``

::: tip 在字符串中表示特殊字符
使用转义符 `\` 进行转义

- `\n` 换行符
- `\t` 制表符

:::

::: tip 使用长数字还是字符串？
如果按照数字阅读则使用数字类型；否则使用字符串类型。
:::

#### 布尔类型

表示真或假；书写方式：

- `true` 真
- `false` 假

#### undefined 类型

表示未定义；书写方式：`undefined`

#### null 类型

表示空值；书写方式：`null`

#### 对象

表示事物、东西等；对象是由多个基本类型或对象组合而成

属性：对象的成员

```js
{
  name: "小明",
  age: 18,
  isStudent: true,
  address: {
    country: 'china'，
    province: "jiangsu",
    city: "suzhou"
  }，
  girlFriend: null
}
```

### 判断数据的类型

#### typeof 操作符

```js
typeof 123 // number
typeof 'abc' // string
typeof true // boolean
typeof undefined // undefined
typeof null // object (JS 特性)
typeof {} // object
```

## 变量 variable

变量是一块**内存**空间，用于保存数据。

### 变量的使用

- 任何可以书写数据的地方都可以使用变量
- 不可以使用一个未声明的变量，
  - 使用 `typeof` 时除外

#### 声明（定义）变量

```js
var a // 声明了一个变量，目前变量为 undefined
console.log(a) // 输出变量的值 undefined
```

::: info 标识符的命名

在开发中，需要自行命名的位置，叫做标识符。

标识符的命名规则：

- 必须以字母、下划线或 `$` 符号开头
- 其他位置可以出现数字、字母、下划线或 `$` 符号
- 不可以与关键字、保留字重复

标识符命名命名规范：

- 变量名应做到望文知义
- 多个单词使用驼峰命名法

:::

#### 赋值

向变量的内存空间中存放数据

```js
a = 123 // 将 123 存放到变量 a 中
```

- JS 中变量的值和类型是可变的；变量可以被重新赋值，新的值会取代旧的值
- 声明和赋值可以合并（_语法糖_）
- 多个变量可以合并声明并赋值（_语法糖_）

```js
var a = 1
var b = a // 将变量 a 的数据**复制**到变量 b 中
b = 2 // 不影响变量 a 的数据（原始类型）
```

```js
var a = 1,
  b = 2,
  c = 3
```

> 语法糖只是方便书写或记忆，没有实质性改变。

#### 变量中存放对象

```js
var user = {
  account: 'abc',
  password: '123456',
  isVip: true
}
```

读取对象中的某个属性：`变量名.属性名`

::: important

- 当读取的属性不存在时，会返回 `undefined`
- 当读取的属性值不存在（_属性值为 `undefined` 或 `null`_）时，会报错

:::

通过变量更改对象的属性：

```js
var user = {
  account: 'abc',
  password: '123456',
  isVip: true
}
user.password = '654321' // 修改对象的属性值
```

> 当赋值的属性不存在时会添加属性

::: warning

```js
var user // user 为 undefined
user.name = 'shaw' // 会报错：原始类型 undefined 不可以添加属性
```

:::

删除属性：`delete 变量名.属性名`

> 实际编程时一般将属性值设为 `undefined` 以达到类似效果

#### 属性表达式

给属性属性赋值或读取属性时可以使用 `变量名["属性名"]`

属性表达式的使用场景：

- 属性名中包含特殊字符（_不是标准标识符_）
  - 实际上 JS 对属性名的命名并不严格，属性名可以为任意格式（_字符串_）
- 属性名为变量

```js
var prop = 'name' // 字符串类型
user[prop] = 'shaw' // 即 user.name = 'shaw'
```

::: important
属性名只能为**字符串**
如果不是字符串（如数字），宿主环境会自动转换为字符串

```js
var obj = {
  0: 0
}
obj[0] = '零'
obj['0'] = 'zero'
console.log(obj[0]) // 'zero'
```

:::

### 变量的声明提升

**JS 中存在变量声明提升**：所有变量的**声明**会自动提升到代码最顶部

> JS 中允许声明多个同名变量，**声明提升后会变为一个**

### 全局对象

JS 大部分宿主环境，都会提供一个特殊的对象，该对象可以在 JS 代码中直接访问，称为**全局对象**

- 浏览器全局对象：`window`; 表示整个窗口
- Node.js 全局对象：`global`; 表示当前 Node.js 进程

==开发者定义的所有变量实际上会成为全局对象的属性；但如果变量没有被赋值，则该变量不会覆盖全局对象中的同名属性==

> 全局对象中的所有属性可以直接使用，前面无需加上全局对象名
> 变量赋值时不写 var 关键字，相当于直接给 `window` 的某个属性赋值

```js
var console = 'abc'
console.log('hello world') // 报错：console 被覆盖为字符串
```

```js
var console
console.log('hello world') // 正常输出
console = 'abc' // 无法访问 console 变量，实际访问的是全局对象中的 console 属性
```

::: tip 特殊的 `name` 属性

```js
var name
console.log(name) // ''
console.log(typeof name) // string
// 因为 window 对象中含有属性 name
```

```js
var name = undefined
console.log(name) // 'undefined'
console.log(typeof name) // string
// name 属性会将任何赋值特殊处理为字符串
```

:::

### 引用类型变量的存储机制

- 原始类型的变量存放具体的内容到内存中

  ```js
  var a = '123'
  var b = a
  b = '456'
  console.log(a) // '123'
  console.log(b) // '456'
  ```

- 引用类型的变量会开辟一块新的内存空间，存放对象的内容，再将该**内存空间的地址**存放到变量中

  ```js
  var obj1 = { name: '123' }
  var obj2 = obj1
  obj2.name = '456'
  console.log(obj1.name) // '456'
  console.log(obj2.name) // '456'
  ```

  - `obj1` 指向某对象 / `obj1` 持有某对象的引用
  - `obj2` 指向同一对象 / `obj2` 也持有同一对象的引用

- ==出现对象字面量的位置，都一定会在内存中开辟一个新的空间==

  ```js
  var user1 = {
    name: '小明',
    age: 18,
    address: {
      // 新的空间
      country: 'china'
    }
  }
  var user2 = {
    name: '小红',
    age: 18,
    address: user1.address
  }
  user2.name = '小刚'
  user2.address.country = 'uk'
  console.log(user1.name, user2.name) // '小明' '小刚'
  console.log(user1.address.country, user2.address.country) // 'uk' 'uk'
  ```

  > 出现一对 `{}` 即为一块新的内存空间

  <!-- @include: @demo/JS-1-VariableSwitch.md#demo-->

#### JS 中的垃圾回收

JS 引擎中的垃圾回收器会定期的发现内存中无法访问到的对象，该对象称之为垃圾，JS 引擎会在合适的时间将其占用的内存空间释放。
