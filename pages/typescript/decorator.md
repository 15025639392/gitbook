### 装饰器（现在已经是es7的标准之一了）
> 装饰器是一种特殊类型的声明，它能够被附加到类声明，方法，属性，或参数上，可以修改类的行为
> * 通俗的讲装饰器就是一个方法，可以注入到类，方法，属性上来扩展类，属性，方法，参数的功能。
> * 常见的装饰器有 类，属性，方法，参数装饰器
> * 写法：普通装饰器（无法传参）， 装饰器工厂（可传参）

#### 类装饰器
>类装饰器表达式在运行时，被当作函数调用，类的构造函数是其唯一的参数
>如果装饰器返回一个值，它会使用提供的构造函数来替换类的声明

````typescript
// 修改属性和方法
function extension(target){
    target.protoytpe.dynamicAttr = '动态扩展的属性'
}
class Test{
    constructor(){

    }

    getDataSource(){
        console.log(this.dynamicAttr)
    }
}

//重载构造函数
function extension(target){
    return class extends target{
        api = 'rewrite';
        getDataSource(){
            console.log(this.api)
        }
    }
}
class Test{
    constructor(){
        this.api = 'test'
    }

    getDataSource(){
        console.log(this.dynamicAttr)
    }
}
````

#### 属性装饰器
>参数1:对于静态成员来说是类的构造函数，对于实例成员来说是类的原型对象
>参数2:成员名称

````typescript
function consoleAttr(params){
    return function(target,attr){
        console.log(target,attr)
    }
}
class Test{
    @consoleAttr
    public api = 'test';
    constructor(){
    }

    getDataSource(){
        console.log(this.dynamicAttr)
    }
}
````

#### 方法装饰器
>会被应用到方法的属性修饰符上，可以用来监视，修改或替换方法定义
>方法装饰器会在运行时自动传入3个参数：
> 1. 对于静态成员来说是类的构造函数，对于实例成员来说是类的原型对象
> 2. 成员名字
> 3. 成员属性描述符

````typescript
function consoleFuc(params){
    return function(target,name,desc){
        console.log(target,name,desc);

        //修改方法
        let oldFn = desc.value;
        desc.value = function(...args:any[]){
            oldFn.apply(this,args)
        }
    }
}
class Test{
    public api = 'test'
    constructor(){
    }
    @consoleFuc('test')
    getDataSource(){
        console.log(this.api)
    }
}
````

#### 参数装饰器
>可以为原型增加一些元数据，传参数如下：
> 1. 对于静态成员来说是类的构造函数，对于实例成员来说是类的原型对象
> 2. 方法名字
> 3. 参数在参数列表中的索引

````typescript
function consoleParams(params){
    return function(target,name,index){
        console.log(target,name,index);
    }
}
class Test{
    constructor(){
    }
    @consoleFuc('test')
    getDataSource(@consoleParams('test') id:any){
    }
}
````


