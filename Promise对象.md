```
14、Promise对象

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