## 1.1数据类型
>javascript是弱类型语言或动态语言，这意味着不必提前申明变量类型，在程序运行过程中类型会被自动确定。

1.js中可以将数据类型分为简单数据类型和复杂数据类型两大类

>1. 简单数据类型（number sting null boolean undefined）
>2. 复杂数据类型 (object)
  
## 1.2全局作用域/局部作用域/作用域链
>通常来说，一段程序代码中所用到的名字并不总是有效和可用的，而限定合格名词的可用性代码范围就是这个名字的作用域，作用域的使用提高了程序逻辑的局部性增强了程序的可靠性，减少了名字的冲突。

1.代码名字在某个作用域内起作用和效果（目的是提高程序可靠性及命名冲突）

>1. 全局作用域（代码在整个script标签，或单独js文件作用和效果的作用域）

>2. 局部作用域（代码只在函数内部起作用和效果的作用域）
   
2.作用域链

>根据内部函数可以访问外部函数变量的原则，用链式查找决定哪些数据能被函数内部访问，就称之为作用域链。

## 1.3冒泡排序

## 1.4闭包
> 闭包（closure）指有权访问另一个函数作用域的函数  ----- Javascript高级程序设计

作用：延伸变量作用范围

## 1.5递归
> 如果一个函数在内部可以调用函数本身，那么这个函数就是递归函数

简单来说：函数内部自己调用自己，那么这个函数就是递归函数

#### 1.5.1利用递归从树中获取匹配对象

````javascript
    let orgTree=[
        {
            id:'test',
            name:'众康云医院',
            children:[
                {
                    id:'test2',
                    name:'心血管科室',
                }
            ]
        },
        {
            id:'dadad',
            name:'江北医院'
        }
    ];

    function getCurrentItem(id,tree,index=0){
        let item = tree[index];
        if(item.id==id){
            return item
        }else{
            if(item.children&&item.children.length){
                let find = getCurrentItem(id,item.children);
                if(find&&find.id==id){
                    return find
                }
            }
            return getCurrentItem(id,tree,++index)
        }
    }

    getCurrentItem('test2',orgTree)
````

#### 1.5.2利用递归实现深拷贝

````javascript
function deepCopy(oldObj){
    let newObj=null;
    if(Array.isArray(oldObj)){
        newObj=newObj||[];
    }else if(oldObj instanceof Object){
        newObj=newObj||{};
    }else{
        newObj=oldObj;
        return newObj
    }
    for(let key in oldObj){
        let item=oldObj[key];
        //1.判断是否数组
        //2.判断是否对象
        //3.是否简单数据
        if(Array.isArray(item)){
            newObj[key]=deepCopy(item);
        }else if(item instanceof Object){
            newObj[key]=deepCopy(item);
        }else{
            newObj[key] = item;
        }
    }
    return newObj
}
````

## 1.6 new关键字执行过程
>1.new 构造函数在内存中创建一个空对象
>2.执行构造函数里面的代码
>3.返回当前创建的对象

## 1.7 基本数据类型的一些注意点

````javascript
//1.字符串不可变
    //字符串的值不可变，虽然可以重新赋值，但是每一次赋值都会在内存中新开辟一块空间
//2.基本包装类型
    //let str = 'test';
    //console.log(str.length);
    //简单数据类型为什么会有length属性呢

    //let str='test';执行了申明操作

    let temp = new String('test');
    let str = temp;
    temp = null;
````

## 1.8 *纯函数思想
>纯函数是指不依赖，修改其作用域之外变量的函数

相同的输入有相同的输出，没有任何可观察的副作用，也不依赖外部环境状态