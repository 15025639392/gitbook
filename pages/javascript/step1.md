## 1 构造函数和原型
#### 1.1 概述：
在典型的oop语言中，都存在类的概念，类就是对象的模板，对象就是类的实例，但是在es6（es2015之后的版本统称）之前，js中并没有引入类的概念

在es6之前，对象并不是通过类创建的，而是用一种称为构造函数的特殊函数来定义对象及特征
````
function Test(){
    this.name = 'test';
    this.abbr = 'test'
}
let obj = new Test();
````
#### 1.2 构造函数的成员
###### 1.2.1 静态成员
>在构造函数本身添加的成员（只能通过构造函数来访问）
````
Test.static = 'static';
console.log(obj.static);//undefined
````

###### 1.2.2 实例成员
>构造函数中通过this添加的成员（只能通过实例化的对象来访问）
````
console.log(obj.name);//test
````

#### 1.3 构造函数和原型
###### 1.3.1 构造函数的原型 prototype

>构造函数通过原型分配的函数hi所有对象所共享的 (一般用于存放公共的东西)
>javascript规定每一个构造函数都有一个prototype属性，指向另一个对象。这个对象的所有属性和方法都会被构造函数所拥有

````
Test.prototype.share = 'share';
console.log(obj.share);//share
console.log(obj.__proto__===Test.prototype)//true

````
###### 1.3.2 constructor
>对象原型（__proto__）和构造函数原型对象(prototype）里面都有一个constructor属性,被称之为构造函数，因为它指回构造函数本身（用于记录引用了哪个构造函数，可用于原型对象指回构造函数本身）

````
Test.prototype ={
    common:'common',
    constructor:Test//指回构造函数本身
}
````

###### 1.3.3 原型链
>多个原型组成链状结构的现象
1. 成员查找规则
   >按照原型链的规则查找
        首先查找对象本身
        然后查找它的原型
        然后查找Object的原型
        依此类推一直查找到Object为止
        
###### 1.3.4 继承
>es6之前没有提供extends继承，通过构造函数+原型对象模拟实现继承，被称为组合继承

````
function Father(name,age){
    this.name = name||'';
    this.age = age||''
}

Father.prototype.makeMony = function(){
    console.log(10000)
}

function Son(name,age){
    Father.call(this,name,age);//继承属性
}

Son.prototype = new Father();//继承原型
Son.prototype.constructor = Son;

let son = new Son('张三','25');
console.log(son.name,son.age)//张三，25
````