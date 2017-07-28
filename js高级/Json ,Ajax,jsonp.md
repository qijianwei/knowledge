## cookie
**是用来在服务端和客户端之间传输==额外数据==一种方式**，在http协议中，头信息中有一项设置，叫cookie，服务端可以在响应某个请求的时候，通过头信心中的cookie字段，向客户端同时发送一个数据，客户端得到数据，然后对头信息进行解析，如果有信息的cookie中有数据的话，那么浏览器会自动的把这个cookie保存起来，当下一次再次发送同域下的请求的时候，浏览器也会自动的把对应域名下的cookie获取出来，并通过请求头信息发送给服务端
1. cookie是以域名的形式进行存储的，不同的域名之间的cookie是不能共享的
2. cookie会随浏览器的请求一起发送，浏览器发送cookie的时候会发送和当前这次请求有关的域名下的cookie
3. 一个域名下可以同时保存多个cookie，不同浏览器支持的个数不一样，一般不少于20个
4. 多个cookie在传输的过程中使用 分号+空格的形式进行分隔
5. cookie一般是key，value形式，通过=号连接
6. 每个cookie是有大小限制，大概4K左右

### post
> 当我们通过一个post方式去发送请求，提交数据的时候，需要设置提交数据的编码格式（类型）

post提交数据，会把数据通过key=value的形式组织在一起，然后通过http的正文部分发送给服务端，我们把post提交的数据叫formdata，这种formdata有一定的组织格式

一共有三种常用类型：
1. application/x-www-form-urlencoded
2. multipart/form-data
3. text/plain

##### application/x-www-form-urlencoded
url编码格式：
把数据通过key=value的形式进行组织，==多个数据通过&进行拼接==：
username=leo&password=123
其中会把一些特殊的字符进行url编码，比如：&、=

##### text/plain
纯文本格式：不会进行任何编码处理，可能在传输中出现乱码问题

##### multipart/form-data
非文本的二进制数据

### GET
> 把数据按照key=value的形式组织起来，多个使用&连接，然后把数据拼接到url的?后面传递给服务端

get的数据组织形式和post中的application/x-www-form-urlencoded的组织形式是一样的，只是在传递过程中位置不一样

get: 请求行的url的？后面（querystring进行传递）

post: 请求正文

## json
1.JSON建构于两种结构：
    1.“名称/值”对的集合（A collection of name/value pairs）。不同的语言中，它被理解为对象（object），纪录（record），结构（struct），字典（dictionary），哈希表（hash table），有键列表（keyed list），或者关联数组 （associative array）。
 
 2.值的有序列表（An ordered list of values）。在大部分语言中，它被理解为数组（array）。
   
1.JSON.parse(str) 
```
parse用于从一个字符串中解析出json对象,如

var str = '{"name":"huangxiaojian","age":"23"}'

结果：

1.JSON.parse(str)

Object
    age: "23"
    name: "huangxiaojian"
    __proto__: Object



注意：单引号写在{}外，每个属性名都必须用双引号，否则会抛出异常。

```
2.JSON.stringify(a)
```
stringify()用于从一个对象解析出字符串，如

var a = {a:1,b:2}

结果：

2.JSON.stringify(a)

"{"a":1,"b":2}"


```



## Ajax
> AJAX即“Asynchronous Javascript And XML”（异步JavaScript和XML），是指一种创建交互式网页应用的网页开发技术。==ajax，其实是通过js提供的一个XMLHttpRequest对象来发送http请求。==

1. 创建对象
2. 设置请求参数
3. 监听响应
4. 发送请求

```
1.get方式
 $('#username').on('blur', function () {

         1. 创建对象
        var xhr = new XMLHttpRequest();
        /*
        * 2. 设置请求参数
        *   true : 异步无阻塞
        *   http://miaov.com/index.php/news/newsDetail/nid/82
        *   我们会对get方式传输的数据进行编码 - encodeURIComponent
        *   get会根据url进行缓存
        *   get会被浏览器历史记录所记录
        * */
        xhr.open('get', '/check_username?username=' + encodeURIComponent($('#username').val() ) + '&' + Date.now(), true);

        /*
        * 3. 监听响应
        * */
        xhr.onload = function() {
            //console.log(this.responseText);

            /*
            * http://localhost:8888/check_username?username=%E9%92%9F%E6%AF%85%E9%92%9F%E6%AF%85
            * http://localhost:8888/check_username?username=%E9%92%9F%E6%AF%85%E9%92%9F%E6%AF%85
            * */

            var res = JSON.parse(this.responseText);

            if (!res.code) {
                $('#checkUsernameMessage').removeClass('text-danger').addClass('text-success');
            } else {
                $('#checkUsernameMessage').removeClass('text-success').addClass('text-danger');
            }
            $('#checkUsernameMessage').html(res.message);
            console.log(res.message);
        };

        /*
        * 4. 发送请求
        * */
        xhr.send();

    });

```

```
2.post方式
$('form').on('submit', function() {

        var xhr = new XMLHttpRequest();

        xhr.open('post', '/register', true);

        xhr.onload = function () {
            //console.log(this.responseText);

            var res = JSON.parse( this.responseText );

            if (!res.code) {
                $('#registerMessage').removeClass('text-danger').addClass('text-success');
            } else {
                $('#registerMessage').removeClass('text-success').addClass('text-danger');
            }
            $('#registerMessage').html(res.message);
        };

        /*
        * 1.如果使用post方式发送请求，数据是通过send()方法的参数传递的因为
        post方法发送的数据类型可以是多种的，那么我们如果通过post方式发送
        数据的话，需要同时告诉后端我们发送的数据是什么类型的，我们需要在
        请求头中设置 content-type=application/x-www-form-urlencoded
        *
        * 当我们通过post方式发送数据的时候，不需要手动给数据进行编码，只需要
        在header中设置对应的content-type，ajax自动按照content-type的编码对数
        据进行处理
        *
        * post不会缓存
        * 不会被浏览器记录历史
        * */
        xhr.setRequestHeader('content-type', 'application/x-www-form-urlencoded');
        xhr.send('username=' + $('#username').val() + '&password=' + $('#password').val() + '&repassword=' + $('#repassword').val());

        return false;
    })

```






