# JavaScript

## JavaScript 起源

网景（Netscape Communication Corporation）于 1994 年推出第一款商用浏览器:网景（Netscape Navigator）。1995 年，网景公司决定在浏览器中加入一门语言，用于于用户交互效果，提高用户体验。该公司聘请 **Brendan Eich** 开发这门语言，10 天后 LiveScript 语言诞生，后来为了商业考虑 更名为 JavaScript（JS）。

> Java 与 JavaScript 的关系：周杰 ~ 周杰伦；葡萄 ~ 葡萄牙。

### 第一次浏览器大战

网景公司打算在浏览器中加入网络操作系统，触动了微软的利益；
1995 年，微软发布 IE 浏览器，开启第一次浏览器大战。
JS 推出之后，网景获得极大的竞争优质。
微软对 JS 语言进行反编译，并借鉴 JS 推出了 JScript、VBScript 两种语言，都可以在 IE 中执行。

第一次浏览器大战是标准之争。

1997 年，网景将 JavaScript 1.1 版本提交给 ECMA (欧洲计算机制造协会)，希望将其标准化。ECMA 收录了 JavaScript 并提交给 ISO，经修改成为第一个JavaScript 标准；称为 **ECMAScript**，检查 ES。

IE3 发布，并绑定 Windows 操作系统，网景市场份额不断下滑，于 1998 破产被收购。

### 第二次浏览器大战

微软推出 IE4、IE5、IE6（捆绑 Windows XP）后，微软决定解散浏览器团队。
Brendan Eich 在网景解散后，带领团队成立 Mozilla 基金会，并将网景浏览器和 JS 开源。
长时间内世界技术爱好者们对网景浏览器进行维护和修补。
2002 年 Mozilla 基金会推出 Firefox 浏览器。
2008 年 Google 推出 Chrome 浏览器；2010 年 Apple 推出 Safari 浏览器；2012 年 ASA 推出 Opera 浏览器。
Chrome 浏览器搭载了 JS 引擎 V8，可以将 JS 代码直接转换为字节码，理论上 JS 代码的执行速度大幅提升，已经接近汇编语言。从此 JS 具备了编写大型应用的能力，甚至服务器应用，**将 JS 的执行推向了一个新的台阶。**

> Ryan Dahl 直接利用 V8 引擎完成了 node.js，使 JS 语言在服务器端可以运行。
