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



## Vue父子组件通信

##### 父组件向子组件动态传值

> 一、watch监听并赋值

```javascript
watch:{
    id(val){
        this.val = val
    }
}
```

> 二、父组件通过$refs调用子组件的方法

```javascript
this.$refs.preview.setId(id)
```

##### 子组件向父组件通信

> 父组件

```html
<child @change="change"></child>
```

> 子组件

```javascript
this.$emit('change',this.id)
```



## 删除对象属性

```javascript
const params = JSON.parse(JSON.stringify(req.body,(key,value) => {
    if(key == '_id'){
        return undefined
    }else{
        return value
    }
}))
```



## 数组交集/差集

```javascript
//交集
let intersection = a.filter(v => b.includes(v))

//差集
let difference = a.concat(b).filter(v => !a.includes(v) || !b.includes(v))
```



## 数组对象交集/差集

```javascript
//交集
let intersection = a.concat(b).filter(v => a.some(x => x.id == v.id) === b.some(y => y.id == v.id))

//差集
let difference = a.concat(b).filter(v => ！a.some(x => x.id == v.id) || !b.some(y => y.id == v.id))
```



## 数组对象通过key去重

```javascript
function unique(arr,key) {
    let hash = {};

    return arr.reduce((item, next) => {
        hash[next[key]] ? '' : hash[next[key]] = true && item.push(next);
        return item
    }, [])
}
```

