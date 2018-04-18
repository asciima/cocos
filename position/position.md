### cc.Node空间坐标

#### cc.Vec2

* 1: cc.Vec2 二维向量坐标, 表结构{x: 120,  y: 120};    cc.v2(x, y) 创建一个二维向量 cc.p() 创建一个二外向量

* 2: cc.pSub: 向量相减

* 3: cc.pAdd: 向量相加;

* 4: cc.pLength: 向量长度;

#### cc.Size/cc.Rect

* 1: cc.Size: 包含宽度和高度信息的对象 {width: 100, height: 100};

* 2: new cc.Size(w, h), cc.size(w, h)创建一个 大小对象;

* 3: cc.Rect: 矩形对象 new cc.Rect(x, y, w, h); cc.rect(x, y, w, h); {x, y, width, height}

* 4: contains(Point): 点是否在矩形内;

* 5: intersects : 两个矩形是否相交;


#### creator坐标系

* 1: 世界(屏幕)坐标系;

* 2: 相对(节点)坐标系,两种相对节点原点的方式(1) 左下角为原点, (2) 锚点为原点(AR)

* 3: 节点坐标和屏幕坐标的相互转换; 我们到底使用哪个？通常情况下带AR;

* 4: 获取在父亲节点坐标系下(AR为原点)的节点包围盒;

* 5: 获取在世界坐标系下的节点包围盒;

* 6: 触摸事件对象世界坐标与节点坐标的转换;

