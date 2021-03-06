#### http缓存控制
1. http缓存能够帮助服务器提高并发性能，很多资源不需要重复请求直接从浏览器中拿缓存。
2. http中缓存分为强缓存，协商缓存
3. 强缓存通过 expires cache-control控制，协商缓存通过last-moify e-tag控制
   
   补充：
   * 为什么有expires 需要 cache-control?
        * expires有客户端和服务器不同步的问题（expires是绝对时间cache-control是相对时间，cache优先级较高）
   * 为什么有last-modify还要e-tag？
        * last-modify有精度问题，精确到秒，e-tag没有精度问题，只要文件改变 e-tag就改变

#### 浏览器缓存分类
1. 浏览器先根据资源http头信息来判断是否命中强缓存，如果命中则直接加载缓存中的资源，并不会将请求头发送到服务器。（强缓存）
2. 如果未命中强缓存，则浏览器会将资源加载请求发送到服务器。服务器来判断浏览器本地缓存是否失效。如果可以使用则服务器不会返回资源信息，浏览器继续从浏览器缓存加载资源（协商缓存）
3. 如果未命中协商缓存，则服务器会将完整的资源返回给浏览器，浏览器加载新资源并更新缓存（重新请求）

#### 强缓存
>强缓存是利用http的返回头中的Expires或者Cache-Control两个字段来控制的

##### Expires
缓存过期时间点，是服务器的具体时间点
