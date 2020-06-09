---
title: Slate富文本编辑器中文输入bug解决
date: 2020-06-06 23:49:05
tags:
- React
- Slate
---

## 版本

V0.47.9

### 相关Issues

https://github.com/ianstormtaylor/slate/issues/2368

https://github.com/ianstormtaylor/slate/pull/2415

https://github.com/ianstormtaylor/slate/pull/2454

https://github.com/ianstormtaylor/slate/issues/2457

https://segmentfault.com/a/1190000019133673

## 解决方法

### 前提

Slate数据模型中的Node：这是Slate模仿DOM自主管理的数据，

同时Slate定义了Document、Block、Inline、Text继承Node。

请看下图解释。



Node的数据结构如下：



### 相关资料

#### DOM Selection对象

https://developer.mozilla.org/en-US/docs/Web/API/Selection

#### Slate Selection对象

https://github.com/ianstormtaylor/slate/blob/v0.47/docs/reference/slate/selection.md

Selection实现Range

https://github.com/ianstormtaylor/slate/blob/v0.47/docs/reference/slate/range.md



在控制台中添加onSelectionChange Listener：

```javascript
document.addEventListener('selectionchange', () => {
  console.log(document.getSelection());
});
```

然后随便点击或选择文本查看输出的Selection对象。



## 解决方法



### 解决历程

首先可能是浏览器会在输入中文时重新定位键盘光标（caret，以下统称光标），从而触发onSelect事件，

由于英文输入不在这种问题，以下讨论输入时均指中文输入。

```javascript
// ...\slate-react\src\components\content.js
class Content extends React.component {
  ...
  	onEvent(handler, event) {
  	...
    if (!IS_ANDROID && handler === 'onSelect') {
      const { editor } = this.props
      const { value } = editor
      const { selection } = value
      const window = getWindow(event.target)
      const domSelection = window.getSelection()
      const range = editor.findRange(domSelection)
      // 通过调试得知，在一个Node的结尾输入中文时，键盘光标会出现bug，而在其他地方输入则不会。在Node末尾输入中文时，range中的offset与domSelection中的不一致。如下图对比。
      console.log(range.anchor.offset);

      if (range && range.equals(selection.toRange())) {
        this.updateSelection()
        return
      }
    }
  	...
  }
  ...
}
```

![光标一致](C:\Users\Rockh\AppData\Roaming\Typora\typora-user-images\1591671154049.png)

![光标不一致](C:\Users\Rockh\AppData\Roaming\Typora\typora-user-images\1591671095180.png)



我想解决方法有两个方向。

- 一是找出为什么中文输入会触发onSelect事件并制止它
- 二是找出在段尾输入会导致光标不一致而在其他地方则不会的原因

选择第一个更合理些，但这里我首先选择了第二种方向。

> ```javascript
> // 目的：找到finRange调用栈中发生差异的方法
> const range = editor.findRange(domSelection)
> ```

最后找到差异发生在这里：

```javascript
// ...\slate\packages\slate\src\models\point.js
...
  normalize(node) {
    ...
    let target = path && node.getNode(path)
    ...
    let point = this.merge({
      key: target.key,
      path: path == null ? node.getPath(target.key) : path,
      offset: offset == null ? 0 : Math.min(offset, target.text.length),
    })
    ...
    return point
    ...
  }
```

请看`Math.min(offset, target.text.length)`，这里的`target`是一个Text Node，此时Slate内部数据还没有和DOM同步，还处在输入之前的状态，所以由于`target.text.length`限制，最大不会超过这个数值。

当在除Node末尾输入时，`offset`的值不会超过`target.text.length`，返回`Point`后，由于`offset`和`target.text.length`两个永远不会等于Slate内部对应的Point的offset。

当在Node末尾输入时，`offset`的值**一定**会等于`target.text.length`，导致返回的`Point`，一定**会和Slate内部对应的Point相等，从而满足条件：

```javascript
      // selection是存储在Slate内部的数据，range为从DOM Selection推断的Range，它出现了问题。
      if (range && range.equals(selection.toRange())) {
        this.updateSelection()
        return
      }
```

从而调用不该调用的updateSelection方法，并使光标重置。

尝试做如下改变：

```javascript
// ...\slate\packages\slate\src\models\point.js
...
  normalize(node) {
    ...
    let point = this.merge({
      key: target.key,
      path: path == null ? node.getPath(target.key) : path,
      offset: offset == null ? 0 : offset,
    })
    ...
  }
```

**至此光标恢复正常：**

![正常状态](C:\Users\Rockh\AppData\Roaming\Typora\typora-user-images\1591679334365.png)

至于为什么没有和DOM同步？有没有更好的解决方案？按照第一种思路来改怎么做?

以后再说吧...

希望以后找bug不要像无头苍蝇一样乱撞，一定要静下心来思考问题可能出现在哪。

https://github.com/ianstormtaylor/slate/compare/v0.47...rockhamx:v0.47



## 参考文章

https://medium.com/articode/fixing-broken-npm-packages-d8f808657d8e

https://docs.npmjs.com/cli-commands/link.html

https://classic.yarnpkg.com/en/docs/workspaces/

https://en.wikipedia.org/wiki/Monorepo