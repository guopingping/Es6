ES6
========================================================
```
ECMAScript6是JavaScript语言的下一代标准
es6是JavaScript语言的国际标准
JavaScript是es6的实现

```

```
1、let const 命令

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
```
2、变量的解析赋值

1)、数组的解构赋值
    解构(Destructuring)：
                        从数组和对象中提取值，对变量进行赋值;
    解构不成功，变量等于undefined;
    不完全解构；
    等号右边不是数组，会报错;
    set结构，可以使用数组的解构赋值；
    只要某种数据结构具有Iterator接口，都可以采用数组形式的解构赋值；

2)、默认值
    允许指定默认值;
    只有当一个数组成员严格等于undefined，默认值才会生效;
        eg:
            let [x,y='b']=['a',undefined]   //x='a' y='b'
            let [x=1]=[null]   //x=null

    默认值是表达式时，是惰性求值，只有用到的时候才会求值；
        eg:
            function f(){
                console.log('111')
            }
            let [x=f()]=[1];  //x能取到值，f不会执行

    默认值可以引用解构赋值的其它变量，但该变量必须已经声明；
        eg:
            let [x=1,y=x]=[1,2] //x=1,y=2
            let [x=y,y=1]=[] //x ReferenceError:y is not defined

3)、对象的解构赋值
    对象的解构与数组解构的区别：
        数组的元素是按照次序排列的，变量值由位置决定；
        对象的属性是无序的，变量必须与属性同名；
    默认值生效的条件：
        对象的属性值严格等于undefined
    解构失败，变量=undefined

4)、字符串的解构赋值
    字符串被转换成数组

5)、数值和布尔值的解构赋值
       解构赋值的原则是：只要等号右边的值不是对象或数组，就将其转为对象

6)、函数参数的解构赋值
    函数参数的解构也可以使用默认值
    undefined就会触发函数参数的默认值

7)、 圆括号问题
    只要有可能导致解构歧义的，就不得在模式中使用圆括号
    不能使用圆括号的情况：
        1）变量声明语句
        2）函数参数
        3）赋值语句的模式
    可以使用圆括号的情况：
        1）赋值语句的非模式部分

8)、用途
    1）交换变量的值
        [x,y]=[y,x]
    2）从函数返回多个值
    3）函数参数的定义
    4）提取JSON数据
    5）函数参数的默认值
    6）遍历Map结构
        const map=new Map()
        map.set('a','1')
        for(let [key,value] of map){
            console.log(key+'is'+value)
        }
        //a is 1
        //获取键名key 获取键值value
    7）输入模块的指定方法
        const {}=require()

```
```
3、字符串的扩展

1)、codePointAt()：处理4个字节储存的字符，返回一个字符的码点(十进制)，参数是字符在字符串中的位置；
    转化为十六进制 .toString(16)

2)、String.fromCodePoint：从码点返回对应的字符

3)、字符串的遍历器接口
    for...of

4)、includes()、startsWith()、endsWith()
    第二个参数，开始搜索的位置；

    includes():布尔值，是否包含；
    startsWith():布尔值，是否在源字符串的头部；
    endsWith()：布尔值，是否在源字符串的尾部；

5)、repeat()：
    返回一个新字符串，将原字符串重复n次
    参数是负数或Infinity--报错
    负数---0
    小数---取整
    NaN---0
    字符串---转化为数字

6)、 padStart()：头部补全
    padEnd()：尾部补全
        第一个参数：字符串的最小长度
        第二个参数：补全的字符串

7）、matchAll()
    返回一个正则表达式在当前字符串的所有匹配；

8）、模板字符串
    反引号`标识；
    `：多行字符串；
    模板字符串中需要引用反引号，前面需要用反斜杠转义；
    表示多行字符串，所有的空格和缩进都会被保留在输出之中
    标签模板：
        紧跟在函数后面 alert '123'=alert(123)

```

```
4、正则的扩展

1）、RegExp构造函数
    var regex=new RegExp('xyz','i')=var regex=/xyz/i

2)、字符串的正则方法
    match()、replace()、search()、split()

3）、u修饰符
    u：Unicode模式，用来处理大于\uFFFF的Unicode字符；
    .：除了换行符以外的任意单个字符
    
```
```
5、数值的扩展

1）、Number
    将0b和0o前缀字符串数值转为十进制；
2）、Number.isFinite() Number.isNaN()
    Number.isFinite():检查一个数值是否为有限的。非数值，都返回false；
    Number.isNaN():检查一个值是否为NaN。 参数非NaN，都返回false；
    Number.parseInt()
    Number.parseFloat()
    Number.isInteger():判断一个数值是否为整数。
3）、Math对象的扩展
    Math.trunc():
        去除一个数的小数部分，返回整数部分；
        空值和无法截取整数，返回NaN；
    Math.sign():
        判断一个数是正数、负数、还是0 ；
        正数，返回+1；
        负数，返回-1；
        0，返回0
        -0，返回-0
        其他值，返回NaN
    Math.cbrt():
        计算一个数的立方根；
    Math.imul()：
        返回两个数以32位带符号整数形式相乘的结果；
    Math.hypot():
        返回所有参数的平方和的平方根；

```
```
6、函数的扩展

1）、函数参数的默认值
    参数变量是默认声明的，不能用let const再次声明；
    函数不能有同名参数；
2）、参数默认值的位置
    非尾部的参数设置默认值，这个参数不可以省略。
    传入undefined，触发参数等于默认值，null无此效果；
3）、函数length属性：
    返回没有指定默认值的参数个数；
    默认值的参数不是尾参数，length属性也不再计入后面的参数；
4）、作用域
    设置了参数的默认值，函数在声明初始化时，参数会形成一个单独的作用域。
5）、作用：
    可以指定某个参数不能省略；
    设定为undefined，标识可以省略；

6）、rest参数
    ...变量名
    多余的参数放在一个数组中；
    rest参数后不能再有其他参数；
    length属性，不包括rest参数；

7）、严格模式
    不能使用的情况：
        函数参数用了默认值；
        解构赋值；
        扩展运算符
    可以：
        在全局设置use strict
        包含在一个无参数的方法中

8）、name属性
    函数的name属性，返回函数名；

9）、箭头函数
    =>
    不需要参数或需要多个参数，使用（）代表参数部分
    注意：
        函数体内的this对象，即定义时所在的对象，而不是使用时所在的对象；
        不可当做构造函数，即不可用new命令
        不可用arguments对象，该对象在函数体内不存在，可用rest参数代替
        不可用yield命令，即不能用作Generator函数

    不适用场合：
        定义函数的方法，且该方法内部包括this；
        需要动态this的时候；

10）、双冒号运算符
    ：：
    左边是一个对象，右边是一个函数；
    左边为空，右边为对象的方法，即该方法绑定该对象

11）、尾调用
    函数的最后一步操作是 调用另一个函数；
    尾调用优化：
        只保留内层函数的调用帧
    尾递归：
        尾调用自身。
        不会发生栈溢出，相对节省内存；
    柯里化：
        将多参数的函数转换成单参数的形式

    尾调用优化，只在严格模式下开启，正常模式无效，正常模式下，函数内部两个变量
        func.argument:返回调用时函数的参数；
        func.caller：返回调用当前参数的那个函数；
    尾调用优化发生时，函数的调用栈会改写，两个变量会失真。

```

```
7、数组的扩展
    扩展运算符：
        
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