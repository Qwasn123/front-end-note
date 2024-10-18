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

### HTTP状态码

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
    SEO（Search Engine Optimization ，搜索引擎优化），是指通过优化网站内容、结构和外部链接等方式，提升网站在搜索引擎结果页面中的自然排名，从而增加网站的流量和可见性。
用简单的话来说，SEO就是让别人更容易在浏览器搜到你的网站。

那怎么更好的做SEO？
- 花钱
- 关键词(keywords,descriptions)
- 网站结构清晰(每一页都有一级标题)
- 友情链接
- 缩短网络层级，减少前往目标跳转次数
- 制作 sitemap.xml 
- SSR/SSG 服务器渲染(网站静态化)
- 简单粗暴(不推荐)：把所有的标签放在主页上

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
- 强缓存：浏览器在请求资源时，先查看缓存中是否有该资源的缓存副本，如果有，则直接使用缓存副本，不再向服务器发送请求。强缓存可以通过设置Cache-Control或Expires来实现。
- 协商缓存：当浏览器请求资源时，如果资源已经过期，则向服务器发送请求，由服务器根据请求报文中的缓存指令来决定是否使用缓存。协商缓存可以通过设置Last-Modified/If-Modified-Since和Etag/If-None-Match来实现。

### == 和 === 的区别
    == 是要求值相等，而 === 是要求值和类型都相等。而在 js 中， == 会先将值进行类型转换，再进行比较，而 === 则不会。

    == 与 === 和 Object.is() 的区别在于，Object.is() 是严格相等。

### script 标签放在 header 里和放在 body 底部里有什么区别？
    脚本会阻塞页面的渲染，放在 header 里可以让浏览器先渲染页面，然后再加载脚本，可以加快页面的渲染速度。