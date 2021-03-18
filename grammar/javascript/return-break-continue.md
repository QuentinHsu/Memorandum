# return, break, continue

## return

### 只能出现在函数体中！

> The return statement ends function execution and specifies a value to be returned to the function caller.
>
> return语句终止函数的执行，并返回一个指定的值给函数调用者。
>
> —— MDN

上述引用中所述的“返回一个指定的值“，并非是必须。

在函数体中使用 return 语句时，函数将会停止运行。无论你的 return 在该函数的哪个位置，哪怕是你在 return 外嵌套了多层的 if 语句，**一旦有一个 return 执行，那么剩下的语句将不再执行**。比如：

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

假如 return 出现在非函数体内的 JavaScript 代码中，将会报错：

```javascript
Uncaught SyntaxError: Illegal return statement
```

### 只会阻断自己所在的第一层函数

return，虽说能阻断函数的执行，但它仅仅**只能阻断自己所在的第一层函数**。

```javascript
function returnFunction(params) {
  console.log("执行了 returnFunction 函数")
  return
  console.log("假如你看到这条日志，那么 returnFunction 函数就没被阻断")
}
returnFunction()
```

比如，假如你将上述这个 _returnFunction_ 函数，放在另一个 _external_ 函数里执行：

```javascript
function returnFunction(params) {
  console.log("执行了 returnFunction 函数")
  return
  console.log("假如你看到这条日志，那么 returnFunction 函数就没被阻断")
}

function external(params) {
  returnFunction()
  console.log("external 函数被执行")
}
external()
```

那么，被阻断的只有函数 _returnFunction_，而函数 _external_ 如期被执行。

如果想函数 _external_ 因为函数 _returnFunction_ 的阻断而阻断，那么函数 _returnFunction_ 中的 return 需要返回一个“标志“，比如 `return false`，`return 1` ，以触发执行另一个 return。

```javascript
function returnFunction(params) {
  console.log("执行了 returnFunction 函数")
  return 1
  console.log("假如你看到这条日志，那么 returnFunction 函数就没被阻断")
}

function external(params) {
  if (returnFunction() === 1) {
    return
  }
  returnFunction()
  console.log("external 函数被执行")
}
external()
```

## break

### 不能直接出现在函数体中！

只能在循环（Loop）体，switch 或者 label 语句中使用，不能在函数体中直接使用。

![](../../.gitbook/assets/image%20%286%29.png)













