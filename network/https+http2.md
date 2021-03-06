## https原理
https://juejin.im/entry/56ce90edefa631df62c21f8d
HTTPS 是披了层 SSL 外壳的 HTTP
第一步，用户在浏览器里输入一个https网址，此时客户端发起HTTPS请求，通过TCP和服务器建立连接（443端口）。

第二步，服务器存放CA证书进行处理，注意的是采用HTTPS协议的服务器必须要有一套数字证书，这套证书其实就是一对公钥和私钥。

第三步，服务器向客户端返回证书。证书里面包含了很多信息：比如域名，申请证书的公司，公钥等。

第四步，客户端对证书进行解析。这部分工作是有客户端的TLS来完成的，首先会验证公钥是否有效，比如颁发机构，过期时间等，如果发现异常，则会弹出一个警告框，提示证书存在问题。如果证书没有问题，那么就生成一个随机数，然后用证书对该随机数进行加密。

第五步，向服务器发送证书加密后的随机数。

第六步，服务器用它的私钥进行解密，得到了客户端传过来的随机数。
 
第七步，服务器用客户端的随机数加密后的信息发送给客户端。

第八步，客户端用之前生成的私钥解密服务端传过来的信息。


## http2
1. **服务端推**允许服务端在客户端需要数据之前就主动地将数据发送到客户端缓存中，从而提高性能。
2. 提供更多的加密支持
3. 使用多路技术，允许多个消息在一个连接上同时交差。
4. 头压缩（header compression），因此即使非常小的请求，其请求和响应的header都只会占用很小比例的带宽

#### defer和async 

>defer并行加载js文件，会按照页面上script标签的顺序执行 

>async并行加载js文件，下载完成立即执行，不会按照页面上script标签的顺序执行 