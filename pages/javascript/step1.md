## 1. 构造函数和原型
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
## 2. 截流和防抖

#### 2.1 截流
>触发高频事件后n秒内函数只会执行一次，如果n秒内高频事件再次被触发，则重新计算时间

原理：每次触发事件时都取消之前的延时调用方法

````
function debounce(fn){
    let timeout = null;
    return function(){
        clearTimeout(timeout);
        timeout = setTimeout(()=>{
            fn.apply(this,arguments);//根据this指向的相关规则  这里将this指回调用fn的上下文
        },300)
    }
}
````

#### 2.2 防抖
>高频事件触发，但在n秒内只会执行一次，所以节流会稀释函数的执行频率

原理：每次触发事件时都判断当前是否有等待执行的延时函数
  
````
function throttle(fn){
    let canRun = true;
    return function(){
        if(!canRun){
            return
        }
        canRun = false;
        setTimeout(()=>{
            fn.apply(this,arguments)
        },300)
    }
}
````

## 3. 深度优先遍历及广度优先遍历

#### 3.1 深度优先遍历
>从某个顶点v出发，首先访问该顶点然后依次从它的各个未被访问的邻接点出发深度优先搜索遍历图，直至图中所有和v有路径相通的顶点都被访问到。若此时尚有其他顶点未被访问到，则另选一个未被访问的顶点作起始点，重复上述过程，直至图中所有顶点都被访问到为止

![深度优先](../../images/deep.png)

````
let orgTree=[
    {
        id:'test',
        name:'众康云医院',
        children:[
            {
                id:'test2',
                name:'心血管科室',
                children:[{
                    id:'test3',
                    name:'test3'
                }]
            }
        ]
    },
    {
        id:'dadad',
        name:'江北医院'
    }
];
//方式1 递归方式
function deepTraversal(tree){
    if(!tree||!tree.length){
        return []
    }
    let arr = [];
    for(let i=0;i<tree.length;i++){
        let item = tree[i];
        let obj={
            id:item.id,
            name:item.name
        }
        arr.push(obj);
        if(item.children&&item.children.length){
            arr.push(...deepTraversal(item.children))
        }
    }
    return arr
}

//方式2 非递归方式
function deepTraversal(tree){
    if(!tree){
        return []
    }
    let arr = [];
    let stack = [];
    for(let i=0;i<tree.length;i++){
        let item = tree[i];
        stack.push(item);
        while(stack.length){
            let stackItem = stack.pop();
            arr.push({
                id:stackItem.id,
                name: stackItem.name
            });
            let children = stackItem.children||[];
            if(children.length){
                for(let c = children.length-1;c>=0;c--){
                    stack.push(children[i])
                }
            }
        }
    }
    return arr
}
````
#### 3.2
>从某顶点v出发，在访问了v之后依次访问v的各个未曾访问过的邻接点，然后分别从这些邻接点出发依次访问它们的邻接点，并使得“先被访问的顶点的邻接点先于后被访问的顶点的邻接点被访问，直至图中所有已被访问的顶点的邻接点都被访问到。 如果此时图中尚有顶点未被访问，则需要另选一个未曾被访问过的顶点作为新的起始点，重复上述过程，直至图中所有顶点都被访问到为止。

![广度优先](../../images/wide.png)

````
function wideTraversal(tree){
    let arr=[];
    let queue=[];
    queue.unshift(...tree);
    while(queue.length){
        let stackItem = stack.shift();
        arr.push({
            id:stackItem.id,
            name: stackItem.name
        });
        let children = stackItem.children||[];
        if(children.length){
            for(let c =0; c<children.length;c++){
                queue.push(children[i])
            }
        }
    }
    return arr;
}

````