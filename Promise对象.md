Promise对象

```
1、
    容器，保存着某个未来才会结束的事情的结果（异步操作）
    特点：
        1）对象的状态不受外界的影响
            pending：进行中
            fulfilled：已成功
            rejected：已失败
            只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态；

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

    promise新建后就会立即执行；
    调用resolve或reject并不会终结promise的参数函数执行；

3、Promise.prototype.then()
    链式then()

4、Promise.prototype.catch()
    指定发生错误时的回调函数；
    Promise状态已经变成resolved，再抛出错误是无效的；
    Promise对象的错误会一直向后传递，直到被捕获；
    一般不要在then方法里定义Reject状态的回调函数，总是用catch方法；

5、Promise.prototype.finally()
    不管promise对象最后状态如何，都会执行的操作；
    不接受任何参数；
    promise.finally(()=>{
        
    })
    ==
    promise.then(
        result =>{
            return result
        },
        error => {
            throw error;
        }
    )

6、Promise.all()
    const p = Promise.all([p1,p2,p3])

    接受一个数组作为参数；
    只有参数里面p1,p2,p3的状态都变成fulfilled，p才会变成fulfilled状态；
    返回值是一个数组，传给p的回调函数；
    Promise.all([]).then(function(res){

    }).catch(function(err){

    })

5、Promise.race()
    const p =Promise.race([p1,p2,p3])
        p1,p2,p3有一个实例率先改变状态，p的状态就跟着改变；

6、Promise.resolve()
    将现有对象转为Promise对象
    参数是一个Promise实例；
    参数是一个thenable对象：具有then方法的对象；
    参数不是具有then方法的对象，或根本不是对象；
    不带有任何参数；

7、Promise.reject(reason)
    实例状态rejected

8、应用
    加载图片；
    Gennrator函数与Promise的结合；

9、Promise.try()
    Promise.resolve().then(f)
    (async () => f())().then(...).catch(...)
    


```