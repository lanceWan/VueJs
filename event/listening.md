# 监听事件
在 `Vue` 中可以用 `v-on` 指令监听 `DOM` 事件来触发一些 `JavaScript` 代码。一些常用的 `Javascript` 事件基本上都支持。

![](image/20170213213800.jpg)

## 监听属性
```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue监听事件</title>
</head>
<body>
	<div id="app">
		<button v-on:click="counter ++"> 增加 1</button>
		<p>点击了 {{ counter }} 次</p>
	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
 			data: {
                counter: 0
 			}
 		});
 	</script>
</body>
</html>
```

> 监听属性一般用于最简单的情况。

## 方法事件处理器
许多事件处理的逻辑都很复杂，所以直接把 `JavaScript` 代码写在 `v-on` 指令中是不可行的。因此 `v-on` 可以接收一个定义的方法来调用。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue监听事件</title>
</head>
<body>
	<div id="app">
		<button v-on:click="counter ++"> 增加 1</button>
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
                }
			}
 		});
 	</script>
</body>
</html>
```