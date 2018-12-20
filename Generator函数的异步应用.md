Generator函数的异步应用

```
    "异步"：
        分段执行
    "同步"：
        连续执行
    ”回调函数"：
        把任务的第二段单独写在一个函数里面，等重新执行这个任务的时候，直接调用该函数，callback；
    Promise：
        允许将回调函数嵌套，改成链式调用；

1、Generator函数
    协程：
        多个线程相互协作，完成异步任务；
    
    协程的Generator函数实现：
        暂停执行
        异步任务的容器，异步需要暂停的地方，用yield语句注明；

    Generator函数的数据交互和错误处理：
        next():返回值得value属性，是Generator函数向外输出数据；
                接受参数，向内输入数据；
        
    异步任务的封装：
        代码简洁

2、Thunk函数
    自动执行Generator函数

    参数的求值策略：
        传名调用（只在执行时求值）：
            将参数放到一个临时函数之中，再将临时函数传入函数体，临时函数（Thunk函数）
        
3、Thunkify模块
    生产环境的转换器；
    npm install thunkify
    只允许回调函数执行一次；

4、Generator函数的流程管理
    Thunk函数用于Generator函数的自动流程管理；

    Thunk函数的自动流程管理

5、co模块
    Generator函数的自动执行；
    不用编写Generator函数的执行器；
    返回Promise对象
    （Think函数和Promise对象）== co
    前提条件：
        Generator函数的yield命令后面，只能是Thunk函数或Promise对象；
        数组或对象的成员全部都是Promise对象，也可以使用co；

    基于Promise对象的自动执行
        next()调用自身，实现自动执行
    
    co模块源码
        接受Generator函数作为参数，返回promise对象；

    处理并发的异步操作
        co支持并发的异步操作，允许某些操作同时进行，等都完成，才进行下一步；
        把并发的操作都放数组或对象里，跟在yield语句后面；
    
    实例：
        处理Stream
            提供Stream模式读写数据，一次处理数据的一部分，数据分成一块块依次处理，像”数据流“一样；
            Stream模式使用EventEmitter Api，释放三个事件：
                data事件：下一块数据块已经准备好了；
                end事件：整个”数据流“处理完了；
                error事件：发生错误；
            使用Promise.race()函数：
                    判断哪个事件最先发生，当data事件最先发生，才进入下一个数据块的处理
                    

```