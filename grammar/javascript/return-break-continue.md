# return, break, continue

## return

### 只能出现在函数体中！

> The return statement ends function execution and specifies a value to be returned to the function caller.
>
> return语句终止函数的执行，并返回一个指定的值给函数调用者。
>
> —— MDN

上述引用中所述的“返回一个指定的值“，并非是必须。

在函数体中使用 return 语句时，函数将会停止运行。无论你的 return 在该函数的哪个位置，比如你嵌套了多层的 if 语句，**只要有一个执行，那么剩下的语句将不再执行**。比如：

```javascript
function returnTest(params) {
  console.log("开始执行函数");
  if (1) {
    console.log("第一个 第一层 if -- 开始");
    if (1) {
      console.log("进入第二层 -- if");
      console.log("接着，执行 return");
      return;
      console.log("执行完 return");
    }
    console.log("第一层 if -- 结束");
  }
  console.log("函数执行完成");
  if (1) {
    console.log("第二个 第一层 if");
  }
}
returnTest();
```

只会是输出：

```javascript
开始执行函数 
第一个 第一层 if -- 开始 
进入第二层 -- if 
接着，执行 return 
```

