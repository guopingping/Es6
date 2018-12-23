ArrayButter

```
1、ArrayBuffter对象
    存储二进制数据的一段内存，不能直接读写，只能通过视图，视图作用是以指定格式解读二进制数据；
    构造函数，分配一段可以存放数据的连续内存区域；

    ArrayBuffer.prototype.byteLength：
        所分配的内存区域的字节长度；
        需要检查是否分配成功
    ArrayBuffer.prototype.slice():
        允许将内存区域的一部分，拷贝生成一个新的ArrayBuffer对象；
        第一个参数：拷贝开始的字节序号；
        第二个参数：拷贝截止的字节序号；
    ArrayBuffer.isView():
        表示参数是否为ArrayBuffer的视图实例

2、TypedArray视图
    同一个数据类型

3、DataView视图
    数组成员可以是不同的数据类型

4、二进制数组的应用
    AJAX
    Canvas
    WebSocket
    Fetch API
    File API
    SharedArrayBuffer
    Atomics对象
    
```