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
    



        
```