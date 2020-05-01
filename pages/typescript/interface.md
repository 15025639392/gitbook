### 接口的作用
>在面向对象的编程中接口是一种规范的定义，它定义了行为和动作的规范，在程序设计里面接口起到一种限制和规范的作用。接口定义了某一批类所要遵守的规范接口不关心这些类的内部状态数据，也不关心这些类里的实现细节，它只规定这批类里面必须提供某些方法提供这些方法的类就可以满足实际需要。

#### 属性接口
>对传入对象的约束

````typescript
interface limit={
    name:sting;
    age:number
}

function test(info:limit){
    console.log(info.name,info.age)
}

test({name:'ssss',age:18})
````

#### 函数类型接口
>对方法传入的参数，以及返回值进行约束

````typescript
interface encrypt{
    (key:string,value:string):string
}

let md5:encrypt=function(key:string,value:string){
    return key+value
}
````

#### 类类型接口
>对类的约束

````typescript
interface Person{
    name:sting;
    age:number;
    say(str:string):void;
}

class Man implements Person{
    name:'ldy';
    age: 24;
    constructor(name:tring){

    }
    say(str:string){
        console.log(`my name is:${this.name}`)
    }
}

let ldy = new Man('test');
ldy.say()
````

#### 接口扩展
>接口可以继承接口

````typescript
interface Animal{
    name:string
}

interface Person extends Amimal{
    work():void;
} 
````