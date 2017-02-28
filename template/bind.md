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