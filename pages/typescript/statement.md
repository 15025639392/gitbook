#### TS允许声明联合类型, 允许使用type关键字声明类型别名

````ts
let test:string[]|string|number|boolean;
test="type";
test=["test"];
test=100;
test=false;

test=function(){};//error


type newArr=Array<string|number|boolean>
type testData=number;
type callBack=()=>void;
````

#### 类型守护
1. JavaScript 一个常用的方式就是使用 typeof 或者 instanceof 来在运行时检查一个表达式的类型。TypeScript 现在可在 if 区域块中理解这种情况。
2. ts实现了这种错误检查机制

````ts
let x:string='test';
if(typeof x==="string"){
    console.log(x.splice(3,1));//string没有splice方法
}
````