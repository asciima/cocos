### cc.AudioSource


* 1:AudioSource组件是音频源组件, 发出声音的源头;

* 2: AudioSource组件面板:

      clip: 声源的播放的音频对象: AudioClip, mp3, wav, ogg,

      volume: 音量大小, [0, 1]百分比

      mute: 是否静音;

      Loop: 是否循环播放;

      Play on Load: 是否在组件加载的时候播放;

      Preload: 是否预先加载;

### cc.AudioClip对象


* 1: 音频剪辑对象，支持的格式有mp3, wav, ogg

* 2:  可以在编辑器上手动关联,生成AudioCip对象;

* 3: 可以通过代码加载AudioCip;  (资源加载详细讲解);

### AudioSource代码使用


* 1: 代码中获得cc.AudioSource组件: 

        编辑器关联; 

        代码获取组件;

* 2: AudioSource 主要的方法:

    play(); 播放音频;

    stop(); 停止声音播放;

    pause(); 暂停声音播放;

    resume(); 恢复声音播放;

    rewind(); 重头开始播放;

    其它接口见文档;  

* 3: AudioSource代码主要属性:

   loop: 是否循环播放

   isPlaying: 是否正在播放; 

   mute: 是否静音;

   如果要在开始的时候设置某些属性，可以放到start函数里面;


