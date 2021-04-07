# Sidebar 侧边导航

## v-for 不能作为 van-sidebar-item 的属性

```markup
<van-sidebar v-model="activeKey">
      <van-sidebar-item v-for="item in list"
                        :title="item.title"
                        :key="item.id"
                        @click="clickItem(item)" />
</van-sidebar>
```

![](../../../../.gitbook/assets/image%20%288%29.png)

### 解决方案

套一层 div 作为 van-sidebar-item 该组件的父元素，并将 v-for 作为其属性即可。

```markup
<van-sidebar v-model="activeKey">
      <div v-for="item in list">
        <van-sidebar-item :title="item.title"
                          :key="item.id"
                          @click="clickItem(item)" />
      </div>
</van-sidebar>
```



