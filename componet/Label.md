### cc.Label

* 1:cc.Label是显示文字的组件;

* 2:cc.Label属性面板:
        
        String: 文本显示的内容;
        
        Horiznotal: 水平对齐的方式: 左 右 居中;
        
        Vertial: 上, 下, 居中, 字与行的排版
        
        Font Size: 字体大小;
        
        LineHeight: 每行的高度;
        
        OverFlow:文字排版: 
        
                None: 没有任何特性; Clamp: 截断; 
        
                Shank:自动缩放到节点大小;  Resize Height: 根据宽度自动折行;
        
        Font: ttf字库文件, 位图字体字库文件;
        
        Font Family: 字体家族,使用系统的哪种字库;
        
        Use System Font: 是否使用系统字体;

* 3: Label节点所在的锚点修改;

### 自定义字库

* 1: 准备好字体文件 .ttf矢量字库;

      使用矢量字体 , 优点: 灵活方便，缺点:字库文件占资源

* 2: 使用字体制作工具生成位图字体;

      使用位图字体;

* 3: 位图字体的优点与缺点:

     速度快，文件小;   支持的字符个数是有限的;

* 4: 自定义ttf字库与自定义位图字库: 个性化我们的字体,个性化系统没有的字库;

    自定义ttf字库，字符不限制，你这个字库里面有多少字符，就会支持, 灵活,占空间比较大
    位图字库, 字符的个数是有限制的，省空间

### 代码使用cc.Label

* 1: 代码中获取cc.Label组件;

* 2: 代码绑定cc.Label组件到编辑器;

* 3: 修改cc.Label的文字内容:  label.string = “xxxxxxxxxx”;

### RichText组件

* 1:  添加富文本组件;

* 2: 设置富文本的字符内容;
        
        <color=#0fffff>Text</color> 指定文字的颜色;
        
        <img src='cow1_1'/>   img标签,文本插入图片，图片要在指定的图集里面;
        
        u: 给文本加下划线
        
        i: 用斜体来渲染, b: 用粗体来渲染
        
        size: 指定字体渲染大小，大小值必须是一个整数 <size=30>enlarge me</size>
        
        outline: 设置文本的描边颜色和描边宽度 <outline color=red width=4>A label with outline</outline>

