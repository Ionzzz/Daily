#ES6
- **let const**
- **正则扩展**
    + RegExp 构造函数
- **Symbol**
    + ES6 引入了一种新的原始数据类型Symbol，表示独一无二的值。它是 JavaScript 语言的第七种数据类型，前六种是：undefined、null、布尔值（Boolean）、字符串（String）、数值（Number）、对象（Object）。
    + 注意，Symbol函数前不能使用new命令，否则会报错。这是因为生成的 Symbol 是一个原始类型的值，不是对象。也就是说，由于 Symbol 值不是对象，所以不能添加属性。基本上，它是一种类似于字符串的数据类型。
- **Set和Map数据结构**
    + ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。
    + WeakSet 结构与 Set 类似，也是不重复的值的集合。但是，它与 Set 有两个区别。 首先，WeakSet 的成员只能是对象，而不能是其他类型的值。
    + Map类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。也就是说，Object 结构提供了“字符串—值”的对应，Map 结构提供了“值—值”的对应，是一种更完善的 Hash 结构实现。如果你需要“键值对”的数据结构，Map 比 Object 更合适。
- **Proxy**
    + Proxy 用于修改某些操作的默认行为，等同于在语言层面做出修改，所以属于一种“元编程”（meta programming），即对编程语言进行编程。
    + Proxy 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。Proxy 这个词的原意是代理，用在这里表示由它来“代理”某些操作，可以译为“代理器”。
- **Reflect**
    + （1）将Object对象的一些明显属于语言内部的方法（比如Object.defineProperty），放到Reflect对象上。现阶段，某些方法同时在Object和Reflect对象上部署，未来的新方法将只部署在Reflect对象上。也就是说，从Reflect对象上可以拿到语言内部的方法。
    + （2）修改某些Object方法的返回结果，让其变得更合理。比如，Object.defineProperty(obj, name, desc)在无法定义属性时，会抛出一个错误，而Reflect.defineProperty(obj, name, desc)则会返回false。
- **Promise**
    + Promise 是异步编程的一种解决方案，比传统的解决方案——回调函数和事件——更合理和更强大。它由社区最早提出和实现，ES6 将其写进了语言标准，统一了用法，原生提供了Promise对象。
- **Module**
    + ES6 模块的设计思想是尽量的静态化，使得编译时就能确定模块的依赖关系，以及输入和输出的变量。CommonJS 和 AMD 模块，都只能在运行时确定这些东西。比如，CommonJS 模块就是对象，输入时必须查找对象属性。
    + ES6 的模块自动采用严格模式，不管你有没有在模块头部加上"use strict";
- **同步遍历器**
- **异步遍历器**
- **数值扩展**
    + ES6 提供了二进制和八进制数值的新的写法，分别用前缀0b（或0B）和0o（或0O）表示。
    + Number.isFinite()用来检查一个数值是否为有限的（finite）,Number.isNaN()用来检查一个值是否为NaN
        + 传统方法先调用Number()将非数值的值转为数值，再进行判断，而这两个新方法只对数值有效，Number.isFinite()对于非数值一律返回false, Number.isNaN()只有对于NaN才返回true，非NaN一律返回false。
    + Number.parseInt(), Number.parseFloat() ES6 将全局方法parseInt()和parseFloat()，移植到Number对象上面，行为完全保持不变。这样做的目的，是逐步减少全局性方法，使得语言逐步模块化
    + Number.isInteger() 用来判断一个数值是否为整数。
    + Number.EPSILON ES6 在Number对象上面，新增一个极小的常量Number.EPSILON。根据规格，它表示 1 与大于 1 的最小浮点数之间的差。
        + Number.EPSILON实际上是 JavaScript 能够表示的最小精度。误差如果小于这个值，就可以认为已经没有意义了，即不存在误差了。 引入一个这么小的量的目的，在于为浮点数计算，设置一个误差范围。我们知道浮点数计算是不精确的。
    + 安全整数和 Number.isSafeInteger() 能够准确表示的整数范围在-2^53到2^53之间（不含两个端点），超过这个范围，无法精确表示这个值。ES6 引入了Number.MAX_SAFE_INTEGER和Number.MIN_SAFE_INTEGER这两个常量，用来表示这个范围的上下限。
    + Math.trunc() 方法用于去除一个数的小数部分，返回整数部分。对于非数值，Math.trunc内部使用Number方法将其先转为数值。对于空值和无法截取整数的值，返回NaN。
    + Math.sign() 方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。
    + Math.cbrt() 用于计算一个数的立方根。
    + Math.clz32() 方法将参数转为 32 位无符号整数的形式，然后返回这个 32 位值里面有多少个前导 0。
    + Math.imul() 方法返回两个数以 32 位带符号整数形式相乘的结果，返回的也是一个 32 位的带符号整数。
    + Math.fround() 返回一个数的32位单精度浮点数形式。Math.hypot()方法返回所有参数的平方和的平方根。
    + Math.expm1()、Math.log1p()、Math.log10()、Math.log2()
    + Math.sinh(x)、Math.cosh(x)、Math.tanh(x)
    + **指数运算符** ES2016 新增了一个指数运算符（**）。这个运算符的一个特点是右结合，而不是常见的左结合。多个指数运算符连用时，是从最右边开始计算的。
    + 引入BigInt类型。没有位数的限制，任何位数的整数都可以精确表示。