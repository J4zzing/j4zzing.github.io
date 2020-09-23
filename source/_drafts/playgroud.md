---
title: playgroud
tags:
---

## Redux

https://redux.js.org/api/bindactioncreators

```js
// redux bindActionCreators
function bindActionCreators(actionCreatorMapObj:ActionCreatorsMapObject, dispatch:Dispatch<any>) {
  Object.entries(actionCreatorMapObj).forEach(([key, val]) => {
    actionCreatorMapObj[key] = (...args:any) => {
      dispatch(actionCreatorMapObj[key](...args));
    };
  });
}

```

## Blockly

```js
// Blockly shortcut script
let mw = Blockly.mainWorkspace;
let wtd = Blockly.Xml.workspaceToDom.bind(Blockly.Xml);
let dtw = Blockly.Xml.domToWorkspace.bind(Blockly.Xml);
let dtt = Blockly.Xml.domToText.bind(Blockly.Xml);
let ttd = Blockly.Xml.textToDom.bind(Blockly.Xml);
let dtpt = Blockly.Xml.domToPrettyText.bind(Blockly.Xml);
let xmlDoc = wtd(mw);
xmlDoc;
// or
let mw = Blockly.mainWorkspace;
let wtd = Blockly.xml.workspace_to_dom.bind(Blockly.xml);
let dtw = Blockly.xml.dom_to_workspace.bind(Blockly.xml);
let dtt = Blockly.xml.dom_to_text.bind(Blockly.xml);
let ttd = Blockly.xml.text_to_dom.bind(Blockly.xml);
let xmlDoc = wtd(mw);
xmlDoc;

let xxx = '<xml xmlns="http://www.w3.org/1999/xhtml"><block type="self_on_tap" id="0M6dLAetYIcypAKesH2q" inline="true" visible="visible" x="336" y="75"><field name="sprite">53d5b308-2d2d-4621-9769-6f3a46ca3de5</field><field name="type">mouse_click</field><next><block type="self_broadcast" id="RJ1RckqsO9YgzUQ5lZOA" inline="true" visible="visible"><field name="message">53d5b308-2d2d-4621-9769-6f3a46ca3de5</field></block></next></block></xml>';
let dom = ttd(xxx)
dom;
dtw(dom, mw);

```



## Heart

搞清楚整个过程，Connect the dots，联系积木定义，domain function在Heart里是怎么运作的。



### 构想

去掉'rest-s'如何？

### 优化

如何设计dom_compiler.ts的block_dom_to_json方法，使之可读性更高？

### Playgroud

```js
let blockXML = '<kitten><block type=\"start_on_click\" id=\"C24oVoAxUz7xoY}k^~yu\" inline=\"true\" x=\"210\" y=\"109\"><next><block type=\"TUTORIAL__signal\" id=\"_c-B|Vhx6Nt]2JyF~jIY\" inline=\"true\"></block></next></block></kitten>'

let p = new DOMParser();
let parsed = p.parseFromString(blockXML, "text/xml");

let blockDom = parsed.firstChild.firstChild;

```



https://developer.mozilla.org/en-US/docs/Web/API/DOMParser





函数式编程