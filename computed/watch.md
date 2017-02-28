# watch属性
虽然计算属性在大多数情况下更合适，但有时也需要一个自定义的 `watcher` 。这是为什么 `Vue` 提供一个更通用的方法通过 `watch` 选项，来响应数据的变化。当你想要在**数据变化响应时，执行异步操作或开销较大的操作**，这是很有用的。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue计算属性之watch</title>
</head>
<body>
	<div id="app">
		<button @click="counter++">增加 1</button>
		<button @click="counter--">减少 1</button>
		<button @click="counter++">计算属性增加 1</button>
		<p>Counter: {{ counter }}</p>
		<p>Result: {{ result() }}</p>
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
				counter: 0
			},
			computed: {
				output() {
					return this.counter > 5 ? 'Counter大于5' : 'Counter小于5';
				}
			},
			watch: {
				// counter: function(value){
				// 	var vm = this;
				// 	console.log(value);
				// 	if (value > 5) {
				// 		vm.counter = 0;
				// 	}
				// },
				// ES6简写模式
				counter(value){
					var vm = this;
					console.log(value);
					if (value > 5) {
						vm.counter = 0;
					}
				}
			},
			// 在 `methods` 对象中定义方法
			methods: {
				result() {
					return this.counter > 5 ? 'Counter大于5' : 'Counter小于5';
				}
			}
		});
	</script>
</body>
</html>
```