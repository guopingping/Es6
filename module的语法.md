module的语法

```
    ES6模块编译时加载，使得静态分析称为可能；

1、严格模式
    es6自动采用严格模式；
    严格模式主要有以下限制：
        变量必须声明后再使用；
        函数的参数不能有同名属性；
        不能使用with语句；
        不能对只读属性赋值；
        不能使用前缀0表示八进制数；
        不能删除不可删除的属性；
        不能删除delete prop，只能删除delete global[prop]；
        eval不会在他的外层作用域引入变量；
        eval和arguments不能被重新赋值；
        arguments不会自动反映函数参数的变化；
        不能使用arguments.callee；
        不能使用arguments.caller；
        禁止this指向全局对象；
        不能使用fn.caller和fn.arguments获取函数调用的堆栈；
        增加了保留字：protected/static/interface等；
    
2、export命令

    export：用于规定模块的对外接口
    import：用于输入其它模块提供的功能
    export default：为模块指定默认输出

    export：
        输出变量
        输出函数或类
        as 重命名输出的变量

3、import命令
    as重命名变量
    输入的变量只读的；
    import...from... from指定模块文件的位置
    具有提升效果，会提升到整个模块的头部，首先执行；
    不能使用变量和表达式；

4、模块的整体加载
    * 指定一个对象；
    不允许运行时改变

5、export default命令
    为模块指定默认输出；

6、export和import的复合写法
7、模块的继承
8、跨模块常量
9、import（）
    动态加载；
    异步加载；

    require：
        运行时加载模块，同步加载；

    适用场合：
        按需加载
        条件加载
        动态的模块路径
        
    

```