
```
Set和Map数据结构

1)、Set
    Set本身是一个构造函数，用来生成Set数据结构；
    不会添加重复的值，
    数组去除重复[...new Set(array)]
    不进行类型转换；
    Set判断两个值是否相等 类似于 ===
    两个空对象是不相等的；

    add():添加某个值；
    delete()
    has()
    clear()

    遍历操作：
        keys()、values()、entries()、forEach()
    
    Set实现交集、并集、差集   

2)、Map
    键值对的集合；
    Map可以接受一个数组作为参数；
    Hash结构;
    键值对的数据结构;
    与内存地址绑定的，内存地址不一样，视为两个键；
    Map 严格相等

    size属性：成员总数；
    set(key,value)；
    get(key):读取键值；
    has(key)
    delete(key)
    clear()

遍历方法：
        keys()、values()、entries()、forEach()

转化为数组：
    ...

数组转为对象：
    将数组中插入Map构造函数，就可以转为Map；

Map转为对象：
    无损的转为对象；

对象转为Map：
Map转JSON：  
JSON转为Map：

```