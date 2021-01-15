---
title: playgroud
tags:
---

## Animation

https://easings.net/#easeOutElastic

```js
function easeOutElastic(x) {
    const c4 = (2 * Math.PI) / 3;
    
    return x === 0
        ? 0
        : x === 1
        ? 1
        : Math.pow(2, -10 * x) * Math.sin((x * 10 - 0.75) * c4) + 1;
}

let progress = [0, 0.16, 0.28, 0.44, 0.59, 0.73, 0.88, 1];
let values = progress.map(easeOutElastic);
```



## Redux

https://redux.js.org/api/bindactioncreators

```js
// createActionCreator
import { ActionCreator, Action } from 'redux';

function create_action_creator<P extends Object>(type:string) : ActionCreator<Action & P> {
  return (payload:P) => {
    return {
      type,
      ...payload,
    }
  }
}

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



### Playgroud

```js
let blockXML = '<kitten><block type=\"start_on_click\" id=\"C24oVoAxUz7xoY}k^~yu\" inline=\"true\" x=\"210\" y=\"109\"><next><block type=\"TUTORIAL__signal\" id=\"_c-B|Vhx6Nt]2JyF~jIY\" inline=\"true\"></block></next></block></kitten>'

let p = new DOMParser();
let parsed = p.parseFromString(blockXML, "text/xml");

let blockDom = parsed.firstChild.firstChild;

```



https://developer.mozilla.org/en-US/docs/Web/API/DOMParser

