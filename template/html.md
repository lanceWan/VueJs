# v-html
双大括号会将数据解释为纯文本，而非 HTML 。为了输出真正的 HTML ，你需要使用 ` v-html` 命令。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue模板v-html</title>
</head>
<body>
	<div id="app">
		<p>{{ link }}</p>
		<p v-html="link"></p>

	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
 			data: {
 				link: 'hello - <a href="http://www.baidu.com" target="_blank">百度</a>'
 			}
 		});
 	</script>
</body>
</html>
```

不能使用 v-html 来复合局部模板，因为 Vue 不是基于字符串的模板引擎。组件更适合担任 UI 重用与复合的基本单元。

> 你的站点上动态渲染的任意 HTML 可能会非常危险，因为它很容易导致 XSS 攻击。请只对可信内容使用 HTML 插值，绝不要对用户提供的内容插值。