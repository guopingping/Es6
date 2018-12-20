Iterator和for...of循环

```
1、Iterator(遍历器)
    一种接口，为各种不同的数据结构提供统一的访问机制；

    作用：
        为各种数据结构，提供一个统一的、简便的访问接口；
        数据结构的成员能够按照某种次序排列；
        创造了新的遍历 for...of；
    
    next():返回一个对象
            value done

    Symbol.iterator

    原生具备Interator接口的数据结构：
        Array、Map、Set、String、TypedArray、函数的arguments对象、NodeList对象
    
2、调用Iterator接口的场合
    1)、解构赋值
    2）、扩展运算符
    3）、yield*
    4）、其他场合
            for...of
            Array.from()
            Map() Set() WeakMap() WeakSet() 
            Promise.all()
            Promise.racez()

4、字符串的Iterator接口
5、遍历器对象的return()、throw()
    return :for...of提前退出
            对象完成遍历之前，需要清理或释放资源
6、for...of循环
    数组、Set、Map、类似数组的对象(arguments对象、DOM NodeList对象)、后文Generator对象、字符串
    获取键值value（for...in获取键名)

7、与其他遍历语法的比较
    数组内置的forEach：
        无法中途跳出forEach循环,break return 都无效
        for...in(of)则可以

```