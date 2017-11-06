# HTTP Cookie

## HTTP Header

有两个Http头部和Cookie有关：Set-Cookie和Cookie。
    
    1. Set-Cookie由服务器发送，它包含在响应请求的头部中。它用于在客户端创建一个Cookie
    2. Cookie头由客户端发送，包含在HTTP请求的头部中。注意，只有cookie的domain和path与请求的URL匹配才会发送这个cookie。

## Set-Cookie Header 


Set-Cookie响应头的格式如下所示：

        Set-Cookie: <name>=<value>[; <name>=<value>]...
                    [; expires=<date>][; domain=<domain_name>]
                    [; path=<some_path>][; secure][; httponly]

    expires=<date>: 设置cookie的有效期，如果cookie超过date所表示的日期时，cookie将失效。
                    如果没有设置这个选项，那么cookie将在浏览器关闭时失效。
                    注意：date是格林威治时间(GMT)，使用如下格式表示：
                        DAY, DD MMM YYYY HH:MM:SS GMT

                        DAY
                            The day of the week (Sun, Mon, Tue, Wed, Thu, Fri, Sat).
                        DD
                            The day in the month (such as 01 for the first day of the month).
                        MMM
                            The three-letter abbreviation for the month (Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec).
                        YYYY
                            The year.
                        HH
                            The hour value in military time (22 would be 10:00 P.M., for example).
                        MM
                            The minute value.
                        SS
                            The second value.

    domain=<domain_name> : 
    path=<some_path>:
                    注：临时cookie(没有expires参数的cookie)不能带有domain选项。
                    当客户端发送一个http请求时，会将有效的cookie一起发送给服务器。
                    如果一个cookie的domain和path参数和URL匹配，那么这个cookie就是有效的。
                    一个URL中包含有domain和path，可以参考http://www.w3school.com.cn/html/html_url.asp
 


    secure   : 表示cookie只能被发送到http服务器。
    httponly : 表示cookie不能被客户端脚本获取到。

## 在程序中生成expires 

C的方式 
```
    time_t curTime = time(NULL);
    tm * gmTime = gmtime(&curTime);

    char strExperis[50];
    strftime(strTimeBuf, 100, " %a, %d %b %Y %X GMT;", gmTime);
```

JavaScript的方式 
```
var d = new Date();
var expires = d.toGMTString();
```

## Windows中的InternetSetCookie 

在Windows中我们可以使用InternetSetCookie来设置Cookie，假如说，A和B两个进程使用Cookie通信，那么会有如下几种情况：

 > A写Global Cookie，B写Session Cookie，此时，A中无法获取Cookie

 > A写Session Cookie，B写Session Cookie，此时，A与B中的Cookie互不影响

 > A写Session Cookie，B写Global Cookie，此时A中的Cookie被Global Cookie覆盖，它们共享一份Global Cookie

    注：这种情况的后果下，如果有任意一个进程再写Session Cookie，那么其他进程将获取不到Cookie 

## 各大平台

1. 