---
title: React pitfalls
date: 2020-06-02 21:55:15
tags:
- React
---

## Key

https://reactjs.org/docs/reconciliation.html#keys

https://codepen.io/pen?&editable=true&editors=0010

https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318



## React Hook

### useState

使用React函数组件的useState()钩子更新state的时候，不像类组件的this.setState一样会**合并**所作的更新，而是直接**替换**掉之前的内容。

```react
const funcComp = () => {
    const [obj, setObj] = useState({
        age: 18,
        name: 'John'
    });

    // 下面这条语句会覆盖整个obj对象，使name属性为undefined
    setObj({num: 19})
	// 可以采用Spread语法解决
    const o = obj;
    setObj({...o, num: 19});
}

```

参考：https://reactjs.org/docs/state-and-lifecycle.html#state-updates-are-merged

https://reactjs.org/docs/hooks-state.html#tip-using-multiple-state-variables

## useRef

ref不能再函数组件上使用，因为函数组件没有实例。