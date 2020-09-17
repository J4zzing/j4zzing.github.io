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
```

