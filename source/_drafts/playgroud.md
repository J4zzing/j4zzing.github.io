---
title: playgroud
tags:
---

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



## Heart

### 目的

搞清楚整个过程，Connect the dots，联系积木定义，domain function在Heart里是如何运作的。

### 疑问

**Block_provider和Runtime_provider？**

Block Provider比Runtime Provider多一个config属性



**Responder 和lifetime responder？**



### 构想

去掉'rest-s'，换成Throw

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





```js
function on_message(event) {
  const { data } = event;
  let { result } = data;

  switch (data.eventName) {
    case 'webviewOnReady':
      console.log('webviewOnReady');
      break;
    case 'CUR_WORKSPACE_SVG':
      const body = document.querySelector('body');
      let lastChild = body.lastElementChild;
      result = JSON.parse(result);
        if (result.startsWith('<svg')) {
          if (lastChild instanceof SVGElement) {
            lastChild.outerHTML = result;
          } else {
            body.insertAdjacentHTML('beforeend', result);
          }
        } else {
          let img;
          if (lastChild instanceof Image) {
            img = lastChild;
          } else {
            img = new Image();
          }
          img.className = 'block-img';
          img.src = result;

          if (!(lastChild instanceof Image)){
            body.appendChild(img);
          }
        }
      break;
    case 'sendWorkspaceSvg':
      console.log('Received SVGs...');
      break;
    case 'loadSvgStatue':
      if (data.result) {
        console.log('All blocks has been generated.');
      } else {
        console.warn('Generating blocks svg did not finished correctlly.');
      }
      break;

    case 'playerOnReady':
      console.log('playerOnReady');
      break;
    case 'loadStatus':
      console.log('loadStatus', data.result);
      break;

    default:
      throw new Error('Unknow Event: ' + data.eventName);
  }
}

window.addEventListener('message', on_message, false);

temp1.contentWindow.postMessage({
  eventName: 'GET_CUR_WORKSPACE_SVG',
  // type: 'xml',
  // type: 'dataurl+ascii',
  // type: 'dataurl+base64',
  type: 'dataurl+png',
  scale: 5,
}, '*');
```

