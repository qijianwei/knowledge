### HTTP
基于tcp/ip协议之上的一套协议，用于web传输

1.单向请求：必须由客户端主动发送请求

2.无（连接）状态：当客户端连接服务端。服务端响应完成以后，客户端和服务端就会断开连接，如果我们还要继续做数据的传输，则需要重新连接

### Socket
网络编程实现接口，如果我们需要进行网络编程，需要使用Socket提供一系列方法来实现

### websocket
一种协议，数据通信协议，优势在于和http比较，1.可以双向通信。2.持久连接

### socket.io
```
socket.emit(name, message)
1.发送一条数据给服务端，其实本质上就是触发案例一个名称叫title的事件，内容是message
    a.name: 事件名称
    b. message: 数据内容
var socket = io();
socket.emit('hello', messageContainer.value);
一个基于node的websocket框架
```
### cookie
document.cookie: 通过该属性可以操作（获取、设置）cookie(通过js可以操作cookie)

cookie默认存储时间是：会话结束，当浏览器关闭的时候


```
/*设置cookie
*/
    document.cookie ='a=1;Max-Age=10000';

    /*
    * 删除cookie
    * */
    document.cookie = 'a=1; Max-Age=-1';

    function getCookie(key) {
        var arr1 = document.cookie.split('; ');
//        console.log(arr1);
        for (var i=0; i<arr1.length; i++) {
            var arr2 = arr1[i].split('=');
            if (arr2[0] == key) {
                return arr2[1];
            }
        }
    }

```

# cache
缓存的整个页面

# cookie
1.存储指定数据
2.会发送给服务端

# localStorage
1.存储指定数据
2.不会发送给服务端
3.同域下的页面共享数据(qq音乐里添加音乐)
4.支持广播事件：storage

# sessionStorage
1.存储指定数据
2.不会发送给服务端
3.页面独享

