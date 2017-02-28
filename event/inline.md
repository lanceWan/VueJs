# 内联处理方法
除了直接绑定到一个方法，也可以用内联 JavaScript 语句，传递参数。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue监听事件</title>
</head>
<body>
	<div id="app">
		<button v-on:click="add(2)"> 增加 2</button>
        <!-- `reduction` 是在下面定义的方法名 -->
        <button v-on:click="reduction">减少 1</button>
        <p>点击了 {{ counter }} 次</p>
	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
 			data: {
                counter: 0
 			},
            // 在 `methods` 对象中定义方法
			methods: {
                reduction(){
                    // `this` 在方法里指当前 Vue 实例
                    this.counter --;
                },
				add(step){
                    this.counter += step;
				}
			}
 		});
 	</script>
</body>
</html>
```