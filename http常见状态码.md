| **状态码** | **内容** | **详细内容** |
| :--- | :--- | :--- |
| 1xx | 这一类型的状态码，代表请求已被接受，需要继续处理。 |  |
| 100 | Continue | 收到请求，客户端应当继续发送请求。 |
| 101 | Switching Protocols | 服务器通过 Upgrade 消息头通知客户端采用不同的协议来完成这个请求。 |
| 2xx | 成功 \| 这一类型的状态码，代表请求已成功被服务器接收、理解、并接受。 |  |
| 200 | OK | 请求已成功，请求的响应头或数据体将随此响应返回。 |
| 201 | Created | 请求已经被实现，而且有一个新的资源已经依据请求的需要而创建，且其 URI 已经随 Location 头信息返回。 |
| 202 | Accepted | 服务器已接受请求，但尚未处理。正如它可能被拒绝一样，最终该请求可能会也可能不会被执行。 |
| 203 | Non-Authoritative Information | 服务器已成功处理了请求，但返回的实体头部元信息不是在原始服务器上有效的确定集合，而是来自本地或者第三方的拷贝。 |
| 204 | No Content | 服务器成功处理了请求，但没有返回任何实体内容。 |
| 205 | Reset Content | 服务器成功处理了请求，且没有返回任何内容。但是与204响应不同，返回此状态码的响应要求请求者重置文档视图。 |
| 206 | Partial Content | 服务器已经成功处理了部分 GET 请求。 |
| 3xx | 重定向 \| 这类状态码代表需要客户端采取进一步的操作才能完成请求。通常，这些状态码用来重定向，后续的请求地址（重定向目标）在本次响应的 Location 域中指明。 |  |
| 300 | Multiple Choices | 被请求的资源有一系列可供选择的回馈信息，每个都有自己特定的地址和浏览器驱动的商议信息。用户或浏览器能够自行选择一个首选的地址进行重定向。 |
| 301 | Moved Permanently | 被请求的资源已永久移动到新位置，并且将来任何对此资源的引用都应该使用本响应返回的若干个 URI 之一。 |
| 302 | Found | 请求的资源现在临时从不同的 URI 响应请求。由于这样的重定向是临时的，客户端应当继续向原有地址发送以后的请求。 |
| 303 | See Other | 对应当前请求的响应可以在另一个 URI 上被找到，而且客户端应当采用 GET 的方式访问那个资源。 |
| 304 | Not Modified | 如果客户端发送了一个带条件的 GET 请求且该请求已被允许，而文档的内容（自上次访问以来或者根据请求的条件）并没有改变，则服务器应当返回这个状态码。 |
| 305 | Use Proxy | 被请求的资源必须通过指定的代理才能被访问。Location 域中将给出指定的代理所在的URI信息，接收者需要重复发送一个单独的请求，通过这个代理才能访问相应资源。 |
| 307 | Temporary Redirect | 请求的资源现在临时从不同的 URI 响应请求。由于这样的重定向是临时的，客户端应当继续向原有地址发送以后的请求。 |
| 4xx | 客户端错误 \| 这类的状态码代表了客户端看起来可能发生了错误，妨碍了服务器的处理。 |  |
| 400 | Bad Request | 由于包含语法错误，当前请求无法被服务器理解。 |
| 401 | Unauthorized | 当前请求需要用户验证。 |
| 402 | Payment Required | 该状态码是为了将来可能的需求而预留的。 |
| 403 | Forbidden | 服务器已经理解请求，但是拒绝执行它。 |
| 404 | Not Found | 请求失败，请求的资源在服务器上找不到。 |
| 405 | Method Not Allowed | 请求中指定的请求方法不能被用于请求相应的资源。 |
| 406 | Not Acceptable | 请求的资源的内容特性无法满足请求头中的条件，因而无法生成响应实体。 |
| 407 | Proxy Authentication Required | 与 401 状态码类似，只不过客户端必须在代理服务器上进行身份验证。 |
| 408 | Request Timeout | 请求超时。客户端没有在服务器预备等待的时间内完成一个请求的发送。 |
| 409 | Conflict | 由于和被请求的资源的当前状态之间存在冲突，请求无法完成。 |
| 410 | Gone | 被请求的资源在服务器上已经不再可用，而且没有任何已知的转发地址。 |
| 411 | Length Required | 服务器拒绝在没有定义 Content-Length 头的情况下接受请求。 |
| 412 | Precondition Failed | 服务器在验证在请求的头字段中给出先决条件时，没能满足其中的一个或多个。 |
| 413 | Request Entity Too Large | 服务器拒绝处理当前请求，因为该请求提交的实体数据大小超过了服务器愿意或者能够处理的范围。 |
| 414 | Request-URI Too Long | 请求的 URI 长度超过了服务器能够解释的长度，因此服务器拒绝对该请求提供服务。 |
| 415 | Unsupported Media Type | 对于当前请求的方法和所请求的资源，请求中提交的实体并不是服务器中所支持的格式，因此请求被拒绝。 |
| 416 | Requested Range Not Satisfiable | 如果请求中包含了 Range 请求头，并且 Range 中指定的任何数据范围都与当前资源的可用范围不重合，同时请求中又没有定义 If-Range 请求头，那么服务器就应当返回 416 状态码。 |
| 417 | Expectation Failed | 在请求头 Expect 中指定的预期内容无法被服务器满足，或者这个服务器是一个代理服务器，它有明显的证据证明在当前路由的下一个节点上，Expect 的内容无法被满足。 |
| 5xx | 服务器错误 \| 这类状态码代表了服务器在处理请求的过程中有错误或者异常状态发生。 |  |
| 500 | Internal Server Error | 服务器遇到了一个未曾预料的状况，导致了它无法完成对请求的处理。 |
| 501 | Not Implemented | 服务器不支持当前请求所需要的某个功能。 |
| 502 | Bad Gateway | 作为网关或者代理工作的服务器尝试执行请求时，从上游服务器接收到无效的响应。 |
| 503 | Service Unavailable | 由于临时的服务器维护或者过载，服务器当前无法处理请求。 |
| 504 | Gateway Timeout | 作为网关或者代理工作的服务器尝试执行请求时，未能及时从上游服务器（URI 标识出的服务器，例如 HTTP、FTP、LDAP）或者辅助服务器（例如 DNS）收到响应。 |
| 505 | HTTP Version Not Supported | 服务器不支持，或者拒绝支持在请求中使用的HTTP版本。 |



