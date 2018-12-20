async函数

```
    是Generator函数的语法糖；
    将Generator函数的 星号 * 替换成 async 
                    yield 替换成 await
    
    返回一个Promise对象，可以用then方法添加回调函数。
    
1、
    1）内置执行器：
        不需要调用next
    2）更好的语义：
        async表示函数里有异步操作
        await表示紧跟在后面的表达式需要等待结果
    3）更广的适用性：
    4）返回值是promise：
        可以用then指定下一步操作
    
    async可以看作多个异步操作，包装成一个Promise对象；
    await 即是内部then命令的语法糖；

2、基本用法
    一旦遇到await就返回，等异步操作完成，再执行函数体后面的语句；

3、语法
    返回Promise对象；
    async函数内部return语句返回的值，会成为then方法回调函数的参数；
    返回错误，Promise对象变为reject状态，被catch接收到；

    Promise对象的状态变化
        必须等到所有await命令后面的promise对象执行完，状态才会改变，除非遇到return或抛出错误；

    多个await后面的Promise对象变为reject状态，整个async都会中断执行；
    要不被中断，将第一个await放到try...catch里，不管第一个是否成功，第二个都会执行；

    错误处理：
        即Promise对象被reject；
        防止出错，多个await，放到try...catch结构中；

    使用注意点：
        放到try...catch中；
        多个await后面的异步操作，若不存在继发关系，最好同时触发,缩短执行时间；
            let [f,g]=await Promise.all([
                f()
                g()
            ])
        await只能用在async函数之中；
        esm模块加载器支持顶层await，即可以不放到async函数里面，直接使用；
        async函数可以保留运行堆栈；

4、async函数的实现原理
    将Generator函数和自动执行器，包装在一个函数里。

5、异步遍历器的接口
    Symbol.asyncIterator
    next()可以连续调用

    for await...of
        遍历异步的Iterator接口；
        try...catch捕捉错误；
        也可以用于同步遍历器；

    异步Generator函数
        异步遍历器对象；
        == async函数与Generator函数的结合；
            异步遍历器的设计目的之一，就是Generator函数处理同步操作和异步操作时，使用同一套接口；
        内部可以同时使用await和yield，await用于将外部操作产生的值输入函数内部
                                    yield用于将函数内部的值输出；
        与for await...of结合起来使用；
        返回的是 一个异步的Iterator对象；

        一系列按照顺序执行的异步操作--async函数；
        一系列产生相同数据结构的异步操作---异步Generator函数；

6、yield* 语句
    可以跟一个异步遍历器


```