# HTML5
## [History](/html5/history.md)
## Back Forward Cache
back-forward, 称为“往返缓存”， 可以在用户使用浏览器的“后退”和“前进”按钮时加快页面的转换速度。这个缓存不仅保存页面数据，还保存了DOM和JS的状态， 实际上是将整个页面都保存在内存里。如果页面位于back-forwardcache中，那么再次打开该页面就不会处罚onload事件

## pageshow事件
页面显示时触发，无论页面是否来自bfcache。重新加载的页面中，pageshow会在load事件触发后触发。对于back-forward cache中的页面，pageshow会在页面状态完全恢复的那一刻触发

## pagehide事件
在浏览器卸载页面的时候触发，而且在unload事件之前触发

## persisted事件
pageshow事件和pagehide事件对event对象还包含一个名为persisted的布尔值属性
对于pageshow事件，如果页面是从back-forward cache中加载，则这个属性的值为true；否则，这个属性的值为false。对于pagehide事件，如果页面在加载之后被保存在back-forward cache中，则这个属性的值为true；否则，这个属性的值为false。不同浏览器在当前窗口“打开”历史记录中的前一个页面的表现并不统一，这和浏览器的实现以及页面本身的设置都有关系。

页面监听了 unload 或者 beforeunload 事件; 
页面设置了 “cache-control: no-store”. 
网站使用 HTTPS 同时页面至少满足以下一个条件: 
“Cache-Control: no-cache” 
“Pragma: no-cache” 
设置请求头 “Expires: 0” 或者 “Expires” 的值为 “Date” 之前的值 (除非 “Cache-Control: max-age=” 也被设置了); 
页面在用户前进后退的时候还没有完全加载完或者它有正在进行的网络请求,比如 XMLHttpRequest; 
页面正在进行IndexedDB操作; 
顶层的页面包含有frame,并且这些frame由于这里列的任何一条原因而不能被缓存; 
页面在一个frame内，并且用户在这个frame内跳转到了一个新的网页,这里将被缓存的是新载入的网页 

``` js
window.onpageshow = function(event) {
  if (event.persisted) {
    window.location.reload();
  }
}
```