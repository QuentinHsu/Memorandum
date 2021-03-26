# Getters

{% hint style="info" %}
类似于 Vue.js 中的计算属性。在大部分情况下，getter 的返回值会根据它的依赖被缓存起来，且只有当它的依赖值发生了改变才会被重新计算。但注意，getter 在通过方法访问时，每次都会去进行调用，而不会缓存结果。
{% endhint %}

## 访问 Getter

### 通过属性访问

* 如同 State 一样，Getters 会暴露为 `store.getters` 对象。以此可访问属性的方式访问具体的 getter。

```javascript
this.$store.getters
```

Getter 也可以接受其他 getter 作为第二个参数：

```javascript
getters: {
  // ...
  doneTodosCount: (state, getters) => {
    return getters.doneTodos.length
  }
}
```

### 通过方法访问



