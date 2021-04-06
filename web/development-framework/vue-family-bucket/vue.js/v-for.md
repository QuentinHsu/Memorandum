# v-for

### 两个在进行列表渲染的同级元素 <a id="66U1O"></a>

**两个在进行列表渲染的同级元素，两者之间的 :key 属性值需要避免重复**

大致的代码如下

```markup
<div>
    <div v-for="(item, index) for list1" :key="index">
    </div>
    <div v-for="(item, index) for list2" :key="index">
    </div>
</div>
```

虽然上述代码中的两个 index，来自不同的 list。但其中的值可能存在相同的，比如：

list1 的 index 的值为 1、2、3，而 list2 的 index 的值为 1、2、3，或者 list 2 的值至少与 list 1 的值有一个值相同，Vue 就会报错：

```text
Duplicate keys detected: 'xxx'. This may cause an update error.
found in 
```

其中的 xxx，为两个 index 之间相同的值。

**为避免此类型的报错，建议如下定义 index**

```markup
<div>
    <div v-for="(item, index) for list1" :key="'list1' + index">
  </div>
  <div v-for="(item, index) for list2" :key="'list2' + index">
    </div>
</div>
```

