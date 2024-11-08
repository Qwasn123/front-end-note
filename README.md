# FrontEnd_Note
这个笔记是用于记录本人在阅读相关资料时的笔记，主要是前端开发相关的知识。

## 《七天八股速记：前端》

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/7-day-interview-qian-duan/dm0d66/
来源：力扣（LeetCode）

### Canvas / WebGL
1. Canvas 是 HTML5 提供的 2D 绘图API，适用于绘制简单的图形、图片、动画等。
2. WebGL 是基于 OpenGL 的 JavaScript API，允许在 Canvas 中使用 GPU 加速绘制 3D 图形和复杂的视觉效果。

### WebSocket
WebSocket 是一种在单个 TCP 连接上进行全双工通信的协议，适用于需要实时数据交换的应用场景，如在线聊天、游戏、股票行情更新等。它比传统的 HTTP 轮询更加高效，能够在客户端和服务器之间保持持续连接，并允许双向数据传输。

[Websocket 优质视频 - 哔哩哔哩 （作者：小白debug）](https://b23.tv/XTWtdyp)

```javascript
// 创建一个 WebSocket 连接
const socket = new WebSocket('ws://example.com/socket');

// 连接成功时触发
socket.onopen = function(event) {
  console.log('WebSocket 连接已打开');
  // 发送一条消息到服务器
  socket.send('Hello, Server!');
};

// 收到服务器消息时触发
socket.onmessage = function(event) {
  console.log('收到服务器消息:', event.data);
};

// 连接关闭时触发
socket.onclose = function(event) {
  console.log('WebSocket 连接已关闭');
};

// 连接出错时触发
socket.onerror = function(error) {
  console.log('WebSocket 错误:', error);
};

```

### 【拓展】网络协议列表
上面提到的HTTP、WebSocket、UDP等都是网络协议，不同的协议用于不同的网络通信。TCP和IP在分开写的时候是TCP/IP四层模型当中的俩协议。

1. **应用层（Application Layer）**
应用层协议用于为应用程序提供网络服务。
- HTTP/HTTPS：超文本传输协议，用于 Web 页面传输。HTTPS 是加密版本。
- FTP：文件传输协议，用于在网络上传输文件。
- SMTP：简单邮件传输协议，用于发送电子邮件。
- IMAP/POP3：用于接收电子邮件的协议，IMAP 支持多客户端同步，POP3 是单次获取。
- DNS：域名系统协议，用于将域名解析为 IP 地址。
- DHCP：动态主机配置协议，用于动态分配 IP 地址。
- SSH：安全外壳协议，用于安全登录远程计算机。
- Telnet：一种早期的远程登录协议，不加密数据传输。
- NTP：网络时间协议，用于同步网络中的时钟。
- SNMP：简单网络管理协议，用于管理和监控网络设备。
2. **传输层（Transport Layer）**
传输层协议负责数据的传输和连接管理。
- TCP：传输控制协议，提供可靠的、面向连接的数据传输。
- UDP：用户数据报协议，不可靠、无连接的传输，但速度快，常用于视频流、游戏等。
3. **网络层（Network Layer）**
网络层协议负责路由和数据包传输。
- IP（IPv4/IPv6）：互联网协议，提供主机间的数据传输和寻址。IPv6 是新一代互联网协议，取代 IPv4。
- ICMP：互联网控制报文协议，用于传递控制消息（如 ping）。
- ARP：地址解析协议，用于将 IP 地址映射为 MAC 地址。
- RIP、OSPF、BGP：路由协议，用于网络间的路由信息交换。
4. **链路层（Link Layer）**
链路层协议负责物理设备间的数据传输。
- Ethernet（以太网）：用于局域网中的数据传输。
- PPP：点对点协议，主要用于通过电话线或其他连接类型进行点对点数据传输。
- Wi-Fi（IEEE 802.11）：无线局域网标准，用于设备间的无线通信。
- MAC：介质访问控制协议，用于网络设备访问共享介质（如以太网或 Wi-Fi）。  

**其他协议**
- WebSocket：在应用层和传输层之间，提供全双工通信，用于实时数据交换。
- TLS/SSL：安全层协议，通常用于加密 HTTPS 和其他网络通信。
- IPsec：用于加密和认证网络层通信，常用于 VPN 中。

### HTTP协议常见版本

- HTTP 1.0： 基于TCP协议，只支持保持短暂的连接，浏览此每次的请求都要重新再和服务器建立一个新的TCP连接。
- HTTP 1.1： 到了1.1版本就加入了持久连接，不会断开。客户端可以同时发送好几个请求。但是服务器处理请求仍然是按顺序进行的，不能并行。
- HTTP 2.0： 将文本形式改为二进制形式，多路复用，只要一个连接就可以并行，头部压缩，服务器推送。
- HTTP 3.0： 转为基于UDP协议，解决了TCP的队头阻塞问题。但同时保留了HTTP2.0的多路复用等特性。

### 【拓展】异步？并行？
> 作为一个小白，我之前一直都分不清异步和并行有什么区别，在我印象里它们都是同时发生的。。。

异步和并行本质上完全不相同：异步是一种任务调度方式，而并行是一种任务执行方式。    
  
异步的核心是非阻塞操作，即程序在等待某个操作完成时，可以执行其他任务。  
并行则强调多个任务在多个线程或核心上同时运行。

### 异步 async & await
async 是异步的意思，await则可以理解为 async wait。所以可以理解async就是用来声明一个异步方法，而 await是用来等待异步方法执行。

### HTTP状态码
HTTP 状态码是服务器在收到客户端请求后返回的响应中的一个字段，用于表示请求的状态。
- 1xx：信息提示类，表示接收到请求，继续处理。
- 2xx：成功类，表示请求成功收到，理解并接受。
- 3xx：重定向类，表示需要进行附加操作，如需先进行某些处理才能完成请求。
- 4xx：客户端错误类，表示请求包含语法错误或无法完成请求。
- 5xx：服务器错误类，表示服务器在处理请求的过程中发生了错误。

常见状态码

- 【403】表示【服务器拒绝执行客户端的请求】
- 【404】表示【服务器找不到客户端所请求的资源（网页）】
- 【304】表示【所请求的资源并未修改（命中协商缓存）

不常见状态码

- 【101】表示【协议切换】

### 304 过程
缓存过期后向服务器发起请求验证缓存是否有效，有效的话则返回304。304多出现在对于静态资源的请求上面。对于静态资源来说：当浏览器第一次发起请求时（请求头中没有If-Modified-Since），server会在响应中告诉浏览器这个资源最后修改的时间（响应头中的Last-Modified）。当你再次请求这个资源时，浏览器会询问server这个资源有没有被修改（请求头中If-Modified-Since）。如果资源没有被修改，server返回304状态码，浏览器使用本地的缓存文件。

### 正则表达式
| 规则 | 描述 |
| --- | --- |
| \ | 转义字符 |
| ^ | 匹配输入的开始 |
| $ | 匹配输入的结束 |
| * | 匹配前一个表达式 0 次或多次 |
| + | 匹配前面一个表达式 1 次或者多次。等价于 {1,} |
|? | 匹配前面一个表达式 0 次或者 1 次。等价于{0,1} |
|. | 默认匹配除换行符之外的任何单个字符 |
| x(?=y) | 匹配'x'仅仅当'x'后面跟着'y'。这种叫做先行断言 |
| (?<=y)x | 匹配'x'仅当'x'前面是'y'.这种叫做后行断言 |
| x(?!y) | 仅仅当'x'后面不跟着'y'时匹配'x'，这被称为正向否定查找 |
| (?<!y)x | 仅仅当'x'前面不是'y'时匹配'x'，这被称为反向否定查找 |
| {n} | n 是一个正整数，匹配了前面一个字符刚好出现了 n 次 |
| {n,} | n是一个正整数，匹配前一个字符至少出现了n次 |
| {n,m} | n 和 m 都是整数。匹配前面的字符至少n次，最多m次 |
| [xyz] | 一个字符集合。匹配方括号中的任意字符 |
| [^xyz] | 匹配任何没有包含在方括号中的字符 |
| \b | 匹配一个词的边界，例如在字母和空格之间 |
| \B | 匹配一个非单词边界 |
| \d | 匹配一个数字 |
| \D | 匹配一个非数字字符 |
| \f | 匹配一个换页符 |
| \n | 匹配一个换行符 |
| \r | 匹配一个回车符 |
| \s | 匹配一个空白字符，包括空格、制表符、换页符和换行符 |
| \S | 匹配一个非空白字符 |
| \w | 匹配一个单字字符（字母、数字或者下划线） |
| \W | 匹配一个非单字字符 |


### SEO 搜索引擎优化
    简单来说，SEO就是让别人更容易在浏览器搜到你的网站。
SEO（Search Engine Optimization ，搜索引擎优化），是指通过优化网站内容、结构和外部链接等方式，提升网站在搜索引擎结果页面中的自然排名，从而增加网站的流量和可见性。  

那怎么更好的做SEO？
- 花钱
- 关键词(keywords,descriptions)
- 网站结构清晰(每一页都有一级标题)
- 友情链接
- 缩短网络层级，减少前往目标跳转次数
- 制作 sitemap.xml 
- SSR/SSG 服务器渲染(网站静态化)
- 简单粗暴(不推荐)：把所有的标签放在主页上

[鱼皮的教学 - SEO 优化]( https://b23.tv/W87vYt7 )

### 数组的常用方法
- join()：将数组的元素组起一个字符串，以separator为分隔符，省略的话则用默认用逗号为分隔符。
- push()：将参数添加到原数组末尾，并返回数组的长度(修改原数组)。
- pop()：删除原数组最后一项，并返回删除元素的值；如果数组为空则返回undefined（修改原数组）。
- shift()：删除原数组第一项，并返回删除元素的值；如果数组为空则返回undefined。
- unshift()： 将参数添加到原数组开头，并返回数组的长度（修改原数组）。
- slice(start,end):可以截取出数组某部份的元素为一个新的数组，有两个必填的参数，第一个是起始位置，第二个是结束位置( 操作时数字减1 ) 原数组不改变。
- splice(start,deleteCount,val1,val2,…):从start位置开始删除deleteCount项，并从该位置起插入。（修改原数组）。
- fill()：使用特定值填充数组中的一个或多个元素(修改原数组)。
- filter()：过滤,数组中的每一项运行给定函数，返回满足过滤条件组成的数组。
- concat()：可以将两个数组合并在一起，如果是使用ES6语法也可以用扩展运算符…来代替。
- indexOf()：返回当前值在数组中第一次出现位置的索引。
- lastIndexOf()：返回查找的字符串最后出现的位置，如果没有找到匹配字符串则返回 -1。
- every()：判断数组中每一项是否都符合条件。
- some()：判断数组中是否存在满足的项。
- includes()：判断一个数组是否包含指定的值。
- sort(orderfunction):按指定的参数对数组进行排序(修改原数组)。
- reverse()：将数组反序(修改原数组)。
- forEach()：循环遍历数组每一项（没有返回值）。
- map()：循环遍历数组的每一项（有返回值）。
- copyWithin(): 从数组的指定位置拷贝元素到数组的另一个指定位置中（修改原数组）。
- find(): 返回第一个匹配的值，并停止查找。
- findIndex(): 返回第一个匹配值的索引，并停止查找。
- toLocaleString()、toString():将数组转换为字符串。
- flat()、flatMap()：扁平化数组。
- entries() 、keys() 、values():遍历数组。 

### 强缓存和协商缓存
    通俗来说，【强缓存】客户端请求数据会先查看本地缓存，通过cache-control字段来判断缓存是不是还有效，有效就用(这种情况没用真正请求服务器)，无效就再请求。  

    【协商缓存】当上面发现强缓存失效的时候，就会返回这个资源的缓存标识。然后客户端就会带着这个标识去真正的请求服务器，询问服务器这个资源是否更新了，如果更新了，服务器会返回新的资源，客户端就更新本地缓存。如果没有更新，就直接用本地缓存。
**浏览器缓存的特点：**
- 浏览器每次发起请求，都会先在浏览器缓存中查找该请求的结果以及缓存标识
- 浏览器每次拿到返回的请求结果都会将该结果和缓存标识存入浏览器缓存中  
  
根据是否需要向服务器重新发起HTTP请求将缓存过程分为两个部分，分别是强制缓存和协商缓存。

**协商缓存**  
- 协商缓存就是强制缓存失效后，浏览器携带缓存标识向服务器发起请求，由服务器根据缓存标识决定是否使用缓存的过程。

- 协商缓存主要有以下两种情况：
  - 协商缓存生效，返回304
  - 协商缓存失效，返回200和请求结果结果

### 【拓展】什么是缓存字段？
通俗来讲，缓存字段是HTTP请求报文中的一部分，是写在header中的一部分，它是用来告诉服务器是否可以直接从缓存中获取资源，还是需要重新向服务器请求。当有些数据有可能会被重复利用时，就可以使用缓存字段来存储，从而减少资源消耗，提高响应速度。
- Cache-Control：控制缓存的行为，如max-age=3600表示缓存内容将在3600秒后过期，在这段时间内重复请求，就不用再次请求服务器。
- Expires：指定缓存的过期时间，与Cache-Control配合使用。  
- Last-Modified/If-Modified-Since：用于标识资源的最后修改时间，配合Etag使用。
- Etag/If-None-Match：用于标识资源的唯一标识，配合Last-Modified使用。
<!-- 
### 【拓展】什么是跨域？
跨域是指浏览器不能执行其他网站的脚本。比如，A网站的脚本不能访问B网站的资源，因为两者协议、域名、端口不同。

**跨域的原理：**
- 同源策略：同源策略是一种约定，由Netscape公司1995年提出，它是浏览器最核心也最基本的安全功能，如果缺少同源策略，则浏览器的正常功能可能被限制。同源策略规定，两个页面只能通信互相发送请求，不能共享数据。
- 跨域请求：跨域请求是指不同源的页面之间进行数据的交互。比如，A网站的脚本不能访问B网站的资源，因为两者协议、域名、端口不同。
- 跨域解决方案：常见的跨域解决方案有JSONP、CORS、postMessage、WebSocket等。

1. JSONP：JSONP（JSON with Padding）是一种非官方的跨域解决方案，它利用script标签的src属性，通过src属性可以跨域请求数据。
2. CORS：CORS（Cross-Origin Resource Sharing）是W3C标准，它是一种跨域解决方案。它通过在HTTP请求头中增加Origin字段，来告诉服务器本次请求的来源，服务器根据这个值判断是否给予响应。
3. postMessage：postMessage是HTML5新增的API，它允许不同源的页面进行通信。
4. WebSocket：WebSocket是一种通信协议，它是一种双向通信的协议，可以实现服务器主动向客户端推送消息。 -->

### == 和 === 的区别

== 是要求值相等，而 === 是要求值和类型都相等。而在 js 中， == 会先将值进行类型转换，再进行比较，而 === 则不会。
== 与 === 和 Object.is() 的区别在于，Object.is() 是严格相等。

### script 标签放在 header 里和放在 body 底部里有什么区别？
    简单来说，放在<header>中时，浏览器会立刻下载并执行脚本，阻塞HTML的解析，导致页面渲染延迟。  

    而在<body>底部时，则可以确保页面被渲染，让用户在加载和执行脚本的时候可以看到页面的其他内容。

### GET 和 POST 的区别
1. 针对数据操作的类型不同
	- GET 是只读，查询数据。
	- POST 是写，增删改数据。
2. 参数大小不同
	- GET 限制URL传的参数长度。
	- POST 不限制。
3. 安全性不同
	- GET 通过URL传递会暴露，不安全。
	- POST 在 Request Body 中，相对安全。
4. 浏览器回退表现不同
	- GET 回退是无害的。
	- POST 是会再次提交请求的。
5. 浏览器对请求地址处理不同
	- GET 会被浏览器自动缓存请求地址。
	- POST 不会，只能手动设置。
6. 浏览器对相应的处理不同
	- GET 请求参数会被完整保留。
	- POST 不会保留。
	
### var,const,let 三者之间的区别
ES6之前创建变量用var，之后用let/const
- var 存在变量提升，另外两个不存在;
- let 不能重复定义，关键词允许值的修改;
- const 也不能重复定义，关键词不允许修改;

### 【拓展】什么是变量提升？
变量提升简单来说就是在代码中要是一个函数中用到了参数num，但是num的声明处于该函数的下方，则可以视为这个num已经在上面声明过了。






