### 概述
1. 正向：表示接下来的字符必须被匹配。
2. 先行：表示匹配模式右侧的字符，表示一个方向。
3. 零宽：表示必须满足匹配条件，但是并不会真正被匹配。
4. 负向：表示接下来的字符必须不被匹配。
5. 后行：表示匹配模式左侧的字符，表示一个方向。

#### 先行零宽断言
##### 1.正向先行零宽断言:

````js
let str="antzone is good";
console.log(/ant(?=z)/g.test(str));
````

##### 2.负向先行零宽断言

````js
let str="antzone is good";
console.log(/ant(?!z)/g.test(str));
````

#### 后行零宽断言
##### 1.正向后行零宽断言:

````js
let str="antzone is good";
console.log(/(?=z)one/g.test(str));
````

##### 2.负向后行零宽断言

````js
let str="antzone is good";
console.log(/(?!z)ant/g.test(str));
````