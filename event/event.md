### cc.Node事件响应

#### 触摸事件

* 1: 触摸事件类型: START, MOVED, ENDED(物体内), CANCEL(物体外);

* 2: 监听触摸事件: node.on(类型, callback, target(回掉函数的this), [useCapture]);

* 3: 关闭触摸事件: node.off(类型, callback, target(回掉函数的this), [useCapture]);

* 4: targetOff (target): 移除所有的注册事件;

* 5: 回掉函数的参数设置  function(t(cc.Touch))

* 6: cc.Touch: getLocation返回触摸的位置;getDelta返回距离上次的偏移;

* 7: cc.Event: stopPropagationImmediate/stopPropagation 停止事件的传递;

* 8: 事件冒泡: 触摸事件支持节点树的事件冒泡,会从当前前天往上一层一层的向父节点传送;

* 9: 完成物体跟随手指触摸的案例;
