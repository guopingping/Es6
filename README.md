ES6
========================================================
```
ECMAScript6是JavaScript语言的下一代标准
es6是JavaScript语言的国际标准
JavaScript是es6的实现

```
#### 1、let和const命令
```
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
    不允许重复声明：
        在相同作用域，不允许重复声明同一个变量
    块级作用域：
        外层作用域无法读取内层作用域的变量
        内层可以定义与外层同名变量
    块级作用域与函数声明：
        允许在块级作用域中声明函数，函数在作用域之外不可引用，es5不允许

3、const命令
    声明一个只读的常量，一旦声明，不可改变，必须立即初始化赋值
    作用域与let相同
    不存在变量提升
    存在暂时性死区
    不可重复声明
    本质：
        变量指向的内存地址所保存的数据不得改动

4、顶层对象的属性
    window：浏览器
    global：node
    window：
        var命令和function命令声明的全局变量，是顶层对象的属性
        let、const、class声明的全局变量，不属于顶层对象的属性
    global：
        this返回顶层对象
```
### 2、数组的扩展
```
    Math.max.apply(null,[1,2,3])
    =Math.max(...[1,2,3])
    =Math.max(1,2,3)
```
### 11、Set和Map数据结构
```
1、Set
    Set本身是一个构造函数，用来生成Set数据结构；
    不会添加重复的值，
    数组去除重复[...new Set(array)]
    Set判断两个值是否相等 类似于 ===
    两个空对象是不相等的
2、Map
    Hash结构
    键值对的数据结构


```
### 12、Proxy
```
    代理器，代理，
    在目标对象之前架设一层拦截
    用于修改某些操作的默认行为，属于“元编程”，对编程语言进行编程
    对外界的访问进行过滤和改写
    var proxy=new Proxy(target,handler)
        生成一个proxy实例，
        target：要拦截的目标对象；如果没有proxy，返回的就是这个对象
        handler：定制拦截的行为，被拦截的对象接下来的操作
    proxy实例的方法：
        get()：拦截某个属性的读取操作；可以继承
        set()：拦截某个属性的赋值操作；
        apply()：拦截函数的调用、call和apply操作
        has()：拦截hasProperty操作，判断对象是否有某个属性的时候
            has(target,属性名)
        construct()：拦截new命令
            construct(target,args,newTarget)
        deleteProperty()：拦截delete操作
        defineProperty()：拦截Object.defineProperty

```
### 14、Promise对象
```
1、
    容器，保存着某个未来才会结束的事情的结果（异步操作）
    特点：
        1）对象的状态不受外界的影响
            pending：进行中
            fulfilled：已成功
            rejected：已失败
            只有异步操作的结果，可以决定当前是哪一种状态
        2）一旦状态改变，就不会再变，任何时候都可以得到这个结果
        pending对象的状态改变，只有两种可能：
            pending变为fulfilled
            pending变为rejected
        一旦发生，就保持结果不变，已定型（resolved）
        （事件：则是一旦错过了它，再去监听，是得不到结果的）
    缺点：
        1）无法取消promise，一旦新建就会立即执行，无法中途取消
        2）如果不设置回调函数，promise内部抛出的错误，不会反应到外部
        3）当处于pending状态时，无法得知目前进展到哪一个阶段
2、基本用法
    promise(resolve,reject)
        resolve：将Promise对象的状态从“未完成”变为“成功”，在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；
        reject：将promise对象的状态从“未完成”变为“失败”，在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去；
    promise.then：指定resolved和rejected状态的回调函数；

```
### 15、async函数
```
    1）自带执行器
    2）更好的语义：
        async表示函数里有异步操作
        await表示紧跟在后面的表达式需要等待结果
    3）更广的适用性
    4）返回值是promise
        可以用then指定下一步操作
```
### 22、module的语法
```
export：用于规定模块的对外接口
import：用于输入其它模块提供的功能
export default：为模块指定默认输出

```