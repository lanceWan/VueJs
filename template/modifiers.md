# modifiers
在事件处理程序中调用 `event.preventDefault()` 或 `event.stopPropagation()` 是非常常见的需求。尽管我们可以在 `methods` 中轻松实现这点，但更好的方式是：`methods` 只有纯粹的数据逻辑，而不是去处理 `DOM` 事件细节。
为了解决这个问题， Vue.js 为 `v-on` 提供了 事件修饰符。通过由点(.)表示的指令后缀来调用修饰符。
* `.stop`
* `.prevent`
* `.capture`
* `.self`
* `.once`

> preventDefault() : 该方法将通知 Web 浏览器不要执行与事件关联的默认动作（如果存在这样的动作）。例如，如果 type 属性是 "submit"，在事件传播的任意阶段可以调用任意的事件句柄，通过调用该方法，可以阻止提交表单。注意，如果 Event 对象的 cancelable 属性是 fasle，那么就没有默认动作，或者不能阻止默认动作。无论哪种情况，调用该方法都没有作用。

> stopPropagation() : 该方法将停止事件的传播，阻止它被分派到其他 Document 节点。在事件传播的任何阶段都可以调用它。注意，虽然该方法不能阻止同一个 Document 节点上的其他事件句柄被调用，但是它可以阻止把事件分派到其他节点。

> .once Vue2.1.4 版本新增

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue事件修饰</title>
</head>
<body>
	<div id="app">
		<p v-on:mousemove="updateMove">
			坐标：{{ x }} / {{ y }}
			--
			<!--<span v-on:mousemove="stopMove">停止</span>-->
			<span v-on:mousemove.stop="stopMove">停止</span>
		</p>
	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
			data: {
				x: 0,
				y: 0,
			},
            // 在 `methods` 对象中定义方法
			methods: {
                updateMove(event){
					this.x = event.clientX;
					this.y = event.clientY;
				},
                stopMove(event){
					//操作原生 DOM 事件
					event.stopPropagation();
				}
			}
 		});
 	</script>
</body>
</html>
```