- clip-path(剪裁路径)
    + clip-path属性可以防止部分元素通过定义的剪切区域来显示，仅通过显示的特殊区域。剪切区域是被URL定义的路径代替行内或者外部svg，或者定义路线的方法例如circle().。clip-path属性代替了现在已经弃用的剪切 clip属性。
    + inset() : 定义一个矩形 。1
    + circle(定义圆)
    + ellipse(定义椭圆)
    + 基本图形：polygon(定义多边形)
    ```css
    /*inset()可以传入5个参数，分别对应top,right,bottom,left的裁剪位置,round radius（可选，圆角）*/
    .demo {
      clip-path: inset(2em 3em 2em 1em round 2em);
      }
    ```