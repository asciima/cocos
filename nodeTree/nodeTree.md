#### 场景树

<image src="/img/nodeTree.png" />

* 1: creator是由一个一个的游戏场景组成，通过代码逻辑来控制场景跳转;

* 2: creator场景是一个树形结构;

* 3: 父节点, 孩子节点;

* 4: cc.Node就是场景树中的节点对象。

* 5: 每个节点只要在场景里面，所以任何一个节点都是一个cc.Node;

#### cc.Node属性

* 1:  name: 获取节点的名字

* 2: active: 设置节点的可见性;

* 3: position: 相对坐标,参照物是父亲节点;

* 4: rotation: 旋转,顺时针为正, 数学逆时针为正;

* 5: scale:  缩放;

* 6: anchor: 锚点, 左下角(0, 0), 右上角(1, 1) 可以超过这个范围可以

* 7: Size: 大小

* 8: Color: 环境颜色;

* 9: Opacity: 透明度,

* 10: Skew: 扭曲;

* 11: Group: 分组;

* 12: parent: 父亲节点的cc.Node;

* 13: children/childrenCount: 孩子节点的数组;

* 14: tag : 节点标签; 

#### cc.Component

* 1:所有的组件都扩展自cc.Component(类, 构造函数);

* 2:每个cc.Component组件实例都有个成员node,指向它关联节点的cc.Node;

* 3: name: 每一个cc.Component组件通过name属性可以获得节点的名字;

* 4: 组件实例入口函数:

     onLoad: 在组件加载的时候调用;

     start: 组件第一次激活前, 调用在第一次update之前;

     update(dt): 每次游戏刷新的时候调用,

     
     lateUpdate(dt): 在update之后调用;

     enabled:组件是否被启动; 

     onEnable: 组件被允许的时候调用;

     onDisable: 组件不被允许的时候调用;

#### 代码组件

* 1:每个代码组件实例都继承自cc.Component(构造函数),所以有一个node数据成员指向cc.Node;

* 2: cc.Class({...}) 定义导出了一个新的类的构造函数，它继承自cc.Component;

* 3: 当为每个节点添加组件的时候,会实例化(new)这个组件类，生成一个组件实例;(js语法new)

* 4: 当组件加载运行的时候，代码函数里面的this指向这个组件的实例;

* 5: 代码组件在挂载的时候扩展自cc.Component, 里面有个成员node会指向节点(cc.Node);

    所以在代码组件里面，可以使用this.node来访问这个组件实例说挂载的节点对象;

* 6: 代码里访问cc.Node总要属性;

#### cc.Node场景树相关方法

* 1: 代码中创建一个节点new cc.Node();

* 1:  addChild; 加一个子节点

* 2: removeFromParent/ removeAllChildren;

* 3:  setLocalZOrder/ 绘制顺序, 在下面的会绘制在屏幕的上面;

* 4: 遍历节点的子节点;

* 5: setPosition/getPosition, 

* 6: getChildByName/getChildByTag, getChildByIndex,

局部查找

    this.node.getChildByName();

全部查找

* 7: cc.find(): 方便，不通用, 消耗 


