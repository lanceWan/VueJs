# 绑定数组形式
我们可以把一个数组传给 `v-bind:class` ，以应用多个class样式。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue绑定class</title>
	<style>
		.demo{
			width: 100px;
			height: 100px;
			background-color: gray;
			display: inline-block;
		}
        .red{
            background-color: red;
        }

        .purple{
            background-color: purple;
        }
        .pink{
            background-color: pink;
        }
	</style>
</head>
<body>
	<div id="app">
		<div class="demo" @click="attachRed = !attachRed" :class="{red : attachRed}"></div>
		<div class="demo" @click="attachRed = !attachRed" :class="divClass"></div>
		<div class="demo" :class="[color, {purple: attachRed}]"></div>
		<hr>
		<input type="text" v-model="color">
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
                attachRed: false,
				color: 'pink'
			},
			computed: {
			    divClass(){
			        return {
                        red: this.attachRed,
                        purple: !this.attachRed
					}
				}
			}

		});
	</script>
</body>
</html>
```