原文地址: [Daily-Interview-Question](https://github.com/Advanced-Frontend/Daily-Interview-Question)
---

#### 第 1 题：写 React / Vue 项目时为什么要在列表组件中写 key，其作用是什么？

公司：滴滴、饿了么

解析：[第 1 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/1)


#### 第 2 题：`['1', '2', '3'].map(parseInt)` what & why ?

解析：[第 2 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/4)




#### 第 3 题：什么是防抖和节流？有什么区别？如何实现？

公司：挖财

解析：[第 3 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/5)




#### 第 4 题：介绍下 Set、Map、WeakSet 和 WeakMap 的区别？

解析：[第 4 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/6)




#### 第 5 题：介绍下深度优先遍历和广度优先遍历，如何实现？（已解答）
解答：[深度优先遍历与广度优先遍历](./step1.md)

解析：[第 5 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/9)




#### 第 6 题：请分别用深度优先思想和广度优先思想实现一个拷贝函数？

解析：[第 6 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/10)




#### 第 7 题：ES5/ES6 的继承除了写法以外还有什么区别？

解析：[第 7 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/20)




#### 第 8 题：setTimeout、Promise、Async/Await 的区别

解析：[第 8 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/33)




#### 第 9 题：Async/Await 如何通过同步的方式实现异步

公司：头条、微医

解析：[第 9 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/156)




#### 第 10 题：异步笔试题

> 请写出下面代码的运行结果

```js
async function async1() {
    console.log('async1 start');
    await async2();
    console.log('async1 end');
}
async function async2() {
    console.log('async2');
}
console.log('script start');
setTimeout(function() {
    console.log('setTimeout');
}, 0)
async1();
new Promise(function(resolve) {
    console.log('promise1');
    resolve();
}).then(function() {
    console.log('promise2');
});
console.log('script end');
```

解析：[第 10 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/7)

公司：头条




#### 第 11 题：算法手写题

> 已知如下数组：
>
> var arr = [ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
>
> 编写一个程序将数组扁平化去并除其中重复部分数据，最终得到一个升序且不重复的数组

公司：携程

解析：[第 11 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/8)




#### 第 12 题：JS 异步解决方案的发展历程以及优缺点。

公司：滴滴、挖财、微医、海康

解析：[第 12 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/11)




#### 第 13 题：Promise 构造函数是同步执行还是异步执行，那么 then 方法呢？

公司：微医

解析：[第 13 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/19)




#### 第 14 题：情人节福利题，如何实现一个 new （已掌握）

公司：兑吧

解答：

````
function _new(fn, ...arg) {
    const obj = Object.create(fn.prototype);
    const ret = fn.apply(obj, arg);
    return ret instanceof Object ? ret : obj;//非构造函数兼容
}

function Doc(name){
       this.name=name
}

Doc.prototype.test="fuck";

let obj= _new(Doc,'yan');
console.log(obj);
obj instanceof Doc// true
````

解析：[第 14 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/12)




#### 第 15 题：简单讲解一下http2的多路复用

公司：网易

解析：[第 15 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/14)




#### 第 16 题：谈谈你对TCP三次握手和四次挥手的理解

解析：[第 16 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/15)




#### 第 17 题：A、B 机器正常连接后，B 机器突然重启，问 A 此时处于 TCP 什么状态

> 如果A 与 B 建立了正常连接后，从未相互发过数据，这个时候 B 突然机器重启，问 A 此时处于 TCP 什么状态？如何消除服务器程序中的这个状态？（超纲题，了解即可）

解析：[第 17 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/21)




#### 第 18 题：React 中 setState 什么时候是同步的，什么时候是异步的？

公司：微医

解析：[第 18 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/17)




#### 第 19 题：React setState 笔试题，下面的代码输出什么？

```js
class Example extends React.Component {
  constructor() {
    super();
    this.state = {
      val: 0
    };
  }
  
  componentDidMount() {
    this.setState({val: this.state.val + 1});
    console.log(this.state.val);    // 第 1 次 log

    this.setState({val: this.state.val + 1});
    console.log(this.state.val);    // 第 2 次 log

    setTimeout(() => {
      this.setState({val: this.state.val + 1});
      console.log(this.state.val);  // 第 3 次 log

      this.setState({val: this.state.val + 1});
      console.log(this.state.val);  // 第 4 次 log
    }, 0);
  }

  render() {
    return null;
  }
};
```

解析：[第 19 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/18)




#### 第 20 题：介绍下 npm 模块安装机制，为什么输入 npm install 就可以自动安装对应的模块？

解析：[第 20 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/22)




#### 第 21 题：有以下 3 个判断数组的方法，请分别介绍它们之间的区别和优劣

> Object.prototype.toString.call() 、 instanceof 以及 Array.isArray() 

解析：[第 21 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/23)




#### 第 22 题：介绍下重绘和回流（Repaint & Reflow），以及如何进行优化

解析：[第 22 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/24)




#### 第 23 题：介绍下观察者模式和订阅-发布模式的区别，各自适用于什么场景

解析：[第 23 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/25)




#### 第 24 题：聊聊 Redux 和 Vuex 的设计思想

解析：[第 24 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/45)




#### 第 25 题：说说浏览器和 Node 事件循环的区别

解析：[第 25 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/26)
 

#### 第 26 题：介绍模块化发展历程

可从IIFE、AMD、CMD、CommonJS、UMD、webpack(require.ensure)、ES Module、`<script type="module">` 这几个角度考虑。

解析：[第 26 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/28)




#### 第 27 题：全局作用域中，用 const 和 let 声明的变量不在 window 上，那到底在哪里？如何去获取？。

解析：[第 27 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/30)




#### 第 28 题：cookie 和 token 都存放在 header 中，为什么不会劫持 token？

解析：[第 28 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/31)




#### 第 29 题：聊聊 Vue 的双向数据绑定，Model 如何改变 View，View 又是如何改变 Model 的

解析：[第 29 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/34)




#### 第 30 题：两个数组合并成一个数组

请把两个数组 ['A1', 'A2', 'B1', 'B2', 'C1', 'C2', 'D1', 'D2'] 和 ['A', 'B', 'C', 'D']，合并为 ['A1', 'A2', 'A', 'B1', 'B2', 'B', 'C1', 'C2', 'C', 'D1', 'D2', 'D']。

解析： [第 30 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/39)




#### 第 31 题：改造下面的代码，使之输出0 - 9，写出你能想到的所有解法。

```js
for (var i = 0; i< 10; i++){
	setTimeout(() => {
		console.log(i);
    }, 1000)
}
```

解析：[第 31 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/43)




#### 第 32 题：Virtual DOM 真的比操作原生 DOM 快吗？谈谈你的想法。

解析：[第 32 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/47)




#### 第 33 题：下面的代码打印什么内容，为什么？

```js
var b = 10;
(function b(){
    b = 20;
    console.log(b); 
})();
```

解析：[第 33 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/48)




#### 第 34 题：简单改造下面的代码，使之分别打印 10 和 20。

```js
var b = 10;
(function b(){
    b = 20;
    console.log(b); 
})();
```

解析：[第 34 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/51)




#### 第 35 题：浏览器缓存读取规则

可以分成 Service Worker、Memory Cache、Disk Cache 和 Push Cache，那请求的时候 from memory cache 和 from disk cache 的依据是什么，哪些数据什么时候存放在 Memory Cache 和 Disk Cache中？

解析：[第 35 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/53)




#### 第 36 题：使用迭代的方式实现 flatten 函数。

解析：[第 36 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/54)




#### 第 37 题：为什么 Vuex 的 mutation 和 Redux 的 reducer 中不能做异步操作？

解析：[第 37 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/65)




#### 第 38 题：下面代码中 a 在什么情况下会打印 1？

```js
var a = ?;
if(a == 1 && a == 2 && a == 3){
 	console.log(1);
}
```

解析：[第 38 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/57)

公司：京东




#### 第 39 题：介绍下 BFC 及其应用。

解析：[第 39 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/59)




#### 第 40 题：在 Vue 中，子组件为何不可以修改父组件传递的 Prop

如果修改了，Vue 是如何监控到属性的修改并给出警告的。

解析：[第 40 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/60)




#### 第 41 题：下面代码输出什么

```js
var a = 10;
(function () {
    console.log(a)
    a = 5
    console.log(window.a)
    var a = 20;
    console.log(a)
})()
```

解析：[第 41题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/61)




#### 第 42 题：实现一个 sleep 函数

比如 sleep(1000) 意味着等待1000毫秒，可从 Promise、Generator、Async/Await 等角度实现

解析：[第 42 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/63)




#### 第 43 题：使用 sort() 对数组 [3, 15, 8, 29, 102, 22] 进行排序，输出结果

解析：[第 43 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/66)




#### 第 44 题：介绍 HTTPS 握手过程

解析：[第 44 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/70)




#### 第 45 题：HTTPS 握手过程中，客户端如何验证证书的合法性

解析：[第 45 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/74)




#### 第 46 题：输出以下代码执行的结果并解释为什么

```js
var obj = {
    '2': 3,
    '3': 4,
    'length': 2,
    'splice': Array.prototype.splice,
    'push': Array.prototype.push
}
obj.push(1)
obj.push(2)
console.log(obj)
```

解析：[第 46 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/76)




#### 第 47 题：双向绑定和 vuex 是否冲突

解析：[第 47 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/81)




#### 第 48 题：call 和 apply 的区别是什么，哪个性能更好一些

解析：[第 48 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/84)




#### 第 49 题：为什么通常在发送数据埋点请求的时候使用的是 1x1 像素的透明 gif 图片？

解析：[第 49 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/87)




#### 第 50 题：实现 (5).add(3).minus(2) 功能。

> 例： 5 + 3 - 2，结果为 6

解析：[第 50 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/88)

公司：百度




#### 第 51 题：Vue 的响应式原理中 Object.defineProperty 有什么缺陷？

为什么在 Vue3.0 采用了 Proxy，抛弃了 Object.defineProperty？

解析：[第 51 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/90)




#### 第 52 题：怎么让一个 div 水平垂直居中

解析：[第 52 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/92)




#### 第 53 题：输出以下代码的执行结果并解释为什么

```js
var a = {n: 1};
var b = a;
a.x = a = {n: 2};

console.log(a.x) 	
console.log(b.x)
```

解析：[第 53 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/93)




#### 第 54 题：冒泡排序如何实现，时间复杂度是多少， 还可以如何改进？

解析：[第 54 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/94)




#### 第 55 题：某公司 1 到 12 月份的销售额存在一个对象里面

如下：{1:222, 2:123, 5:888}，请把数据处理为如下结构：[222, 123, null, null, 888, null, null, null, null, null, null, null]。

解析：[第 55 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/96)




#### 第 56 题：要求设计 LazyMan 类，实现以下功能。 

```js
LazyMan('Tony');
// Hi I am Tony

LazyMan('Tony').sleep(10).eat('lunch');
// Hi I am Tony
// 等待了10秒...
// I am eating lunch

LazyMan('Tony').eat('lunch').sleep(10).eat('dinner');
// Hi I am Tony
// I am eating lunch
// 等待了10秒...
// I am eating diner

LazyMan('Tony').eat('lunch').eat('dinner').sleepFirst(5).sleep(10).eat('junk food');
// Hi I am Tony
// 等待了5秒...
// I am eating lunch
// I am eating dinner
// 等待了10秒...
// I am eating junk food
```

解析：[第 56 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/98)




#### 第 57 题：分析比较 opacity: 0、visibility: hidden、display: none 优劣和适用场景。 

解析：[第 57 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/100)




#### 第 58 题：箭头函数与普通函数（function）的区别是什么？构造函数（function）可以使用 new 生成实例，那么箭头函数可以吗？为什么？

解析：[第 58 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/101)




#### 第 59 题：给定两个数组，写一个方法来计算它们的交集。

> 例如：给定 nums1 = [1, 2, 2, 1]，nums2 = [2, 2]，返回 [2, 2]。

解析：[第 59 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/102)




#### 第 60 题：已知如下代码，如何修改才能让图片宽度为 300px ？注意下面代码不可修改。

> `<img src="1.jpg" style="width:480px!important;”>`

解析：[第 60 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/105)




#### 第 61 题：介绍下如何实现 token 加密

解析：[第 61 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/106)




#### 第 62 题：redux 为什么要把 reducer 设计成纯函数

解析：[第 62 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/107)




#### 第 63 题：如何设计实现无缝轮播

解析：[第 63 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/108)




#### 第 64 题：模拟实现一个 Promise.finally

解析：[第 64 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/109)




#### 第 65 题： `a.b.c.d` 和 `a['b']['c']['d']`，哪个性能更高？

解析：[第 65 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/111)




#### 第 66 题：ES6 代码转成 ES5 代码的实现思路是什么

解析：[第 66 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/112)




#### 第 67 题：数组编程题

随机生成一个长度为 10 的整数类型的数组，例如 `[2, 10, 3, 4, 5, 11, 10, 11, 20]`，将其排列成一个新数组，要求新数组形式如下，例如 `[[2, 3, 4, 5], [10, 11], [20]]`。

解析：[第 67 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/113)




#### 第 68 题： 如何解决移动端 Retina 屏 1px 像素问题

解析：[第 68 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/115)




#### 第 69 题： 如何把一个字符串的大小写取反（大写变小写小写变大写），例如 ’AbC' 变成 'aBc' 。

解析：[第 69 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/116)




#### 第 70 题： 介绍下 webpack 热更新原理，是如何做到在不刷新浏览器的前提下更新页面的

解析：[第 70 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/118)




#### 第 71 题： 实现一个字符串匹配算法，从长度为 n 的字符串 S 中，查找是否存在字符串 T，T 的长度是 m，若存在返回所在位置。

解析：[第 71 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/119)




#### 第 72 题： 为什么普通 `for` 循环的性能远远高于 `forEach` 的性能，请解释其中的原因。

![image-20190512225510941](https://ws2.sinaimg.cn/large/006tNc79gy1g2yxbg4ta8j31gh0u048h.jpg)



解析：[第 72 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/121)




#### 第 73 题： 介绍下 BFC、IFC、GFC 和 FFC

解析：[第 73 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/122)




#### 第 74 题： 使用 JavaScript Proxy 实现简单的数据绑定

解析：[第 74 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/123)




#### 第 75 题：数组里面有10万个数据，取第一个元素和第10万个元素的时间相差多少

解析：[第 75 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/124)




#### 第 76 题：输出以下代码运行结果

```js
// example 1
var a={}, b='123', c=123;  
a[b]='b';
a[c]='c';  
console.log(a[b]);

---------------------
// example 2
var a={}, b=Symbol('123'), c=Symbol('123');  
a[b]='b';
a[c]='c';  
console.log(a[b]);

---------------------
// example 3
var a={}, b={key:'123'}, c={key:'456'};  
a[b]='b';
a[c]='c';  
console.log(a[b]);
```

解析：[第 76 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/125)




#### 第 77 题：算法题「旋转数组」

> 给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。

示例 1：

```js
输入: [1, 2, 3, 4, 5, 6, 7] 和 k = 3
输出: [5, 6, 7, 1, 2, 3, 4]
解释:
向右旋转 1 步: [7, 1, 2, 3, 4, 5, 6]
向右旋转 2 步: [6, 7, 1, 2, 3, 4, 5]
向右旋转 3 步: [5, 6, 7, 1, 2, 3, 4]
```

示例 2：

```js
输入: [-1, -100, 3, 99] 和 k = 2
输出: [3, 99, -1, -100]
解释: 
向右旋转 1 步: [99, -1, -100, 3]
向右旋转 2 步: [3, 99, -1, -100]
```

解析：[第 77 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/126)




#### 第 78 题：Vue 的父组件和子组件生命周期钩子执行顺序是什么

解析：[第 78 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/128)




#### 第 79 题：input 搜索如何防抖，如何处理中文输入

解析：[第 79 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/129)




#### 第 80 题：介绍下 Promise.all 使用、原理实现及错误处理

解析：[第 80 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/130)




#### 第 81 题：打印出 1 - 10000 之间的所有对称数

> 例如：121、1331 等

解析：[第 81 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/131)




#### 第 82 题：周一算法题之「移动零」

> 给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。
>
> 示例:
>
> ```
> 输入: [0,1,0,3,12]
> 输出: [1,3,12,0,0]
> ```
>
> 说明:
>
> 1. 必须在原数组上操作，不能拷贝额外的数组。
>
> 1. 尽量减少操作次数。

解析：[第 82 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/132)




#### 第 83 题：var、let 和 const 区别的实现原理是什么

解析：[第 83 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/133)




#### 第 84 题：请实现一个 add 函数，满足以下功能。

> ```js
> add(1); 			// 1
> add(1)(2);  	// 3
> add(1)(2)(3)；// 6
> add(1)(2, 3); // 6
> add(1, 2)(3); // 6
> add(1, 2, 3); // 6
> ```

解析：[第 84 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/134)




#### 第 85 题：react-router 里的 `<Link>` 标签和 `<a>` 标签有什么区别

> 如何禁掉 `<a>` 标签默认事件，禁掉之后如何实现跳转。

解析：[第 85 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/135)




#### 第 86 题：周一算法题之「两数之和」

给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。

你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。

示例：

```js
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

解析：[第 86 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/136)

公司：京东、快手




#### 第 87 题：在输入框中如何判断输入的是一个正确的网址。

解析：[第 87 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/138)




#### 第 88 题：实现 convert 方法，把原始 list 转换成树形结构，要求尽可能降低时间复杂度

以下数据结构中，id 代表部门编号，name 是部门名称，parentId 是父部门编号，为 0 代表一级部门，现在要求实现一个 convert 方法，把原始 list 转换成树形结构，parentId 为多少就挂载在该 id 的属性 children 数组下，结构如下：

```js
// 原始 list 如下
let list =[
    {id:1,name:'部门A',parentId:0},
    {id:2,name:'部门B',parentId:0},
    {id:3,name:'部门C',parentId:1},
    {id:4,name:'部门D',parentId:1},
    {id:5,name:'部门E',parentId:2},
    {id:6,name:'部门F',parentId:3},
    {id:7,name:'部门G',parentId:2},
    {id:8,name:'部门H',parentId:4}
];
const result = convert(list, ...);

// 转换后的结果如下
let result = [
    {
      id: 1,
      name: '部门A',
      parentId: 0,
      children: [
        {
          id: 3,
          name: '部门C',
          parentId: 1,
          children: [
            {
              id: 6,
              name: '部门F',
              parentId: 3
            }, {
              id: 16,
              name: '部门L',
              parentId: 3
            }
          ]
        },
        {
          id: 4,
          name: '部门D',
          parentId: 1,
          children: [
            {
              id: 8,
              name: '部门H',
              parentId: 4
            }
          ]
        }
      ]
    },
  ···
];
```

解析：[第 88 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/139)




#### 第 89 题：设计并实现 Promise.race()

解析：[第 89 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/140)




#### 第 90 题：实现模糊搜索结果的关键词高亮显示

<img src="https://ws3.sinaimg.cn/large/006tNc79ly1g43dykaccuj30u01hc49s.jpg" height="800"/>

解析：[第 90 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/141)




#### 第 91 题：介绍下 HTTPS 中间人攻击

解析：[第 91 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/142)




#### 第 92 题：已知数据格式，实现一个函数 fn 找出链条中所有的父级 id

> ```js
> const value = '112'
> const fn = (value) => {
> ...
> }
> fn(value) // 输出 [1， 11， 112]
> ```



<img src="https://ws1.sinaimg.cn/large/006tNc79gy1g45a04ntttj30k20wen01.jpg" height="800"/>



解析：[第 92 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/143)




#### 第 93 题：给定两个大小为 m 和 n 的有序数组 nums1 和 nums2。请找出这两个有序数组的中位数。要求算法的时间复杂度为 O(log(m+n))。

示例 1：

```js
nums1 = [1, 3]
nums2 = [2]
```

中位数是 2.0

示例 2：

```js
nums1 = [1, 2]
nums2 = [3, 4]
```

中位数是(2 + 3) / 2 = 2.5

解析：[第 93 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/144)




#### 第 94 题：vue 在 v-for 时给每项元素绑定事件需要用事件代理吗？为什么？

解析：[第 94 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/145)




#### 第 95 题：模拟实现一个深拷贝，并考虑对象相互引用以及 Symbol 拷贝的情况

解析：[第 95 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/148)




#### 第 96 题：介绍下前端加密的常见场景和方法

解析：[第 96 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/150)




#### 第 97 题：React 和 Vue 的 diff 时间复杂度从 O(n^3) 优化到 O(n) ，那么 O(n^3) 和 O(n) 是如何计算出来的？

解析：[第 97 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/151)




#### 第 98 题：写出如下代码的打印结果

```js
function changeObjProperty(o) {
  o.siteUrl = "http://www.baidu.com"
  o = new Object()
  o.siteUrl = "http://www.google.com"
} 
let webSite = new Object();
changeObjProperty(webSite);
console.log(webSite.siteUrl);
```

公司：京东

解析：[第 98 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/152)




#### 第 99 题：编程算法题

> 用 JavaScript 写一个函数，输入 int 型，返回整数逆序后的字符串。如：输入整型 1234，返回字符串“4321”。要求必须使用递归函数调用，不能用全局变量，输入函数必须只有一个参数传入，必须返回字符串。

公司：bilibili

解析：[第 99 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/153)




#### 第 100 题：请写出如下代码的打印结果

> ```js
> function Foo() {
> Foo.a = function() {
>   console.log(1)
> }
> this.a = function() {
>   console.log(2)
> }
> }
> Foo.prototype.a = function() {
> console.log(3)
> }
> Foo.a = function() {
> console.log(4)
> }
> Foo.a();
> let obj = new Foo();
> obj.a();
> Foo.a();
> ```



公司：京东

解析：[第 100 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/155)




#### 第 101 题：修改以下 print 函数，使之输出 0 到 99，或者 99 到 0

> 要求：
>
> 1、只能修改 `setTimeout` 到 `Math.floor(Math.random() * 1000` 的代码
>
> 2、不能修改 `Math.floor(Math.random() * 1000`
>
> 3、不能使用全局变量
>
> ```js
> function print(n){
> setTimeout(() => {
>  console.log(n);
> }, Math.floor(Math.random() * 1000));
> }
> for(var i = 0; i < 100; i++){
> print(i);
> }
> ```



公司：头条

解析：[第 101 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/158)




#### 第 102 题：不用加减乘除运算符，求整数的7倍

解析：[第 102 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/161)




#### 第 103 题：模拟实现一个 localStorage

公司：阿里

解析：[第 103 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/166)




#### 第 104 题：模拟 localStorage 时如何实现过期时间功能

公司：阿里

解析：[第 104 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/171)




#### 第 105 题：编程题

> url有三种情况
>
> ```js
> https://www.xx.cn/api?keyword=&level1=&local_batch_id=&elective=&local_province_id=33
> https://www.xx.cn/api?keyword=&level1=&local_batch_id=&elective=800&local_province_id=33
> https://www.xx.cn/api?keyword=&level1=&local_batch_id=&elective=800,700&local_province_id=33
> ```
>
> 匹配elective后的数字输出（写出你认为的最优解法）:
>
> ```js
> [] || ['800'] || ['800','700']
> ```



解析：[第 105 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/177)




#### 第 106 题：分别写出如下代码的返回值

> ```js
> String('11') == new String('11');
> String('11') === new String('11');
> ```



公司：京东

解析：[第 106 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/180)




#### 第 107 题：考虑到性能问题，如何快速从一个巨大的数组中随机获取部分元素。

> 比如有个数组有100K个元素，从中不重复随机选取10K个元素。



解析：[第 107 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/187)




#### 第 108 题：请写出如下代码的打印结果

> ```js
> var name = 'Tom';
> (function() {
>  if (typeof name == 'undefined') {
>      var name = 'Jack';
>      console.log('Goodbye ' + name);
>  } else {
>      console.log('Hello ' + name);
>  }
> })();
> ```



公司：京东

解析：[第 108 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/190)




#### 第 109 题：扩展题，请写出如下代码的打印结果

> ```js
> var name = 'Tom';
> (function() {
>  if (typeof name == 'undefined') {
>      name = 'Jack';
>      console.log('Goodbye ' + name);
>  } else {
>      console.log('Hello ' + name);
>  }
> })();
> ```



公司：京东

解析：[第 109 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/198)




#### 第 110 题：编程题，请写一个函数，完成以下功能

> 输入
> ``'1, 2, 3, 5, 7, 8, 10'``
> 输出
> ``'1~3, 5, 7~8, 10'``



解析：[第 110 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/201)




#### 第 111 题：编程题，写个程序把 entry 转换成如下对象

> ```js
> var entry = {
> a: {
> b: {
>   c: {
>     dd: 'abcdd'
>   }
> },
> d: {
>   xx: 'adxx'
> },
> e: 'ae'
> }
> }
> 
> // 要求转换成如下对象
> var output = {
> 'a.b.c.dd': 'abcdd',
> 'a.d.xx': 'adxx',
> 'a.e': 'ae'
> }
> ```



解析：[第 111 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/206)




#### 第 112 题：编程题，写个程序把 entry 转换成如下对象（跟昨日题目相反）

> ```js
> var entry = {
> 'a.b.c.dd': 'abcdd',
> 'a.d.xx': 'adxx',
> 'a.e': 'ae'
> }
> 
> // 要求转换成如下对象
> var output = {
> a: {
> b: {
>   c: {
>     dd: 'abcdd'
>   }
> },
> d: {
>   xx: 'adxx'
> },
> e: 'ae'
> }
> }
> ```



解析：[第 112 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/212)




#### 第 113 题：编程题，根据以下要求，写一个数组去重函数（蘑菇街）

> 1. 如传入的数组元素为`[123, "meili", "123", "mogu", 123]`，则输出：`[123, "meili", "123", "mogu"]`
> 2. 如传入的数组元素为`[123, [1, 2, 3], [1, "2", 3], [1, 2, 3], "meili"]`，则输出：`[123, [1, 2, 3], [1, "2", 3], "meili"]`
> 3. 如传入的数组元素为`[123, {a: 1}, {a: {b: 1}}, {a: "1"}, {a: {b: 1}}, "meili"]`，则输出：`[123, {a: 1}, {a: {b: 1}}, {a: "1"}, "meili"]`



解析：[第 113 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/215)




#### 第 114 题：编程题，找出字符串中连续出现最多的字符和个数（蘑菇街）

> ```js
> 'abcaakjbb' => {'a':2,'b':2}
> 'abbkejsbcccwqaa' => {'c':3}
> ```



解析：[第 114 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/220)




#### 第 115 题：写一个单向链数据结构的 js 实现并标注复杂度（水滴筹）



解析：[第 115 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/226)




#### 第 116 题：输出以下代码运行结果

> ```js
> 1 + "1"
> 
> 2 * "2"
> 
> [1, 2] + [2, 1]
> 
> "a" + + "b"
> ```



解析：[第 116 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/229)




#### 第 117 题：介绍下 http1.0、1.1、2.0 协议的区别？



解析：[第 117 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/232)




#### 第 118 题：vue 渲染大量数据时应该怎么优化？



解析：[第 118 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/233)




#### 第 119 题：vue 如何优化首页的加载速度？vue 首页白屏是什么问题引起的？如何解决呢？



解析：[第 119 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/234)




#### 第 120 题：为什么 for 循环嵌套顺序会影响性能？

```js
var t1 = new Date().getTime()
for (let i = 0; i < 100; i++) {
  for (let j = 0; j < 1000; j++) {
    for (let k = 0; k < 10000; k++) {
    }
  }
}
var t2 = new Date().getTime()
console.log('first time', t2 - t1)

for (let i = 0; i < 10000; i++) {
  for (let j = 0; j < 1000; j++) {
    for (let k = 0; k < 100; k++) {

    }
  }
}
var t3 = new Date().getTime()
console.log('two time', t3 - t2)
```



解析：[第 120 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/235)




#### 第 121 题：统计 1 ~ n 整数中出现 1 的次数。

例如统计 1 ~ 400W 出现 1 的次数。



解析：[第 121 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/237)




#### 第 122 题：webpack 打包 vue 速度太慢怎么办？

解析：[第 122 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/238)




#### 第 123 题：vue 是如何对数组方法进行变异的？例如 push、pop、splice 等方法



解析：[第 123 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/239)




#### 第 124 题：永久性重定向（301）和临时性重定向（302）对 SEO 有什么影响



解析：[第 124 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/241)




#### 第 125 题：算法题

如何将`[{id: 1}, {id: 2, pId: 1}, ...]` 的重复数组（有重复数据）转成树形结构的数组 `[{id: 1, child: [{id: 2, pId: 1}]}, ...]` （需要去重）



解析：[第 125 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/243)




#### 第 126 题：扑克牌问题

> 有一堆扑克牌，将牌堆第一张放到桌子上，再将接下来的牌堆的第一张放到牌底，如此往复；
>
> 最后桌子上的牌顺序为： (牌底) 1,2,3,4,5,6,7,8,9,10,11,12,13 (牌顶)；
>
> 问：原来那堆牌的顺序，用函数实现。



解析：[第 126 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/245)




#### 第 127 题：如何用 css 或 js 实现多行文本溢出省略效果，考虑兼容性



解析：[第 127 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/246)




#### 第 128 题：Http 状态码 301 和 302 的应用场景分别是什么



解析：[第 128 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/249)




#### 第 129 题：输出以下代码执行结果

> ```js
> function wait() {
> return new Promise(resolve =>
>  setTimeout(resolve, 10 * 1000)
> )
> }
> 
> async function main() {
> console.time();
> const x = wait();
> const y = wait();
> const z = wait();
> await x;
> await y;
> await z;
> console.timeEnd();
> }
> main();
> ```



解析：[第 129 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/251)




#### 第 130 题：输出以下代码执行结果，大致时间就好（不同于上题）

> ```js
> function wait() {
> return new Promise(resolve =>
>  setTimeout(resolve, 10 * 1000)
> )
> }
> 
> async function main() {
> console.time();
> await wait();
> await wait();
> await wait();
> console.timeEnd();
> }
> main();
> ```



解析：[第 130 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/253)




#### 第 131 题：接口如何防刷



解析：[第 131 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/254)




#### 第 132 题：实现一个 Dialog 类，Dialog可以创建 dialog 对话框，对话框支持可拖拽（腾讯）



解析：[第 132 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/257)




#### 第 133 题：用 setTimeout 实现 setInterval，阐述实现的效果与 setInterval 的差异



解析：[第 133 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/259)




#### 第 134 题：求两个日期中间的有效日期

> 如 2015-2-8 到 2015-3-3，返回【2015-2-8 2015-2-9...】



解析：[第 134 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/264)




#### 第 135 题：算法题（盛大）

> 在一个字符串数组中有红、黄、蓝三种颜色的球，且个数不相等、顺序不一致，请为该数组排序。使得排序后数组中球的顺序为:黄、红、蓝。
>
> 例如：红蓝蓝黄红黄蓝红红黄红，排序后为：黄黄黄红红红红红蓝蓝蓝。



解析：[第 135 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/266)




#### 第 136 题：如何实现骨架屏，说说你的思路



解析：[第 136 题](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/270)
