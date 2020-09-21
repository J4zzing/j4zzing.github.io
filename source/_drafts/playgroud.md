---
title: playgroud
tags:
---

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



```js
// Blockly shortcut script
let mw = Blockly.mainWorkspace;
let wtd = Blockly.Xml.WorkspaceToDom;
let dtw = Blockly.Xml.DomToWorkspace;
let dtt = Blockly.Xml.DomToText;
let ttd = Blockly.Xml.TextToDom;
let dtpt = Blockly.Xml.DomToPrettyText;
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



