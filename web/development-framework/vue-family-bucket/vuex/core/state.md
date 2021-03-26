# State

常规来讲，State 大都是在计算属性中使用。

## 基本用法：this.$store.state

以全局注入的方式，就是通过 `this.$store.state` 来获取 state 中存储的状态值。

## mapState 辅助函数

在不使用 mapState 辅助函数时，你需要用 `this.$store.state` 的繁琐方式才能获取存储在 Vuex State 中的状态值，虽然你可以暂存，但还是不够”优雅“。

使用 mapState 辅助函数，你可以更方便地获取到 State。

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

注意，像上述两种方式，不在其中显式地引入具体的 State 状态，是无法使用其状态值的。mapState 函数只是提供一个可以引入 State 状态的“环境”，想使用具体的 State 状态，还需要我们**按需引入**。

### 按需引入

* 箭头函数

```javascript
countAlias：state => state.count
```

* 传 State 同名字符串

```javascript
countAlias: 'count'
// 'count' 等同于 state => state.count

// 假如你依旧使用跟 state 状态名一样的字段，那么你可以这样简写:
'count'
```



使用上述两种引入方式，其引用的状态将被挂载到当前组件 this（局部），使其能被访问和使用，且**仅在当前组件中有效**。没被在此按需引用的，将不能通过 this 访问。

```javascript
computed: {
  ...mapState({
    countAlias: 'count',
  }),
  countResult() {
    return 'this is countResult: ' + this.countAlias
  },
},
```

