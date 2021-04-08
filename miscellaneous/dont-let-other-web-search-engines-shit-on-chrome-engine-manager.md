# 不要让其他网页的搜索引擎在 Chrome 引擎管理里拉屎

你可能在 Chrome 这个地址页面 chrome://settings/searchEngines 的“其他搜索引擎”项目下见到几十个，或者上百个第三方网页搜索引擎选项，甚至是几百个。虽然这个页面几乎一年都不见得打开几次。但有这些没必要的“其他搜索引擎”选项，心里就觉得膈应，觉得“不干净”。

![](../.gitbook/assets/image%20%289%29.png)

**让我们来解决这种拉屎的行为！**

## 清除已有的“其他搜索引擎”

一个个删，可行，但不太现实。  
能批量删除的，就批量删除。

但 Chrome 不提供批量删除的选项……  
那就用代码吧！

自己写代码也不太现实，能有现成的，就用现成的。  
可 Chrome 一直在迭代，所以代码具有时效性。  
截止 2021年4月8日，自测可行的代码，如下：  
原文地址：[https://superuser.com/a/1627512](https://superuser.com/a/1627512)

```javascript
var engineList=document.querySelector("body > settings-ui").shadowRoot.querySelector("#main").shadowRoot.querySelector("settings-basic-page").shadowRoot.querySelector("#basicPage > settings-section.expanded > settings-search-page").shadowRoot.querySelector("#pages > settings-subpage > settings-search-engines-page").shadowRoot.querySelector("#otherEngines")
function get_engines_list() {
    return engineList.shadowRoot.querySelector("#container").children[0].children;
}
function get_engine_count(){
    // "Templates" is first entry.
    return get_engines_list().length - 1;
}
var i;
for (i = 1; i <= get_engine_count(); i++) {
    var entry=get_engines_list()[i]
    var engineName = entry.shadowRoot.querySelector('.list-item').querySelector('#name-column').childNodes[1].innerText;
    if(!engineName.includes("(KEEP)")){
        entry.shadowRoot.querySelector("#delete").click();
    }
}
```

将上述代码在 `chrome://settings/searchEngines` 页面的控制台运行。  
运行一次仅能删除一部分，根据情况手动运行多次，直至清除完全。  
该代码，仅在 Chrome 中有效，在  [Chromium](https://www.chromium.org/) 版的 Microsoft Edge 不适用。

## 阻断这种拉屎的行为

看了下网上的说法，这种拉屎的行为是浏览器的“自作主张”……

安装 **Don't add custom search engines** 这个插件，就可以有效阻断这种自作主张。

[https://github.com/gregsadetsky/chrome-dont-add-custom-search-engines](https://github.com/gregsadetsky/chrome-dont-add-custom-search-engines)  


