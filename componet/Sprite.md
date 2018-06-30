#### cc.Sprite

* 1: 游戏中显示一个图片，通常我们把这个叫做”精灵” sprite

* 2: cocos creator如果需要显示一个图片，那么需要在节点上挂一个精灵组件,为这个组件指定要显示的图片(SpriteFrame)

* 3: 显示一个图片的步骤:

     (1) 创建一个节点;

     (2) 添加一个组件;

     (3) 要显示的图片(SpriteFrame)拖动到SpriteFrame;

     (4) 配置图片的SIZE_MODE:  

             a: CUSTOM 大小和CCNode的大小一致;

             b: RAW 原始的图片大小;

             c:  TRIMMED 大小为原始图片大小, 显示的内容是裁剪掉透明像素后的图片;

     (5) trim: 是否裁剪掉 图片的透明区域, 如果勾选，就会把完全透明的行和列裁掉, 做帧动画的时候，我们一般是用原始大小不去透明度,动画，不至于抖动;

* 4: 精灵更换spriteFame;

* 5: 快捷创建带精灵组件的节点;

#### 图片模式

* 1:  simple: 精灵最普通的模式, 选择该模式后,图片将缩放到指定的大小;

* 2:  Tiled: 平铺模式, 图片以平铺的模式，铺地板砖的模式，铺到目标大小上;

* 3:  Slice: 九宫格模式，指定拉伸区域;

<image src="/img/slice.png">

* 4:  Filled: 设置填充的方式(圆，矩形)，可以使用比例来裁剪显示图片(只显示的比例);

#### 九宫格的使用

* 1:  指定拉伸区域, 让图片在拉伸的时候某些区域不会改变;

     比如圆角,聊天气泡等

* 2:  九宫格能省图片资源, (对话框);

* 3:  编辑九宫格,来制定缩放区域;

* 4: 体会对话框背景的九宫拉伸;

#### Filled模式


* 1:  配置Filled模式

* 2: 配置Filled模式, 设置为Radius参数;

* 3: 配置Radius的参数模式, 
            中心: 位置坐标(0, 1小数), (0, 0)左下脚, (1, 1) 右上角 (0.5, 0.5) 中心点

           Fill Start 开始的位置: 0 ~1, 右边中心点开始，逆时针走 
           
           Fill Range: 填充总量(0, 1]

           FillRange为正，那么就是逆时针，如果为负，那么就是顺时针;

* 4: 个性化时间进度条案例;

* 5: 游戏中道具的时间进度显示都可以;
