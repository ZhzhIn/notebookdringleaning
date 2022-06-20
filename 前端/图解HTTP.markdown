### chapter1  
http协议与其他协议的关系
![](.图解HTTP.markdown_images/6ace106c.png)  
URI: uniform resource identifier,指协议表示的资源定位标识符。
uri用字符串标识某一互联网资源，url表示资源的地点。
### chapter4  
http code   
![](.图解HTTP.markdown_images/3681d723.png)  
200 请求在服务端被正常处理了，在响应报文内，岁状态码一起返回的信息会因方法的不同而发生改变。  
比如，使用get方法时，对应请求资源的实体会作为响应返回；而是用HEAD方法时，对应请求资源的实体主体不随报文首部作为响应返回（即在响应中只返回首部，不会返回实体的主体部分）。
204 