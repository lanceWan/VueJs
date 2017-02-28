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

# 属性绑定v-bind
Vue 在HTML 属性中使用时，不能使用 `Mustache ` 语法，需要使用 `v-bind` 命令。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue模板-属性绑定</title>
</head>
<body>
	<div id="app">
		<a v-bind:href="link" target="_blank">百度</a>
	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
 			data: {
 				link: 'http://baidu.com'
 			}
 		});
 	</script>
</body>
</html>
```
> 上面HTML属性 `v-bind:href` 可以简写为 `:href`

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

# v-html
双大括号会将数据解释为纯文本，而非 HTML 。为了输出真正的 HTML ，你需要使用 `v-html` 命令。

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

不能使用 `v-html` 来复合局部模板，因为 Vue 不是基于字符串的模板引擎。组件更适合担任 UI 重用与复合的基本单元。

> 你的站点上动态渲染的任意 HTML 可能会非常危险，因为它很容易导致 XSS 攻击。请只对可信内容使用 HTML 插值，绝不要对用户提供的内容插值。