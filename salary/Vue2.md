# Vue2

## Vue nextTick 实现原理

#### 作用：

- 在下次DOM更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的DOM。

#### 实现原理

- 此知识点涉及到了JS的运行机制（Event Loop）
  - JS是单线程的
  - JS的任务分为同步任务和异步任务：同步阻塞和异步非阻塞
  - JS的任务又分为宏任务和微任务
- 入参是一个回调函数，将回调函数挂载到任务栈中
- 挂载任务栈的使用优先级:`Promise > MutationObserver > setImmediate > setTomeout`
- `Promise` 和 `MutationObserver` 属于微任务
- 微任务通常来说就是在当前task执行结束后立即执行的任务，会在一个task执行结束后，在下一个task执行开始前，对页面重新进行渲染。

