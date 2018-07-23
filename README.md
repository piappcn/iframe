## a.html 是父亲框架，b是子框架。子向父亲传递数据； c 页面是loding的样式；
###  1、子页面向主页面发送消息
```
// str是一个对象，JSON.stringify是JS将一个数组或者是对象转换成一个JSON字符串；
// 后面的*是传递给所有的窗口				    	
window.parent.postMessage(JSON.stringify(str),"*");				    	
// 上层父级页面接收消息
window.addEventListener('message',function(e){
	// 接收到消息之后的业务处理逻辑
	// 其中e.data是传过来内容
	// 其中e.source 传过来的对象
}

````

#### 2、主页面向子页面发送消息

````
// 主页面给子页面发送消息
var childIframe= document.getElementById('child');
//发送消息
childIframe.contentWindow.postMessage({"a":"111"},"*");
 
// 子页面接收消息
window.addEventListener('message',function(e){
	// 接收到消息之后的业务处理逻辑
	// 其中e.data是传过来内容
	// 其中e.source 传过来的对象
	// 其中e.origin 发送消息窗口的源（协议+主机+端口号）

````