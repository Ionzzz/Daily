#ES6
- let const
- 数值扩展
    + ES6 提供了二进制和八进制数值的新的写法，分别用前缀0b（或0B）和0o（或0O）表示。
        ```javascript
        0b111110111 === 503 // true
        0o767 === 503 // true
        Number('0b111')  // 7
        Number('0o10')  // 8
        ```
    + Number.isFinite()用来检查一个数值是否为有限的（finite）,Number.isNaN()用来检查一个值是否为NaN
        ```javascript
        Number.isFinite(15); // true
        Number.isFinite(0.8); // true
        Number.isFinite(NaN); // false
        Number.isFinite(Infinity); // false
        Number.isFinite(-Infinity); // false
        Number.isFinite('foo'); // false
        Number.isFinite('15'); // false
        Number.isFinite(true); // false
        Number.isNaN(NaN) // true
        Number.isNaN(15) // false
        Number.isNaN('15') // false
        Number.isNaN(true) // false
        Number.isNaN(9/NaN) // true
        Number.isNaN('true' / 0) // true
        Number.isNaN('true' / 'true') // true
        ```
        + 传统方法先调用Number()将非数值的值转为数值，再进行判断，而这两个新方法只对数值有效，Number.isFinite()对于非数值一律返回false, Number.isNaN()只有对于NaN才返回true，非NaN一律返回false。
          ```javascript
            isFinite(25) // true
            isFinite("25") // true
            Number.isFinite(25) // true
            Number.isFinite("25") // false
            
            isNaN(NaN) // true
            isNaN("NaN") // true
            Number.isNaN(NaN) // true
            Number.isNaN("NaN") // false
            Number.isNaN(1) // false
          ```
    + Number.parseInt(), Number.parseFloat() ES6 将全局方法parseInt()和parseFloat()，移植到Number对象上面，行为完全保持不变。这样做的目的，是逐步减少全局性方法，使得语言逐步模块化
    + Number.isInteger() 用来判断一个数值是否为整数。
    + Number.EPSILON ES6 在Number对象上面，新增一个极小的常量Number.EPSILON。根据规格，它表示 1 与大于 1 的最小浮点数之间的差。
        + Number.EPSILON实际上是 JavaScript 能够表示的最小精度。误差如果小于这个值，就可以认为已经没有意义了，即不存在误差了。 引入一个这么小的量的目的，在于为浮点数计算，设置一个误差范围。我们知道浮点数计算是不精确的。
        ```javascript
        Number.EPSILON === Math.pow(2, -52)
        // true
        Number.EPSILON
        // 2.220446049250313e-16
        Number.EPSILON.toFixed(20)
        // "0.00000000000000022204"
        function withinErrorMargin (left, right) {
        return Math.abs(left - right) < Number.EPSILON * Math.pow(2, 2);
        }
        0.1 + 0.2 === 0.3 // false
        withinErrorMargin(0.1 + 0.2, 0.3) // true
        1.1 + 1.3 === 2.4 // false
        withinErrorMargin(1.1 + 1.3, 2.4) // true
        ```
    + 安全整数和 Number.isSafeInteger() 能够准确表示的整数范围在-2^53到2^53之间（不含两个端点），超过这个范围，无法精确表示这个值。ES6 引入了Number.MAX_SAFE_INTEGER和Number.MIN_SAFE_INTEGER这两个常量，用来表示这个范围的上下限。
    + Math.trunc() 方法用于去除一个数的小数部分，返回整数部分。对于非数值，Math.trunc内部使用Number方法将其先转为数值。对于空值和无法截取整数的值，返回NaN。
        ```javascript
        Math.trunc(4.1) // 4
        Math.trunc('123.456') // 123
        Math.trunc(NaN);      // NaN
        Math.trunc('foo');    // NaN
        Math.trunc();         // NaN
        Math.trunc(undefined) // NaN
        ```
    + Math.sign() 方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。
        ```javascript
        Math.sign(-5) // -1
        Math.sign(5) // +1
        Math.sign(0) // +0
        Math.sign(-0) // -0
        Math.sign(NaN) // NaN
        ```