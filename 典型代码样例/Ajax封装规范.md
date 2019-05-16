## AJAX的基本概念

AJAX = Asynchronous JavaScript and XML（异步的JavaScript和XML），意思是用JavaScript执行异步网络请求。

AJAX最大的优点是在不重新加载整个页面的情况下，可以与服务器交换数据并更新部分网页内容。

AJAX不需要任何浏览器插件，但需要用户允许JavaScript在浏览器上执行。

    尽管X在Ajax中代表XML, 但由于JSON的许多优势，比如更加轻量以及作为Javascript的一部分，目前JSON的使用比XML更加普遍。JSON和XML都被用于在Ajax模型中打包信息。

IE 5 率先在 js 中引入 ActiveX 对象，使 JS 可以直接发请求。
之后，Mozilla、Safari、Opera迅速跟进，取名 XMLHttpRequest，并被 W3C 纳入规范。
2005年，Jesse James Garrett 将使用 XMLHttpRequest 对象发请求的技术成为 AJAX。

## XMLHttpRequest对象

重点：**XMLHttpRequest 对象用来在浏览器和服务器之间进行数据传输**

### XMLHttpRequest对象实例解析

使用XMLHttpRequest对象，首先需要生成一个实例。
`let request = new XMLHttpRequest()`
接下来，讲一下XMLHttpRequest实例的方法

1. **request.open(nethod, url, async)**

request.open(method,url,async) 用来开启数据传输通路（字面意思，open，打开……）。
三个参数分别对应：
- method：请求的方法，可以是GET、PPST、PUT、DELETE等
- url：请求的路径
- async：是否异步，默认为true，就是异步。false 为同步，可能造成浏览器阻塞。

2. **request.send()**

request.send()用来向请求路径发送数据。当请求有数据发送时，参数为所发送的数据。
同步请求会等全部响应完毕再返回，异步请求直接返回该方法。

3. **readyState属性**

readyStage属性返回一个XMLHttpRequest代理当前所处的状态。

| 值 | 状态 | 描述 |
| ---- | ---- | ---- |
| 0 | UNSENT | 代理被创建，但尚未调用open()方法 |
| 1 | OPENED | open()方法已经被调用 |
| 2 | HEADERS_RECEIVED | send()方法已经被调用，并且头部和状态已经可获得 |
| 3 | LOADING | 下载中：responseText属性已经包含部分数据 |
| 4 | DONE | 下载操作已完成 |

4. **onreadystatechange属性**

onreadystatechange属性监听 readyState 的值（监听 XMLHttpRequest代理的状态），当值发生变化（状态变化），对不同的状态执行相应的回调函数。

    以上4个方法/属性就可以完成一个AJAX的请求

5. **request.setRequestHeader()方法**

request.setRequestHeader()方法：在发送请求之前设置请求头，对应http请求的第二部分。

`request.setRequestHeader('Content-Type','x-www-form-urlencoded')`

6. **request.responseText属性**

request.responseText 属性就是 AJAX 中后端返回的数据，一般是 JSON 格式的字符串。

## AJAX的请求流程

1. 生成 XMLHttpRequest 对象 `let request = new XMLHttpRequest()`
2. 配置 XMLHttpRequest 对象 `request.open('method','path')`
3. 发送请求 `request.send()`
4. 监听 XMLHttpRequest 对象 `request.onreadystatchange()`

基于上述流程，我们即可写一个简单的AJAX调用：

```javascript
'use strict'

function success(text) {
    var textarea = document.getElementById('test-response-text');
    textarea.value = text;
}

function fail(code) {
    var textarea = document.getElementById('test-response-text');
    textarea.value = 'Error code: ' + code;
}

var xmlhttp;
if (window.XMLHttpRequest) {
    //  IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
    xmlhttp=new XMLHttpRequest();
} else {
    // IE6, IE5 浏览器执行代码
    xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
}

xmlhttp.onreadystatechange = function () { // 状态发生变化时，函数被回调
    if (request.readyState === 4) { // 成功完成
        // 判断响应结果:
        if (request.status === 200) {
            // 成功，通过responseText拿到响应的文本:
            return success(request.responseText);
        } else {
            // 失败，根据响应码判断失败原因:
            return fail(request.status);
        }
    } else {
        // HTTP请求还在继续...
    }
}

// 发送请求:
xmlhttp.open('GET', '/api/categories');
xmlhttp.send();

alert('请求已发送，请等待响应...');
```

## AJAX封装最佳实践

上文详细讲述了AJAX的基本原理，正如AJAX名字的含义所表述的，AJAX是处理异步请求的，因此与最近流行的Promise结合起来可以方便的对基于BS的系统的AJAX公共方法进行封装。同时jQuery提供了非常完善强大的AJAX封装`$.ajax`，下面给出的封装基于`$.ajax`。`$.ajax`的更多接口说明，请戳[这里](http://www.w3school.com.cn/jquery/ajax_ajax.asp)。

```javascript
'use strict'

var TIME_OUT = 10 * 60 * 1000;

function ajax(config) {
    var settings = {
        "type": config.type,
        "contentType": "application/json; charset=UTF-8",
        "timeout": config.timeout || TIME_OUT,
        "headers": {
            // 可以增加系统公共请求头
        },
        "url": config.url,
        "data":  typeof config.params === "string" ? config.params : JSON.stringify(config.params || {}),
        "beforeSend": function(request, setting) {
            if (config.mask) {
                //打开遮罩层
            }

            // 支持调用自定义的beforeSend方法
            config.beforeSend && config.beforeSend(request, setting);
        },
        "complete": function(xhr, status) {
            if (config.mask) {
                // 关闭遮罩层
            }
            //可以视情况增加公共异常处理
        }
    };

    return new Promise(function(resolve, reject) {
        var $ajax = $.ajax(settings);
        $ajax.success(function(data, status, xhr){
            resolve(data);
        }).error(function(error) {
            reject(error);
        })
    })
}

// 调用
function getSomething () {
    var options = {
        "url" : '/rest/v1.0/getsomething',
        "timeout": 60000,
        "params": {
            "start": 0,
            "limit": 10,
            "name": "aaaa"
        },
        "beforeSent": function(request, setting) {
            request.setRequestHeader("contentType", "application/xml; charset=UTF-8");
        }
    };
    ajax(options).then(function(data) {
        //正常响应处理
    }, function(error) {
        //异常信息提示等处理
    })
}
```

## 基于angular的三层封装

待补充

## ES6标准下的ajax封装

待补充

