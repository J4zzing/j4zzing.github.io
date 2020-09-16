---
title: Vim参考手册
date: 2020-06-10 17:03:16
tags:
- Vim
---

## Cheat Sheet

```vim
:set number
:set nonumber
:set relativenumber
:set norelativenum
```

https://jeffkreeftmeijer.com/vim-number/

## VsCode 设置

```json
{
  "editor.lineNumbers": "relative",
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.tslint": true
  },
  "window.zoomLevel": 0,
  "vim.normalModeKeyBindingsNonRecursive": [
    {
      "before": ["<space>"],
      "commands": ["workbench.action.files.save"]
    },
    {
      "before": ["<leader>", "w"],
      "commands": ["workbench.action.splitEditor"]
    }
  ]
}
```



## 学习

Learn vim script the hard way

https://learnvimscriptthehardway.stevelosh.com/

键 映射

https://learnvimscriptthehardway.stevelosh.com/chapters/03.html

快速移动

https://medium.com/usevim/vim-101-quick-movement-c12889e759e0

Register

`:reg`

https://www.brianstorti.com/vim-registers/

Leader key

https://medium.com/usevim/vim-101-what-is-the-leader-key-f2f5c1fa610f

## 插件

[Vim surround](https://github.com/tpope/vim-surround)

[vim-xkbswitch](https://github.com/lyokha/vim-xkbswitch)

vscode vim

https://medium.com/@hoitz/improved-vim-setup-in-visual-studio-code-bc579501b80c

```json
"vim.normalModeKeyBindingsNonRecursive": [
  {
    "before": ["<space>"],
    "commands": ["workbench.action.files.save"]
  }
]
```



## 书

https://www.amazon.com/Practical-Vim-Edit-Speed-Thought/dp/1680501275/ref=as_li_ss_tl?ie=UTF8&qid=1501817867&sr=8-3&keywords=vim&linkCode=sl1&tag=caspbeye-20&linkId=6c394064b4e6f05b198e68c64a6f4d76

## 配件

HHKB

https://www.amazon.com/HRH-Functional-Shortcuts-Keyboard-Silicone/dp/B01MFXLBO9/ref=as_li_ss_tl?_encoding=UTF8&pd_rd_i=B01MFXLBO9&pd_rd_r=MQ0G7GR3ZTR44DX0N0DX&pd_rd_w=EVMod&pd_rd_wg=43zpB&psc=1&refRID=MQ0G7GR3ZTR44DX0N0DX&linkCode=sl1&tag=caspbeye-20&linkId=6fa29a44e25b23a14f53e215fa219845

## 其他资料

http://vimcasts.org/