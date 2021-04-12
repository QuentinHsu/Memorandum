# 取消 Chrome Console 中的 SourceMap 警告⚠

## DevTools failed to load SourceMap: Could not load content for chrome-extension <a id="articleContentId"></a>

![](../.gitbook/assets/image%20%2813%29.png)

本地开发的时候会在 Chrome Console 中发现这个关于 SourceMap，但项目中并没有用 SourceMap。最初以为是项目配置的原因，后面发现是 Chrome Console 设置问题。

### 解决

Chrome =&gt; Console =&gt; Settings =&gt; Preferences =&gt; Sources

取消勾选下列两项，即可解决。

* Enable JavaScript source maps
* Enable CSS source maps

![](../.gitbook/assets/image%20%2810%29.png)

![](../.gitbook/assets/image%20%2812%29.png)

