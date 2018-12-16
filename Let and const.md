
```
let const 命令

1）、Babel转码器
    .babelrc:
        Babel的配置文件。

    babel-cli:
        命令行转码.
        安装cnpm install -g babel-cli

    babel-node:
        支持es6的REPL环境

    babel-register:
        改写成require命令，为它加上钩子，使用require加载.js、.jsx、.es和.es6后缀名的文件，就会用babel进行转码。
        cnpm install --save-dev babel-register

    babel-core:
        调用API的babel的api进行转码
        cnpm install babel-core --save

    babel-polyfill：
        为当前环境提供一个垫片
        cnpm install babel-polyfill --save

    ESlint：
        用于静态检查代码的语法和风格
            cnpm install --save-dev eslint babel-eslint
        配置文件.eslintrc 
        package.json:加入scripts脚本lint

    Mocha:
        测试框架
        package.json:加入scripts脚本test


2）、let
    只在所在的代码块有效；
    不存在变量提升，
    【var存在变量提升，即变量可以在声明之前使用，值为undefined】

    暂时性死区：
        如果区块中存在let或const，区块对变量形成了封闭作用域，不存在变量提升；
        typeof：
            typeof x
            let x 报错

            typeof x //undefined

    不允许重复声明：
        在相同作用域，不允许重复声明同一个变量

    块级作用域：
        外层作用域无法读取内层作用域的变量
        内层可以定义与外层同名变量

    块级作用域与函数声明：
        允许在块级作用域中声明函数，函数在作用域之外不可引用，es5不允许

3）、const命令

    声明一个只读的常量，一旦声明，不可改变，必须立即初始化赋值
    作用域与let相同
    不存在变量提升
    存在暂时性死区
    不可重复声明
    本质：
        变量指向的内存地址所保存的数据不得改动;
    对象和对象属性冻结：Object.freeze()

ES6声明变量的六种方法：
    var,function,let,const,import,class

4）、顶层对象的属性

    window：浏览器
    global：node
    window：
        var命令和function命令声明的全局变量，是顶层对象的属性
        let、const、class声明的全局变量，不属于顶层对象的属性

    global：
        this返回顶层对象
    this局限性：
        1）全局环境中，this会返回顶层对象。node、es6模块，this返回当前模块
        2）函数里的this，指向顶层对象，严格模式下，返回undefined
        3）new Function('return this')(),返回全局对象，浏览器用了CSP(内容安全策略)，该方法无法使用

```