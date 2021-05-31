# 常用正则表达式

## 匹配有首尾固定标志的内容

例如

```text
你看这个链接【链接:,www.xxx.com】能打开不？，或者试试这个链接【链接:,www.ccc.com】。
```

正则表达式

```javascript
const regex = /【链接:.*?】/
```

