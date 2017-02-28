# 一次性属性v-once
通过使用 ` v-once` 指令，你也能执行一次性地显示属性，当数据改变时，属性的内容不会更新。
> 注意这会影响到该节点上所有的数据绑定。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue模板v-once</title>
</head>
<body>
	<div id="app">
		<h1 v-once>{{ title }}</h1>
		<p>{{ sayHello() }} - <a :href="link" target="_blank">百度</a></p>

	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
 			data: {
 			    title: 'Hello Vue',
 				link: 'http://baidu.com'
 			},
			methods: {
                sayHello(){
                    this.title = 'Hello !';
                    return this.title;
				}
			}
 		});
 	</script>
</body>
</html>
```