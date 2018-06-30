### cc.Button使用

* 1:添加按钮的方法

    (1)直接创建带Button组件的节点;

    (2) 先创建节点，再添加组件;

* 2:按钮组件, 按钮是游戏中最常用的组件, 点击然后响应事件;

* 3: 按钮的过渡效果:

    过渡: 普通状态, 鼠标滑动到物体上, 按下状态, 禁用状态

    (1)没有过渡，只有响应事件;

    (2)颜色过渡, 过渡效果中使用颜色;

    (3)精灵过渡，使用图片过渡;

    (4)缩放过渡, 选项，在disable的时候是否置灰;

* 4: 按钮禁用;

* 5: 按钮添加响应事件 --> 节点-->组件 --> 代码的函数;

* 6: 按钮传递自定义参数; ---> 字符串对象;

* 7: Button响应这个触摸点击，所以Button所挂的这个节点，一定要有大小,如果你向大小(0, 0)的节点上，挂一个Button,这个是无法响应点击事件;

### 代码使用cc.Button

* 1: 代码添加/获取cc.Button组件;

* 2: 代码里面添加按钮的响应事件;

* 3: 代码触发按钮指定的回掉函数;

* 4: Component.EventHandler
        var eventHandler = new cc.Component.EventHandler();

        eventHandler.target = newTarget;

        eventHandler.component = "MainMenu";

        eventHandler.handler = "OnClick";     

        eventHandler.customEventData = "my data";

        eventHandler.emit(["param1", "param2", ....]);


