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

#### 键盘事件

1:cc.SystemEvent.on(type, function, target, useCapture);

   type: cc.SystemEvent.EventType.KEY_DOWN  按键按下;
         cc.SystemEvent.EventType.KEY_UP 按键弹起; 

2: cc.SystemEvent.on(type, function, target, useCapture);

3: 监听的时候，我们需要一个cc.SystemEvent类的实例，我们有一个全局的实例cc.systemEvent,小写开头

3: 键盘回掉函数: function(event) {
      event.keyCode [cc.KEY.left, ...cc.KEY.xxxx]


#### 自定义事件

1:监听: this.node.on(“自定义事件名称”, function, target, useCapture);

2: 自派送: emit(“事件名称”, [detail]); 只有自己能够收到;

3: 冒泡派送: dispatchEvent(new cc.Event.EventCustom(“name”, 是否冒泡传递));


