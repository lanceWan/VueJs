# 对象迭代-v-for
`v-for` 通过一个对象的属性来迭代，同时支持当前项的索引。
```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue条件</title>
</head>
<body>
	<div id="app">
		<ul>
			<li v-for="web in website">
				<div v-for="(value, key, index) in web">{{key}}:{{value}}({{index}})</div>
			</li>
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