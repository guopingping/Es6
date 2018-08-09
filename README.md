ES6
========================================================
```
ECMAScript6是JavaScript语言的下一代标准
es6是JavaScript语言的国际标准
JavaScript是es6的实现

1、Babel转码器
    配置文件.babelrc
    命令行转码babel-cli:
        安装cnpm install -g babel-cli
    babel-node:支持es6的REPL环境
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

2、let
    只在所在的代码块有效；
    不存在变量提升，
    【var存在变量提升，即变量可以在声明之前使用，值为undefined】
    暂时性死区：
        如果区块中存在let或const，区块对变量形成了封闭作用域，不存在变量提升；
    

```