- **TypeScript程序由以下几个部分组成**
    + 模块
    + 函数
    + 变量
    + 语句和表达式
    + 注释
    ```javascript
    //Runoob.ts 文件
    const hello : string = "hello world!"
    console.log(hello)
    ```
    + 以上代码可以通过tsc命令编译，使用node 可以执行文件
    ```shell
    tsc Runoob.ts
    node Runoob.js
    ```
- **空白和换行**
    + ts忽略程序中出现的空格、制表符和换行符
- **ts区分大小写**
- **ts注释** /* */ //
- **ts面向对象**
    ```javascript
    class Site { 
       name():void { 
          console.log("Runoob") 
       } 
    } 
    var obj = new Site(); 
    obj.name();
    ```
- Never类型
  + Never类型表示的是那些用不存在的值得类型。
  ```typescript
  let ne:never;
  ```
  + 总是会抛出异常或根本就不会有返回值的函数表达式或箭头函数表达式的返回值类型。
  + 变量也可能是Never类型，当它们被永不为真的类型保护所约束时。Never类型是任何类型的子类型，可以赋值给任何类型；没有类型是Never的子类型或可以赋值给Never类型（除了Never本身）。 即使 Any类型也不可以赋值给Never类型。
- Any类型
  + Any类型的变量可以被赋值为任意值。Any类型数据可以使用对应数据类型的方法或者属性。
  ```typescript
  let anyValue : any = 8;
  anyValue = "字符串数据";
  anyValue = true;
  ```