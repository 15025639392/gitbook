### 前言
>由于我或者其他前端小伙伴，对于前端跨域常常有许多迷惑行为，这里对几种跨域实现进行了搜录，总体来说，对于纯前端，无法实现跨域。不信？请看下列方案，自然会明白。

#### 1. jsonp
>只能发送get请求，xss攻击，不安全

````javascript
function jsonp({url,params,cb}){
    return new Promise((resolve,reject)=>{
        let script = document.createElement('script');
        window[cb]=function(data){
            resolve(data);
            document.body.appendChild(script);
            window[cb] = null;
        }
        let newparams = {
            ...params,
            cb
        }

        let arr = [];
        for(let key in newparams){
            arr.push(`${key}=${params[key]}`);
        }
        script.src = `${url}?${arr.join('&')}`;
        document.body.appendChild(script);
    })
}
````

#### 2. cors
>服务端解决方案，安全，麻烦

````javascript
let express = require('express');
let app = express();
app.use(express.static(__dirname));
app.listen(83);
let witList = ['http://localhost:3000']//设置白名单
let preFix = 'Access-Control-';
app.get('app',(req,res)=>{
    let {origin} = req.headers;
    if(witList.includes(origin)){
        //允许某个源反问
        res.setHeader(setHeader('Allow-Origin',origin));
        //允许携带哪个头
        res.setHeader(setHeader('Allow-Header','name'));
        //允许携带cookies
        res.setHeader(setHeader('Allow-Credentials',true));
        //允许使用什么方法访问
        res.setHeader(setHeader('Allow-Methods','PUT'));
        //预检存活时间
        res.setHeader(setHeader('Allow-Max-Age',6));
        //允许返回的头
        res.setHeader(setHeader('Allow-Expose-Headers','name'));
    }
    next();
})

function setHeader(suffix){
    return `${preFix}${suffix}`
}
````

#### 3. postMessage

a.html

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <iframe id="iframe" src="http://localhost:83/b.html" onload="onload(this)">
</body>
<script type="text/javascript">
    function onload(dom){
        dom.contentWindow.postMessage('b你好');
        window.onmessage=function(e){
            console.log(e.data);//a你好
        }
    }
</script>
</html>
````

b.html

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
</body>
<script type="text/javascript">
    window.onmessage(e){
        console.log(e.data);//b你好
        e.source.postMessage('a你好',e.origin)
    }
</script>
</html>
````

#### 4. window.name
>a 和 b 是同域的 http://localhost:3000

>c 是独立的 http://localhost:4000

>a 获取 c 数据

>a 先引用 c  c把值放到window.name; 把a的地址引用改为b

总结：这种方式很麻烦，很蠢

#### 5. hash通信
>a 和 b 是同域的 http://localhost:3000

>c 是独立的 http://localhost:4000

>a 获取 c 数据

>a 把hash传给 c  c收到hash后把结果通过hash传给b; b将结果放到a的hash中

总结：这种方式也很麻烦，很蠢

#### 6. domain
> a-> http://bstem.test.zcareze.com 和 b ->http://manage.test.zcareze.com

> a 和 b 都加上 window.domain = "test.zcareze.com"

#### 7. webSoket

server.js

````javascript
let express = require('express');
let app = express();
let webSorcket = require('ws');
let wss = new webSorcket.Server({port:3000});
wss.on('connect',(ws)=>{
    ws.on('message',(data)=>{
        console.log(data);//i love you
        ws.send('get it out')
    })
})
````

test.js

````javascript
//一般使用socket.io
let socket = new WebSocket('ws://localhost:3000');
socket.onopen = ()=>{
    socket.send('i love you');
}

socket.onmessage = (e)=>{
    console.log(e.data)//get it out
}
````