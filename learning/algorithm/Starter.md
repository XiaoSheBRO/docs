# 入门

## 时间与空间复杂度

数据结构和算法解决是`如何让计算机更快时间、更省空间的解决问题`
复杂度描述的是算法执行时间（或占用空间）与数据规模的增长关系

### 大`O`表示法

算法的执行时间与每**行**代码的执行次数成正比，总时间 = O(_f_(n))

`O(1)`常数阶 < `O(log(n))`对数阶 < `O(n)`线性阶 < `O(n^2)` 平方阶 < `O(n^3)`(立方阶) < `O(2^n)` (指数阶)

> n 往往表示数据的规模

### 时间复杂度

代码执行时间随数据规模增长的**增长趋势**

> 判断一个算法所编程序运行时间的多少，并不是通过程序在计算机上运行所消耗的时间来度量。原因很简单，一方面，解决一个问题的算法可能有很多种，一一实现的工作量无疑是巨大的，得不偿失；另一方面，不同计算机的软、硬件环境不同，程序的运行时间很可能会受影响。

如何预估一个算法所编程序的运行时间呢？很简单，先分别计算程序中每条语句的执行次数，然后用总的执行次数间接表示程序的运行时间。

> 表示一个算法所编程序运行时间的多少，用的并不是准确值（事实上也无法得出），而是根据合理方法得到的预估值

```js
for (let i = 0; i < n; i++) {
  //从 0 到 n，执行 n+1 次
  a++ //从 0 到 n-1，执行 n 次
}
```

> for 循环从 i 的值为 0 一直逐增至 n（注意，循环退出的时候 i 值为 n），因此 for 循环语句执行了 n+1 次；
> 循环内部仅有一条语句，a++ 从 i 的值为 0 就开始执行，i 的值每增 1 该语句就执行一次，一直到 i 的值为 n-1，因此，a++ 语句一共执行了 n 次。
> 因此，整段代码中所有语句共执行了 (n+1)+n 次，即 2n+1 次。

**数据结构中，每条语句的执行次数，又被称为该语句的频度**，整段代码的总执行次数，即整段代码的频度。

```js
for (let i = 0; i < n; i++) {
  // n+1
  for (let j = 0; j < m; j++) {
    // n*(m+1)
    num++ // n*m
  }
}
```

> 计算此段程序的频度为：(n+1)+n\*(m+1)+n\*m，简化后得 2\*n\*m+2\*n+1。
> 值得一提的是，不同程序的运行时间，更多场景中比较的是在最坏条件下程序的运行时间，最坏条件即指的是当 n、m 都为无限大时此段程序的运行时> 间。
> 当 n、m 都无限大时，我们完全就可以认为 n==m。在此基础上，2\*n\*m+2\*n+1 又可以简化为 2\*n^2^+2\*n+1
> 类似 2n+1、2\*n^2^+2\*n+1 这样的频度，还可以再简化吗？答案是肯定的。
> 以 2n+1 为例，当 n 无限大时，是否在 2n 的基础上再做 +1 操作，并无关紧要，因为 2n 和 2n+1 当 n 无限大时，它们的值是无限接近的。甚至于> 我们还可以认为，当 n 无限大时，是否给 n 乘 2，也是无关紧要的，因为 n 是无限大，2\*n 也是无限大。
> 再以无限大的思想来简化 2\*n^2^+2\*n+1。当 n 无限大的：
> 首先，常数 1 是可以忽略不计的；
> 其次，对于指数级的 2\*n^2^来说，是否在其基础上加 2\*n，并无关紧要；
> 甚至于，对于是否给 n^2^  乘 2，也可以忽略。
> 因此，最终频度 2\*n^2^+2\*n+1 可以简化为 n^2^ 。

在数据结构中，频度表达式可以这样简化：

- 去掉频度表达式中，所有的加法常数式子。
- 如果表达式有多项含有无限大变量的式子，只保留一个拥有指数最高的变量的式子。
- 如果最高项存在系数，且不为 1，直接去掉系数。

> 事实上，对于一个算法（或者一段程序）来说，其最简频度往往就是最深层次的循环结构中某一条语句的执行次数。例如 2n+1 最简为 n，实际上就是 a++ 语句的执行次数；同样 2n^2^+2n+1 简化为   n^2^，实际上就是最内层循环中 num++ 语句的执行次数。

- 量级最大法则：忽略常量、低阶和系数

> 只关注循环执行次数最多的一段代码，执行次数最多的是 for 循环及里面的代码，执行了 n 次，所以时间复杂度为 O(n)

- 加法法则：总复杂度等于量级最大的那段代码的复杂度，比如一段代码中有单循环和多重循环，那么取多重循环的复杂度
- 乘法法则：嵌套代码的复杂度等于嵌套内外代码复杂度的乘积
- 多个规模求加法：比如方法有两个参数控制两个循环的次数，那么这时就取二者复杂度相加

### 空间复杂度

算法的存储空间与数据规模之间的增长关系

每一个算法所编写的程序，运行过程中都需要占用大小不等的存储空间，包括

- 程序代码本身所占用的存储空间
- 程序中如果需要输入输出数据的存储空间
- 程序在运行过程中临时申请的存储空间

如果程序所占用的存储空间和输入值无关，则该程序的空间复杂度就为 O(1)；
反之，如果有关，则需要进一步判断它们之间的关系：如果随着输入值 n 的增大，程序申请的临时空间成线性增长，则程序的空间复杂度用 O(n) 表示；如果随着输入值 n 的增大，程序申请的临时空间成 n^2^ 关系增长，则程序的空间复杂度用 O(n^2^) 表示...
