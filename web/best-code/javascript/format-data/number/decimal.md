# Decimal

格式化小数

## 四舍五入正负小数

### 仅适用于小额数值

```javascript
/**
 * 四舍五入正负小数,并千分位
 * 仅适用于小额数值
 * @param {Number} value 待格式化数值
 * @param {Number} scale 保留小数位数 0~20
 */
function decimalRound(value, scale) {
  return Intl.NumberFormat("zh-CN", {
    maximumFractionDigits: scale
  }).format(value);
}
```

