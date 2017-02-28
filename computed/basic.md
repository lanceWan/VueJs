# 基础栗子
**为什么需要计算属性**
---
在模板中绑定表达式是非常便利的，但是它们实际上只用于简单的操作。在模板中放入太多的逻辑会让模板过重且难以维护。在这种情况下，模板不再简单和清晰。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue计算属性</title>
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
				output(){
					return this.counter > 5 ? 'Counter大于5' : 'Counter小于5';
				}
			},
     		 // 在 `methods` 对象中定义方法
			methods: {
              result(){
                  return this.counter > 5 ? 'Counter大于5' : 'Counter小于5';
				}
			}
 		});
 	</script>
</body>
</html>
```

**计算属性和methods区别**
---

你可能已经注意到我们可以通过调用表达式中的method来达到同样的效果。不经过计算属性，我们可以在 `methods` 中定义一个相同的函数来替代它。对于最终的结果，两种方式确实是相同的。然而，**不同的是计算属性是基于它的依赖缓存**。计算属性只有在它的相关依赖发生改变时才会重新取值。这就意味着只要 `counter` 没有发生改变，多次访问 `output` 计算属性会立即返回之前的计算结果，而不必再次执行函数。所以在巨大的数组遍历和做大量的计算的情况下，使用计算属性是最佳的选择。