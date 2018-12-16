```
Proxy

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

    this:
        Proxy代理的情况下，目标对象内部的this关键字会指向Proxy代理。

    web服务的客户端

```