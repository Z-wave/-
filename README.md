## axios单个请求添加header

```javascript
this.$axios({
    method: 'post',
    url: '/api/xxx',
    headers: {
        'token': token,
    }
}).then(res => {})
```

## Webpack按需拆分代码(异步加载组件)

`() => import()`

*ECMAScript推荐使用*


```javascript
() => import(/* webpackChunkName: "linkface" */ './components/linkface.vue')
```

> 魔术注释指定chunkName
>



`require.ensure()`

*webpack特有属性*

```javascript
resolve => require.ensure([], () => resolve(require('./components/linkface.vue')), "linkface")
```

