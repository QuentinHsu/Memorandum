# State

常规来讲，State 大都是在计算属性中使用。

## 基本用法：this.$store.state

以全局注入的方式，就是通过 `this.$store.state` 来获取 state 中存储的状态值。

## mapState 辅助函数

在不使用 mapState 辅助函数时，你需要用 `this.$store.state` 的繁琐方式才能获取存储在 Vuex State 中的状态值，虽然你可以暂存，但还是不够”优雅“。

使用 mapState 辅助函数，你可以更方便获取到 State。

而 mapState 辅助函数，大体上有两种用法：

* 用 mapState 函数”外包装“下 computed

```javascript
computed: mapState({

})
```

* 在 computed 内使用对象展开运算符”展开“ mapState 函数

```javascript
computed: {
  ...mapState({
    
  })
}
```



