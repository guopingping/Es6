Class的基本语法

```
    类的数据类型是函数，本身指向构造函数；

    Object.assign():
        可以一次向类添加多个方法；
    
    类内部所有定义的方法，都是不可枚举的；

1、constructor方法
    类的默认方法--构造方法
    new生成对象实例时，自动调用该方法；
    一个类必须有constructor方法；
        class Point{

        }
        ==
        class Point{
            constructor(){

            }
        }
    constructor() 默认返回实例对象（this）
    必须使用new调用；

    类的实例
        new
        实例的属性 都是定义在原型上（class）；
        类的所有实例共享一个原型对象；
            可以通过_proto_属性为类添加方法；

    取值函数getter和存值函数setter
    属性表达式
        类的属性名，可以采用表达式；
    Class表达式
        可以使用表达式的形式主义；
            const MyClass=class {
                ...
            }
    注意点
        严格模式
                默认严格模式
        不存在提升
                使用在前，定义在后，RefernceError
        name属性
                返回紧跟在class关键字后面的类名
        Generator方法
                *
        this指向
                类方法内部的this，默认指向类的实例
                不可单独拉出来，在外部用
                    解决：
                        在构造方法中绑定this
                        箭头函数；
                        使用Proxy，获取方法的时候，自动绑定this；

2、静态方法
    类相当于实例的原型，在类中定义的方法，都会被实例继承；
    方法前加上static，则不会被继承；通过类来调用--静态方法；
        class f={
            static g(){
                return '1'
            }
        }

        f.g()   //1

        var f1=new f()
        f1.g() //error  f1是f的实例
    如果静态方法包含this关键字，this指的是类，而不是实例；
    静态方法可以与非静态方法重名；
    父类的静态方法，可以被子类继承；
    静态方法也可以从super对象上调用的；

3、实例属性的新写法
    实例属性除在constructor()方法里面定义，也可以直接写在类的最顶层；

4、静态属性
    指Class本身的属性，Class.propName；
    不是实例对象this上的属性；

    ES6规定，class内部只有静态方法，没有静态属性；

5、私有方法和私有属性
    只能在类的内部访问的方法和属性，外部不能访问；ES6不支持
    方法：
        将私有方法移出模块；
        利用Symbol值得唯一性，将私有方法名字命名为一个Symbol值；

    #标识私有属性、私有方法；
    私有属性也可以设置getter和setter方法；
    私有属性不限于从this引用，只是在类的内部，实例也可以引用私有属性；
    静态的私有属性和私有方法，加static

6、new.target属性
    用在构造函数，返回new命令作用于的那个构造函数
    若构造函数不是通过new命令调用的，new.target返回undefined
    用来确定构造函数是怎么调用的；

    class内部调用new.target，返回当前的class；
    子类继承父类，new.target返回子类；
    
    函数外部使用new.target会报错；


```