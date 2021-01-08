- **DOM 和 BOM**
    + Document Object Model 文档对象模型，就是把【文档】当做一个【对象】来看待。--document 对象
        + 各个组件（component）可以通过object.attribute访问
        + 一个DOM有一个根对象，这个对象通常是document
    + Browser Object Model 浏览器对象模型，就是把【浏览器】当做一个【对象】来看待。--window 对象
        + BOM除了可以访问文档中的组件之外，还可以访问浏览器组件，比如 navigator（导航条）、history（历史记录）等等
- **输入URL 浏览器都发生了什么**
    + 完善前端知识体系: <https://segmentfault.com/a/1190000013662126>
- **AJAX**
    1. **创建XMLHttpRequest异步对象**
        ```javascript
        var xhr;
        if (window.XMLHttpRequest)
        {
            // code for IE7+, Firefox, Chrome, Opera, Safari
            //主流
            xhr=new XMLHttpRequest();
        }
        else
        {
            // code for IE6, IE5
            xhr=new ActiveXObject("Microsoft.XMLHTTP");
        }
        ``` 
    2. **设置回调函数**
        ```javascript
        xhr.onreadystatechange = callback
        ```
    3. **使用open方法与服务器建立连接**
       ```javascript
        // get 方式
        xhr.open("get", "api/text", true)
        
        // post 方式发送数据 需要设置请求头
        xhr.open("post", "api/text", true)
        xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded")
        ```
    4. **向服务器发送数据**
       ```javascript
        // get 不需要传递参数
        xhr.send(null)
        
        // post 需要传递参数
        xhr.send("name=jay&age=18")
        ```
    5. **在回调函数中针对不同的响应状态进行处理**
        ```javascript
        function callback() {
        // 判断异步对象的状态
        if(xhr.readyState == 4) {
        // 判断交互是否成功
        if(xhr.status == 200) {
        // 获取服务器响应的数据
        var res = xhr.responseText
        // 解析数据
        res = JSON.parse(res)
        }
        }
        }
        ```
    6. **补充**：
        - onreadystatechange: 存储函数（或函数名），每当 readyState 属性改变时，就会调用该函数。
        - readyState：存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。
            + 0: 请求未初始化
            + 1: 服务器连接已建立
            + 2: 请求已接收
            + 3: 请求处理中
            + 4: 请求已完成，且响应已就绪
        - status： 	200: “OK”
- **重排与重绘**
    + 重绘（repaint或redraw）：当盒子的位置、大小以及其他属性，例如颜色、字体大小等都确定下来之后，浏览器便把这些原色都按照各自的特性绘制一遍，将内容呈现在页面上。重绘是指一个元素外观的改变所触发的浏览器行为，浏览器会根据元素的新属性重新绘制，使元素呈现新的外观。
触发重绘的条件：改变元素外观属性。如：color，background-color等。
    + 重排（重构/回流/reflow）：当渲染树中的一部分(或全部)因为元素的规模尺寸，布局，隐藏等改变而需要重新构建, 这就称为回流(reflow)。每个页面至少需要一次回流，就是在页面第一次加载的时候。
    + 重绘和重排的关系：在回流的时候，浏览器会使渲染树中受到影响的部分失效，并重新构造这部分渲染树，完成回流后，浏览器会重新绘制受影响的部分到屏幕中，该过程称为重绘。
- **CSS动画 JS动画**
    + css实现动画：animation transition transform 
    + js实现动画: setInterval setTimeout requestAnimationFrame
    + JS动画
        + JS动画控制能力强，可以再动画播放过程中对动画进行控制：开始、暂停、回放、终止、取消
        + 动画效果比css3丰富，比如曲线运动，冲击闪烁，视差滚动效果
        + css3剧透兼容问题，JS大多没有兼容问题
        + JS在浏览器的主线程中运行，而主线程中还会有其他运行的js脚本、样式计算、布局、绘制任务等，对于其干扰线程可能会出现阻塞，从而造成丢帧的情况
        + 代码复杂度高于CSS动画
        + **总结** : 如果动画只是简单的状态切换，不需要中间过程的控制，在这种情况下，css动画是优选方案。它会把动画逻辑放在样式文件里，而不后悔让你的页面充斥js库。而如果涉及很复杂的富客户端界面或者开发一个有着复杂UI状态的APP，那么要是用js动画。
    + css动画
        + 集中所有DOM，一次重绘重排，刷新频率和浏览器刷新频率相同
        + 代码简单，方便调优
        + 不可见元素不参与重排，节约CPU
        + 可以使用硬件加速GPU(translateZ(0))
        + 对过程无法把控，无进度报告，无回调函数，代码冗长
    + css动画和js动画的差异
        + 代码复杂度， js动画代码相对复杂一些
        + 动画运行时，对动画的控制程度上， css不能添加事件，js可以
        + 动画性能上，js动画多了一个js解析过程，性能不如css动画好
- **事件冒泡**
    + 当一个元素收到事件(仅仅指事件event)的时候 会把他接收到的事件传给自己的父级，一直到window。
    + 取消事件冒泡的两种方式： 
        - 标准的W3C 方式：e.stopPropagation();这里的stopPropagation是标准的事件对象的一个方法，调用即可 
        - 非标准的IE方式:ev.cancelBubble=true;  这里的cancelBubble是 IE事件对象的属性，设为true就可以了
- **AMD CMD**
    + AMD依赖前置
    + CMD依赖就近
    + CommonJS/AMD/CMD <https://www.cnblogs.com/chenguangliang/p/5856701.html>
    + Webpack的AMD插件开发运行机制 <https://blog.csdn.net/weixin_34110749/article/details/88037827?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromBaidu-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromBaidu-1.control>
    + Webpack打包原理 <https://segmentfault.com/a/1190000021494964?utm_source=tag-newest>
