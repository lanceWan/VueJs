# 按键修饰符
当监听键盘事件时，我们常常需要判断常用的 `key code`。Vue.js 提供了一个特殊的只能用在 `v-on` 指令的过滤器：`key`。它接收一个表示` key code` 的参数并完成判断。
记住所有的 keyCode 比较困难，所以 Vue 为最常用的按键提供了别名：

* `.enter`
* `.tab`
* `.delete` (捕获 “删除” 和 “退格” 键)
* `.esc`
* `.space`
* `.up`
* `.down`
* `.left`
* `.right`

> Vue2.10 新增按键修饰符

* `.ctrl`
* `.alt`
* `.shift`
* `.meta`

可以通过全局 `config.keyCodes` 对象自定义按键修饰符别名：

```html
// 可以使用 v-on:keyup.f1
Vue.config.keyCodes.f1 = 112
```

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue键盘修饰</title>
</head>
<body>
	<div id="app">
		<!--<input type="text" v-on:keyup.enter="alert($event)">-->
		<input type="text" v-on:keyup.alt.67="alert($event)">
	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
            // 在 `methods` 对象中定义方法
			methods: {
                alert(event){
                    alert(event.target.value);
				}
			}
 		});
 	</script>
</body>
</html>
```

## 为什么要在 HTML 中写监听器？
你可能注意到这种事件监听的方式违背了关注点分离（separation of concern）传统理念。不必担心，因为所有的 Vue.js 事件处理方法和表达式都严格绑定在当前视图的 `ViewModel` 上，它不会导致任何维护上的困难。实际上，使用 `v-on` 有几个好处：
* 扫一眼 HTML 模板便能轻松定位在 JavaScript 代码里对应的方法。
* 因为你无须在 JavaScript 里手动绑定事件，你的 ViewModel 代码可以是非常纯粹的逻辑，和 DOM 完全解耦，更易于测试。
* 当一个 ViewModel 被销毁时，所有的事件处理器都会自动被删除。你无须担心如何自己清理它们。