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