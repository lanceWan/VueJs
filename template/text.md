# 文本显示
Vue.js 使用了基于 HTML 的模版语法，允许开发者声明式地将 DOM 绑定至底层 Vue 实例的数据。所有 Vue.js 的模板都是合法的 HTML ，所以能被遵循规范的浏览器和 HTML 解析器解析。

数据绑定最常见的形式就是使用 “Mustache” 语法（双大括号）的文本插值。

```html
<div id="app">
    <h1>{{ title }}</h1>
</div>
```

Mustache 标签将会被替代为对应数据对象上 `title` 属性的值。无论何时，绑定的数据对象上 `title` 属性发生了改变，插值处的内容都会更新。

> 属性显示直接写属性名称，像 `{{ this.title }}` 或 `{{ data.title }}` 都是错误的写法，只要属性在 `app` 作用域内，VueJs会自动解析属性

## methods返回字符串
Vue模板除了能显示属性数据之外，还可以显示方法返回的字符串。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue模板</title>
</head>
<body>
	<div id="app">
		<h1>{{ title }}</h1>
		<h1>{{ sayHello() }}</h1>
	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
 			data: {
 				title: 'hello Vue'
 			},
			methods: {
 			    sayHello(){
 			        return 'Hello';
				}
			}
 		});
 	</script>
</body>
</html>
```
## methods返回属性对象
在 `methods` 中除了返回字符串外，还可以返回当前作用域中的属性。

```html
<h1>{{ say() }}</h1>
...
var app = new Vue({
    el: '#app',
    data: {
        title: 'hello Vue'
    },
    methods: {
       ...
        say(){
            return this.title;
        }
    }
});
```