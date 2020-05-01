## TypeScript相对于javascript来说增加了以下几种类型

````typescript
//1.元组类型 (tuple)
//2.枚举类型 (enum)
//3.任意类型（any）
//4.never类型

//基本赋值方法
let arr:number[]=[1,2,3]
let arr:Array<number>=[1,2,3]

//元组
let arr:[string,number,boolean] = ['1',2,true]

//枚举
enum flag {
    succes:1,
    error:0
}
````