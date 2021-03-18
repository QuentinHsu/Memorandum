# Android

## WeChat

### WeChat App 内部的“字体”大小功能，会影响使用 REM 布局的网页。

WeChat App 内部的“字体”大小功能，会影响在 WeChat 内部打开的网页的 HTML 根节点字体大小，进而影响使用 REM 布局的网页。

哪怕你的网页是有通过动态计算来设置 HTML 根节点字体大小的，也会受 WeChat App 内部这个字体大小修改机制的影响。感觉是强制覆盖！

但幸好，有办法解决！

在你执行动态计算根节点字体大小前，执行下述代码：

```javascript
// 在 Android 平台，阻止微信修改 Web 字体大小
function preventWeChatModifyFontSizeForAndroid() {
    if (typeof WeixinJSBridge == "object" && typeof WeixinJSBridge.invoke == "function") {
      handleFontSize();
    } else {
      document.addEventListener("WeixinJSBridgeReady", handleFontSize, false);
    }
    function handleFontSize() {
      // 设置网页字体为默认大小
      WeixinJSBridge.invoke('setFontSizeCallback', { 'fontSize': 0 });
      // 重写设置网页字体大小的事件
      WeixinJSBridge.on('menu:setfont', function () {
        WeixinJSBridge.invoke('setFontSizeCallback', { 'fontSize': 0 });
      });
    }
};
preventWeChatModifyFontSizeForAndroid()
```

实测（20210318）有效！马上去更新生产环境！🙌

## 参考资料

* [移动端用户设置字体放大导致的问题](https://www.cnblogs.com/axl234/p/7753187.html)

