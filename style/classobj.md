# 绑定对象形式
我们可以传给 `v-bind:class` 一个对象，以动态地切换 `class` 。

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
		<div class="demo"></div>
		<div class="demo"></div>
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
                attachRed: false
			}

		});
	</script>
</body>
</html>
```

上面的语法表示 `red` 的更新将取决于数据属性 `attachRed` 是否为真值 。我们也可以在对象中传入更多属性用来动态切换多个 class 。

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
		<div class="demo"></div>
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
                attachRed: false
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

> 对象中 `key` 为class样式名称，`value` 为判断是否应用这个class的条件