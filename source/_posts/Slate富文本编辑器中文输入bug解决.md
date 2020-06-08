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



https://github.com/ianstormtaylor/slate/compare/v0.47...rockhamx:v0.47



## 理解

### DOM Selection对象

https://developer.mozilla.org/en-US/docs/Web/API/Selection

### Slate Selection对象

https://github.com/ianstormtaylor/slate/blob/v0.47/docs/reference/slate/selection.md

Selection实现Range

https://github.com/ianstormtaylor/slate/blob/v0.47/docs/reference/slate/range.md

####  属性



在控制台中添加onSelectionChange Listener：

```javascript
document.addEventListener('selectionchange', () => {
  console.log(document.getSelection());
});
```

然后随便点击或选择文本查看输出的Selection对象。



## 源码解释

```javascript
class Content extends React.component {
  ...
  updateSelection = () => {
    const { editor } = this.props
    const { value } = editor
    const { selection } = value
    const { isBackward } = selection
    const window = getWindow(this.ref.current)
    const native = window.getSelection()
    // document.activeElement返回当前focus的元素。如果一个可编辑的对象(<input>, <textarea>, contentEditable元素)里有文本被选择，那么它会返回这个元素。
    // 见 https://developer.mozilla.org/en-US/docs/Web/API/DocumentOrShadowRoot/activeElement
    const { activeElement } = window.document

    if (debug.update.enabled) {
      debug.update('updateSelection', { selection: selection.toJSON() })
    }

    // COMPAT: In Firefox, there's a but where `getSelection` can return `null`.
    // https://bugzilla.mozilla.org/show_bug.cgi?id=827585 (2018/11/07)
    if (!native) {
      return
    }

    const { rangeCount, anchorNode } = native
    let updated = false

    // If the Slate selection is blurred, but the DOM's active element is still
    // the editor, we need to blur it.
    if (selection.isBlurred && activeElement === this.ref.current) {
      this.ref.current.blur()
      updated = true
    }

    // If the Slate selection is unset, but the DOM selection has a range
    // selected in the editor, we need to remove the range.
    // However we should _not_ remove the range if the selection as
    // reported by `getSelection` is not equal to `this.tmp.nativeSelection`
    // as this suggests `onNativeSelectionChange` has not triggered yet (which can occur in Firefox)
    // See: https://github.com/ianstormtaylor/slate/pull/2995

    const propsToCompare = [
      'anchorNode',
      'anchorOffset',
      'focusNode',
      'focusOffset',
      'isCollapsed',
      'rangeCount',
      'type',
    ]

    let selectionsEqual = true

    for (const prop of propsToCompare) {
      if (this.tmp.nativeSelection[prop] !== native[prop]) {
        selectionsEqual = false
      }
    }

    if (
      selection.isUnset &&
      rangeCount &&
      this.isInEditor(anchorNode) &&
      selectionsEqual
    ) {
      removeAllRanges(native)
      updated = true
    }

    // If the Slate selection is focused, but the DOM's active element is not
    // the editor, we need to focus it. We prevent scrolling because we handle
    // scrolling to the correct selection.
    if (selection.isFocused && activeElement !== this.ref.current) {
      this.ref.current.focus({ preventScroll: true })
      updated = true
    }

    // Otherwise, figure out which DOM nodes should be selected...
    if (selection.isFocused && selection.isSet) {
      const current = !!native.rangeCount && native.getRangeAt(0)
      const range = editor.findDOMRange(selection)

      if (!range) {
        warning(
          false,
          'Unable to find a native DOM range from the current selection.'
        )

        return
      }

      const { startContainer, startOffset, endContainer, endOffset } = range

      // If the new range matches the current selection, there is nothing to fix.
      // COMPAT: The native `Range` object always has it's "start" first and "end"
      // last in the DOM. It has no concept of "backwards/forwards", so we have
      // to check both orientations here. (2017/10/31)
      if (current) {
        if (
          (startContainer === current.startContainer &&
            startOffset === current.startOffset &&
            endContainer === current.endContainer &&
            endOffset === current.endOffset) ||
          (startContainer === current.endContainer &&
            startOffset === current.endOffset &&
            endContainer === current.startContainer &&
            endOffset === current.startOffset)
        ) {
          return
        }
      }

      // Otherwise, set the `isUpdatingSelection` flag and update the selection.
      updated = true
      this.tmp.isUpdatingSelection = true
      removeAllRanges(native)

      // COMPAT: IE 11 does not support `setBaseAndExtent`. (2018/11/07)
      if (native.setBaseAndExtent) {
        // COMPAT: Since the DOM range has no concept of backwards/forwards
        // we need to check and do the right thing here.
        if (isBackward) {
          native.setBaseAndExtent(
            range.endContainer,
            range.endOffset,
            range.startContainer,
            range.startOffset
          )
        } else {
          native.setBaseAndExtent(
            range.startContainer,
            range.startOffset,
            range.endContainer,
            range.endOffset
          )
        }
      } else {
        native.addRange(range)
      }

      // Only scroll to selection when a user action is performed
      if (editor.userActionPerformed() === true) {
        // Scroll to the selection, in case it's out of view.
        scrollToSelection(native)
      }

      // Then unset the `isUpdatingSelection` flag after a delay, to ensure that
      // it is still set when selection-related events from updating it fire.
      setTimeout(() => {
        // COMPAT: In Firefox, it's not enough to create a range, you also need
        // to focus the contenteditable element too. (2016/11/16)
        if (IS_FIREFOX && this.ref.current) {
          this.ref.current.focus()
        }

        this.tmp.isUpdatingSelection = false

        debug.update('updateSelection:setTimeout', {
          anchorOffset: window.getSelection().anchorOffset,
        })
      })
    }

    if (updated && (debug.enabled || debug.update.enabled)) {
      debug('updateSelection', { selection, native, activeElement })

      debug.update('updateSelection:applied', {
        selection: selection.toJSON(),
        native: {
          anchorOffset: native.anchorOffset,
          focusOffset: native.focusOffset,
        },
      })
    }
  }
  ...
}
```

## 总结

该解决方法只在Chrome上测试过。

暂时不想继续深究原因了...

## 参考文章

https://medium.com/articode/fixing-broken-npm-packages-d8f808657d8e

https://docs.npmjs.com/cli-commands/link.html

https://classic.yarnpkg.com/en/docs/workspaces/

https://en.wikipedia.org/wiki/Monorepo