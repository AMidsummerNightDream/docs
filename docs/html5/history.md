# History API
Histroy API与浏览器历史堆栈管理
为了提高用户体验和加快响应速度，采用SPA架构。传统的单页应用基于url的hash值进行路由，这种实现不存在兼容新问题，但是缺点也针对不支持onhashchange属性的IE6-7需要设定时器不断检查hash值改变，性能上并不是友好。

移动端开发中HTML5规范给我们提供一个History接口，使用该接口可以自由操纵历史记录。

History接口如何影响浏览器历史堆栈。
history.pushState()和history.replaceState(),和1个事件， window.onpopstate

## pushState
history.pushState(stateObject, title, url)
- stateObject： 用于存储该url对应的状态对象，该对象可在onpopstate事件中获取，也可以在history对象中获取
- title： 标题，目前浏览器未实现
- url： 一般设置为相对路径，如果设置为绝对路径需要保证同源

pushState函数向浏览器的历史堆栈压入一个url为设定值的记录，并改变历史堆栈的当前指针至栈顶
## replaceState
该接口与pushState参数相同，含义也相同。唯一的区别在于replaceState是替换浏览器历史堆栈的当前历史记录为设定的url，replaceState不会改动浏览器历史堆栈的当前指针

## onpopstate
该事件是window的属性，该事件会在调用浏览器的前进，后退以及执行history.forward,history.back和history.go触发，因为这些操作有一个共性，即修改了历史堆的当前指针。在不改变document的前提下， 一旦当前指针改变则会触发onpopstate事件

history对象
概述
history.length
history.back()
history.forward()
history.go(-1)

history.pushState()和history.replaceState()

history.state属性
popstate事件
仅仅调用pushState方法或replaceState方法 ，并不会触发该事件，只有用户点击浏览器倒退按钮和前进按钮，或者使用JavaScript调用back、forward、go方法时才会触发

URLSearchParams API用于处理URL之中的查询字符串，即问号之后的部分。没有部署这个API的浏览器，可以用url-search-params这个垫片库。

- has(): 返回以