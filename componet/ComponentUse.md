#### 组件入口函数

* 1: onLoad: 组件加载的时候调用, 保证了你可以获取到场景中的其他节点，以及节点关联的资源数据

* 2: start: 也就是第一次执行 update 之前触发

* 3: update(dt):组件每次刷新的时候调用,距离上一次刷新的时间(会在所有画面更新前执行)

* 4: lateUpdate(dt) 刷新完后调用(会在所有画面更新后执行);

* 5: onEnable: 启用这个组件的时候调用;

* 6: onDisable: 禁用这个组件的时候调用;

* 7: onDestroy: 组件实例销毁的时候调用;


#### cc.Component属性

* 1: 组件类: 所有组件的基类;

* 2: node: 指向这个组件实例所挂载的这个节点(cc.Node);

* 3: name: 这个组件实例所挂载的节点的名字<组件的名字>;

* 4: properties: { 
    } 属性列表;

    (1) name: value, 数,bool, 字符串;

    (2) 位置,颜色, 大小:  cc.p(0, 0), cc.color(0, 0), cc.size(100, 100)

    (3) 组件: {
           type: 组件类型, 系统类型，也可以require自己编写的组件类型
           default: null or [] 
     }

    (4)其他: 打开cocos creator源码，找到参考，然后移动到你的代码里面;

#### 组件添加查找删除


* 1:  addComponent(组件的类型): 向节点上添加一个组件实例, 返回添加好的组件实例;

* 2:  getComponent(组件类型): 查找一个为指定类型的组件实例(如果有多个，第一个匹配);

* 3: getComponents(组件类型): 查找这个节点上所有这个类型的组件实例;

    [inst1, inst2, inst3, ...]

* 4: getComponentInChildren(组件类型):  在自己与孩子节点里面查找;

* 5: getComponentsInChildren (组件类型): 在自己与孩子节点里面查找;

* 6: destroy(): 从节点中删除这个组件的实例;

#### Shedule定时器操作

* 1:  sheduleOnce(函数, time): time秒后启动一次定时器;

* 2: schedule(函数, time, 次数,  多长时间后开始); 执行的次数为(次数 + 1)， cc.macro.REPEAT_FOREVER

* 3: unschedule(函数); // 取消这个定时器操作;

* 4: unscheduleAllCallbacks  取消所有的定时器操作;

**注意，如果节点或组件没有激活是不会调用的;**


