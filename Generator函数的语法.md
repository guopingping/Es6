Generator函数的语法

```
    状态机，封装了多个内部状态；
    遍历对象生成函数，返回一个遍历器对象，遍历函数内部的每一个状态；
    
    特征：
        function 关键字与函数名之间有一个星号；
        函数内部yield表达式，定义不同的内部状态；

    Generator函数的调用后，并不执行，返回的也不是函数运行结果，而是一个指向内部状态的只针对新
        value：当前内部状态的值；
        yield：当前表达式的值；
        done：遍历是否结束的布尔值，ture：结束；
    
1、    yield表达式：
        暂停标志；
        只有调用next方法，内部指针才会执行
        只能用在Generator函数里面；
        用在另一个表达式之中，必须放在圆括号里面；
        用在函数参数或赋值表达式的右边，可以不加括号；

        next：
            遇到yield表达式，暂停执行后面的操作，
            下次调用next方法，继续往下执行，
            直到遇到新的yield表达式，
            没有遇到yield，会一直执行到函数结束，直到return语句，
            没有return语句，返回对象value=undefined

        yield与return区别：
            遇到yield，函数暂停执行，return不具备位置记忆的功能；
            一个函数只能执行一个return语句，可以执行多次yield；
    
    Generator不用yield表达式，变成暂缓执行函数；

2、next方法的参数
    参数表达上一个yield表达式的返回值；
    第一次使用next方法，传递参数是无效的；用来启动遍历器对象；
    可以使用wrapper包一层，实现第一次调用next方法，就输入参数；

3、for...of循环
    可以自动遍历Iterator对象，无须调用next方法；

4、Generator.prototype.throw()
    抛出错误；
    在Generator内部体内捕获；
    Generator函数内部没有部署try...catch代码块，throw方法抛出的错误，会被外部try...catch代码块捕获；
    内外部都没有，程序报错；
    若要被内部捕获，必须执行过一次next方法；
    throw执行以后，会接着执行吓一跳yield表达式（next）；
    throw抛出的错误不会影响遍历器的状态；
    Generator执行过程中抛出错误，切没被内部捕获，就不会再执行下去了；继续执行，返回
        {
            value:undefined,
            done:true
        }

5、Generator.prototype.return()
    返回给定的值，终结遍历函数；
    return不提供参数，返回value：undefined
    try...finanlly：正在执行try代码，return会推迟到finally代码库执行完再执行；

6、next() throw() return()共同点
    next()：
        将yield表达式替换成一个值；

    throw():
        将yield表达式替换成一个throw语句；

    return()：
        将yield表达式替换成一个return语句；

7、yield*表达式
    在Generator函数内部调用另一个Generator函数，默认情况是没有效果的；
    需要yield*表达式；没有return语句；
    后面跟数组：
        加了*号返回是数组的遍历器对象，不加* 返回整个数组；
    取出嵌套数组的所有成员；
    遍历完全二叉树；

8、作为对象属性的Generator函数
    let obj={
        * f(){
            ...
        }
    }
    ===
    let obj={
        f:function* (){
            ...
        }
    }

9、Generator函数的this
    返回的总是一个遍历器对象，而不是this对象；
    不能跟new命令一起用，会报错；

    生成一个空对象，使用call()绑定Generator函数内部的this，就可以了
        function* F(){
            this.a=1
            yield this.b=2
        }
        var obj={}
        var f=F.call(obj)
        ===
        var f=F.call(F.prototype)

        f.next()   //Object {value:2,done:false}
        obj.a      //1

        ===
        将F改造成构造函数：
        function* gen(){
            this.a=1
            yield this.b=2
        }
        function F(){
            return gen.call(gen.prototype)
        }
        var f=new F()
        f.next()
        f.a

10、含义
    Generator与状态机：
            不用外部变量保存状态，本身就包含了状态信息；
    Generator与协程：
            协程是程序运行的方式，协作的线程 协作的函数 可以单线程也可以多线程实现；
    Generator与上下文：
            遇到yield命令，会暂时退出堆栈，但不消息，里面对象和变量会冻结在当前状态；
            执行next命令，重新加入调用栈，冻结的变量和对象回复执行；

11、应用
    异步操作的同步化表达；
    控制流管理；
    部署Iterator接口；
    作为数据结构；
    
```