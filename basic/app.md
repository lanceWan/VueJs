# 第一个Vue实例
* 创建一个Vue对象
* 模型属性显示
* 动态改变模型属性的值

## 创建一个Vue对象
创建一个Vue，只需要用关键词 `new Vue()` 即可，将会创建一个 `Vue` 对象

```html
<script type="text/javascript" src="../js/vue.js"></script>
<script type="text/javascript">
	var app = new Vue({...});
</script>
```

## 模型属性显示
创建一个Vue对象后，所有的属性、方法等全部放在 `new Vue({...})` 对象中，页面显示属性用 `{{ ... }}` 显示

```html
<!DOCTYPE html>
<html>
<head>
	<title>第一个Vue实例</title>
</head>
<body>
	<div id="app">
		<h1>{{title}}</h1>
        <input type="text" v-on:input="changeTitle">
	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
 			data: {
 				title: 'hello Vue'
 			},
            methods: {
                changeTitle: function (event) {
                    this.title = event.target.value;
                }
            }
 		});
 	</script>
</body>
</html>
```

> 属性的显示必须在Vue的作用域中，如果不在作用域中，属性值将不会显示。属性在的显示方法是由 `{{ ... }}` 的形式

# 动态改变模型属性的值
上面代码中 `<input type="text" v-on:input="changeTitle">`  ，在input上加上一个 `changeTitle` 的事件。`Vue` 实例中的 `methods` 相当于后端语言MVC模式中的 C （controller）。