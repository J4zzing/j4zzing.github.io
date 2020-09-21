---
title: Blockly Notes
date: 2020-09-07 13:59:57
tags:
- Blockly
---


```js
// 继承
/**
 * Inherit the prototype methods from one constructor into another.
 *
 * @param {!Function} childCtor Child class.
 * @param {!Function} parentCtor Parent class.
 * @suppress {strictMissingProperties} superClass_ is not defined on Function.
 */
Blockly.utils.object.inherits = function(childCtor, parentCtor) {
  childCtor.superClass_ = parentCtor.prototype;
  childCtor.prototype = Object.create(parentCtor.prototype);
  childCtor.prototype.constructor = childCtor;
};
```

### Elegant code style

```js
var blocks = [1,2,3];
for (var i = 0, block; (block = blocks[i]); i++) {
  // statements
}
```






### Source code

```javascript
// Blockly.blockRendering.register

```



```ts
// Blockly/core/registry.js
declare var Blockly.registry.typeMap_ = {
  [type: Blockly.registry.Type.toString() | string]: {
    [name: string]: registryItem;
  }
}

declare type registryItem = new () => any;

declare interface Blockly.registry.Type = {
  name: 'renderer' | 'field' | 'toolbox' | 'theme';
  toString(): string;
}

```

Renderer, Theme, ToolBox, Field 作用与关系?



```javascript
// Blockly.core.contextMenu

```



```javascript
// Blockly.WidgetDiv

```





### Workspace Dom 格式

```xml
<xml xmlns="https://developers.google.com/blockly/xml">
  <block type="controls_if" id="@)FQM^]9]Ir@k6)U2!;I" inline="false" x="20" y="20">
    <mutation else="1"></mutation>
    <value name="IF0">
      <block type="logic_compare" id="}o.4{`w6qP;y,7P(BzQI">
        <field name="OP">EQ</field>
        <value name="A">
          <block type="math_arithmetic" id="_!mEs%JUg;R#Ny%a,u.z">
            <field name="OP">MULTIPLY</field>
            <value name="A">
              <block type="math_number" id="6`hrhB1Lj7~6:sBFmH!U">
                <field name="NUM">6</field>
              </block>
            </value>
            <value name="B">
              <block type="math_number" id="J?D1faW2DAcvD6mq5XZd">
                <field name="NUM">7</field>
              </block>
            </value>
          </block>
        </value>
        <value name="B">
          <block type="math_number" id="T4X^-hNOcPNb!`p*,:{I">
            <field name="NUM">42</field>
          </block>
        </value>
      </block>
    </value>
    <statement name="DO0">
      <block type="text_print" id="vn5.J1~,CVjGL2UtUCmC" inline="false">
        <value name="TEXT">
          <block type="text" id="D=atBZs@0tt5bJxsGE:_">
            <field name="TEXT">Don't panic</field>
          </block>
        </value>
      </block>
    </statement>
    <statement name="ELSE">
      <block type="text_print" id="zS]/FonsEs)a0gq~8z!k" inline="false">
        <value name="TEXT">
          <block type="text" id="rnt~=X9XnRfzBcQC53k?">
            <field name="TEXT">Panic</field>
          </block>
        </value>
      </block>
    </statement>
    <next>
      <block type="text_print" id="ev+alBj=7,$})cr+4W5t" inline="false">
        <value name="TEXT">
          <block type="text" id="--mQNqts@TRFbsrTws$B">
            <field name="TEXT">Cool..</field>
          </block>
        </value>
        <next>
          <block type="text_print" id="iV5+xL4yCuR0{3Y8/2`r" inline="false">
            <value name="TEXT">
              <block type="text" id="b62HA)[dWg_4i_{./FD9">
                <field name="TEXT">Cool..</field>
              </block>
            </value>
          </block>
        </next>
      </block>
    </next>
  </block>
</xml>
```

Block