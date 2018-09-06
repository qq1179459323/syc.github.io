---
title: React 简单整理
date: 2018-08-02 15:15:30
tags:react
---
### 1. React的生命周期
###  组件生命周期的三种状态展示： 
- Mounting: 已插入了真是dom结构 
- Updating: 正在被重新渲染 
- Unmounting: 已移出了真实dom结构

### 2.关于 生命周期的处理函数（will表示进入状态之前调用，did表示进入状态之后调用）：
- **componentWillMount()** :
组件将要渲染到真实dom节点；执行一次，在初始化render之前执行，如果在这个方法内调用setState，render()知道state发生变化，并且只执行一次
- **componentDidMount()**
//组件已经渲染到真实dom节点；在初始化render之后只执行一次，在这个方法内，可以访问任何组件，componentDidMount()方法中的子组件在父组件之前执行；
从这个函数开始，就可以和 js 其他框架交互了，例如设置计时 setTimeout 或者 setInterval，或者发起网络请求
- **componentWillUpdate()**//当props和state发生变化，组件将要被重新渲染；并且在render方法之前执行，当然初始化render时不执行该方法，需要特别注意的是，在这个函数里面，你就不能使用this.setState来修改状态。这个函数调用之后，就会把nextProps和nextState分别设置到this.props和this.state中。紧接着这个函数，就会调用render()来更新界面了
- **componentDidUpdate()**//组件已经完成重新渲染；在初始化render时不执行
- **componentWillUnmout()**//卸载组件，比如跳转路由的时候
- **componentWillReceiveProps()** //已经加载组件props发生改变的时候调用；在这个回调函数里面，你可以根据属性的变化，通过调用this.setState()来更新你的组件状态，旧的属性还是可以通过this.props来获取,这里调用更新状态是安全的，并不会触发额外的render调用
- **shouldComponentUpdate()**//组件判断是否要重新渲染的时候调用；在初始化render时不会执行，当props或者state发生变化时执行，并且是在render之前，当新的props或者state不需要更新组件时，返回false
#### 3. 关于组件生命周期的执行顺序 如下图所示：
![image](https://note.youdao.com/yws/public/resource/ab2cc4cb6abd27779a98343b11256d86/xmlnote/D3F2B8C7A6A04D8F99722AF34EEA9F36/851A0C31E6A749EB948EE8F6B5C6E006/88)
### 3.react中遇到的坑和一些小的知识点:
#### - setState()是异步的:
this.setState()会调用render方法，但并不会立即改变state的值，state是在render方法中赋值的。
所以执行this.setState()后立即获取state的值是不变的。
同样的直接赋值state并不会出发更新，因为没有调用render函数。
#### - 组件的生命周期
componentWillMount，componentDidMount 只有在初始化的时候才调用。
componentWillReceivePorps，shouldComponentUpdate，componentWillUpdata，componentDidUpdate 只有组件在更新的时候才被调用，初始化时不调用。
#### - reducer必须返回一个新的对象才能出发组件的更新
因为在connect函数中会对新旧两个state进行浅对比，如果state只是值改变但是引用地址没有改变，connect会认为它们相同而不触发更新。
#### - 无论reducer返回的state是否改变，subscribe中注册的所有回调函数都会被触发。
#### - 组件命名的首字母必须是大写，这是类命名的规范。
#### - 组件卸载之前，加在dom元素上的监听事件，和定时器需要手动清除，因为这些并不在react的控制范围内，必须手动清除。
#### - 按需加载时如果组件是通过export default 暴露出去，那么require.ensure时必须加上default。

```
require.ensure([], require => {
    cb(null, require('../Component/saleRecord').default)
},'saleRecord')
```
#### - react的路由有hashHistory和browserHistory，hashHistory由hash#控制跳转，一般用于正式线上部署，browserHistory就是普通的地址跳转，一般用于开发阶段。
#### - 标签里用到的，for 要写成htmlFor，因为for已经成了关键字。
#### - componentWillUpdate中可以直接改变state的值，而不能用setState。
#### - 如果使用es6class类继承react的component组件，constructor中必须调用super，因为子类必须用super继承component的this，否则实例化的时候会报错。
#### - 组件卸载之前，加在dom元素上的监听事件，和定时器需要手动清除，因为这些并不在react的控制范围内，必须手动清除。指的是在this.refs.xxx这种真实dom上addEventListener这样添加的监听事件，在组件卸载的时候要手动清除(removeEventListener)，react组件上的onClick这种不用管，react帮我们处理好了
