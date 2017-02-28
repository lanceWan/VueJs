# v-for
我们用 `v-for` 指令根据一组数组的选项列表进行渲染。 `v-for` 指令需要以 `item in items` 形式的特殊语法， `items` 是源数据数组并且 `item` 是数组元素迭代的别名。
```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue条件</title>
</head>
<body>
	<div id="app">
		<ul>
			<li v-for="fruit in fruits">{{ fruit }}</li>
		</ul>
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
                fruits:['香蕉','苹果','芒果','火龙果'],
				website:[
					{name: '百度' , url: 'http://www.baidu.com'},
					{name: '晚黎' , url: 'http://www.iwanli.me'},
					{name: 'Google' , url: 'http://www.google.com'},
				]
			},
		});
	</script>
</body>
</html>
```
`v-for` 还支持一个可选的第二个参数为当前项的索引。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue条件</title>
</head>
<body>
	<div id="app">
		<ul>
			<li v-for="(fruit,i) in fruits">{{i}}-{{ fruit }}</li>
		</ul>
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
                fruits:['香蕉','苹果','芒果','火龙果'],
				website:[
					{name: '百度' , url: 'http://www.baidu.com'},
					{name: '晚黎' , url: 'http://www.iwanli.me'},
					{name: 'Google' , url: 'http://www.google.com'},
				]
			},
		});
	</script>
</body>
</html>
```

> 第二个参数名称可以任意取名，但要保证在模板渲染的时候要跟索引名称保持一致