- **闭包**
    + **概念** 内层函数能够访问外层函数作用域的变量
    + **缺点** 引起内存泄漏（释放内存）
    + **作用**
        + 使用闭包修正打印值
        + 实现私有变量，实现JS模块化应用
        + 保持变量与函数活性，可延迟回收和执行
- **JavaScript严格模式(use strict)**
    + 使用 use strict 指令，是指定代码在严格条件下执行(Internet Explorer 10 +、 Firefox 4+ Chrome 13+、 Safari 5.1+、 Opera 12+)
    + "use strict" 指令在 JavaScript 1.8.5 (ECMAScript5) 中新增，它不是一条语句，但是是一个字面量表达式，在javascript旧版本会被忽略
    + 消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为。
        * 消除代码运行的一些不安全之处，保证代码运行的安全
        * 提高编译效率，增加运行速度
        * 为未来新版本的javascript做好铺垫
    + **不允许使用未声明的变量**
    + **不允许删除变量或者对象**
    + **不允许删除函数**
    + **不允许变量重名**
    + **不允许使用八进制** var x = 010; //正常模式下，整数的第一位如果是0，表示这是八进制数，比如0100等于十进制的64。严格模式禁止这种表示法，整数第一位为0，将报错。
    + **不允许使用转义符**
    + **不允许对只读属性赋值**
    + **不允许对一个getter方法读取的属性进行赋值**
    + **不允许删除一个不允许删除的属性**
    + **变量名不能用“eval”、“arguments”字符串**
    + **作用域eval()创建的变量将不能被调用**
    + **禁止this关键字指向全局对象**
    + **新增保留关键字**
        * implements\interface\let\package\private\protected\public\static\yield
- **call、apply、bind**
    + call()/apply()/bind()用来改变this指向
    + bind与apply、call最大的区别是：bind不会立即被调用、而是返回一个新函数，称为绑定函数，其内的this指向为创建它时传入bind的第一个参数、而传入bind的第二个及以后的参数作为原函数的参数调用原函数、
    ```javascript
        var obj = {};
        function test() {
            console.log(this === obj);
        }
        test(); //false
        var testObj = test.bind(obj);
        testObj();  //true
    ```
    + apply和call是为了改变某个函数运行时的上下文存在的（就是为了改变函数内部this的指向）。apply和call的调用返回函数执行结果。
    + 使用apply和call方法，那么this指向他们的第一个参数，apply的第二个参数是一个参数数组，call的第二个参数及以后的参数是数组里的元素。
    ```javascript
    var name = '小王', age = 17;
    var obj = {
        name: '小张',
        objAge: this.objAge, 
        myFun:function (fm,t) {
            console.log(this.name + "年龄" + this.objAge,  "来自" + fm + "去往" + t);
        }
    }
    var db = {
        name: '皇马',
        age: 99
    }
    obj.myFun.call(db,'成都','上海');　　　 // 皇马 年龄 99  来自 成都去往上海
    obj.myFun.apply(db,['成都','上海']);      // 皇马 年龄 99  来自 成都去往上海  
    obj.myFun.bind(db,'成都','上海')();       // 皇马 年龄 99  来自 成都去往上海
    obj.myFun.bind(db,['成都','上海'])();　　 // 皇马 年龄 99  来自 成都, 上海去往 undefined
    ```
    + call 、bind 、 apply 这三个函数的第一个参数都是 this 的指向对象，第二个参数差别就来了：
        * call 的参数是直接放进去的，第二第三第 n 个参数全都用逗号分隔，直接放到后面 obj.myFun.call(db,'成都', ... ,'string' )。
        * apply 的所有参数都必须放在一个数组里面传进去 obj.myFun.apply(db,['成都', ..., 'string' ])。
        * bind 除了返回是函数以外，它 的参数和 call 一样。
        * 当然，三者的参数不限定是 string 类型，允许是各种类型，包括函数 、 object 等等。
- **关于this**
    + 当一个函数调用时，会创建一个活动记录（执行上下文）。这个上下文包括函数在哪里被调用（调用栈）、函数调用方法、传入的参数等信息。this的指向取决于函数调用位置而非函数定义位置。
    + 绑定规则
        - 有function关键字的函数
            * 默认绑定：在没有其他规则时，this遵循的默认绑定
            * 非严格模式下：全局作用域中函数被调用时，该函数词法作用域内的this指向全局对象，浏览器环境中指向window，node环境中指向global。
            * 严格模式时，函数调用时词法作用域内的this指向undefined，报TypeError错误
        - 隐式绑定
            * 当函数在某个上下文中调用时，函数this指向该上下文对象，如var bar = obj.fn()
        - 显式绑定
            * 避免隐式绑定造成的误导，可以使用函数自有方法call或者apply或者bind来显示明确具体函数调用时内部this的指向，如 var bar = fn.call(obj1)
        - new 绑定
            * 指通过new构造函数生成实例对象，此时构造函数内部的this就指向这个实例对象。
        - ES6中的箭头函数不遵循前述四种绑定规则，而是根据词法作用域来决定this绑定。即箭头函数会继承外层函数调用时的this绑定，并且不会管这个this绑定到底是什么。这点其实在ES5中已有实现，为var self = this;
- **ES5 与 ES6继承区别**
    + ES5以函数形式定义类, 以prototype来实现继承
    + ES6以class形式定义类, 以extend形式继承