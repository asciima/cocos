
        /**
        * 通用组件
        * ComFunc()全局调用方法
        *所有图片资源放在resourse目录下
        */

        function ComFunc(){

        }

        ComFunc.prototype.BtnSpriteUpdate=function(obj){   //Button按钮图片修改
            cc.loader.loadRes(obj.string,cc.SpriteAtlas,function(err,atlas){
                if (!err) {
                var frame1 = atlas.getSpriteFrame(obj.btnNormalSpriteFrame);
                obj.btn.normalSprite = frame1;
                var frame2 = atlas.getSpriteFrame(obj.btnPressSpriteFrame);
                obj.btn.pressedSprite = frame2;
                var frame3 = atlas.getSpriteFrame(obj.btnDisableSpriteFrame);
                obj.btn.disabledSprite = frame3;
                }else{
                    console.log(err);
                }
            });   
        }

        ComFunc.prototype.BtnSpriteFrameUpdate=function(obj){   //Button按钮图片修改
            cc.loader.loadRes(obj.string,cc.SpriteFrame,function(err,res){
                if (!err) {
                    obj.btn.normalSprite = res;
                    obj.btn.pressedSprite = res;
                    obj.btn.disabledSprite = res;
                }else{
                    console.log(err);
                }
            });   
        }


        ComFunc.prototype.SpriteAtlasUpdate=function(obj){   //图集精灵修改
            cc.loader.loadRes(obj.string,cc.SpriteAtlas,function(err,atlas){
                if (!err) {
                var frame = atlas.getSpriteFrame(obj.spriteFrame);
                obj.sprite.spriteFrame = frame;
                }else{
                    console.log(err);
                }
            });   
        }

        ComFunc.prototype.LoadPropItem = function(){    
            
            var urls = [];
            for (var i = 0; i < 5; i++) {
                var str = "";
                str = "propItem/PropItem_" + (i + 1);

                urls[i] = str;
            }
            urls[urls.length] = "propItem/PropItem_path";

            var self = this;
            window.propItemRes = null;
            cc.loader.loadResArray(urls, cc.SpriteAtlas, function (err, assets) {
                cc.log(assets,'所有道具图片资源');
                window.propItemRes = assets;
                
            });

            cc.loader.loadRes("PropList", function (err, txt) {
                cc.log(txt,'所有道具信息');
                window.PropItemPlist = txt;
            });
            window.AllCueRes = [];
            cc.loader.loadResDir("OtherImage/AllCue",cc.SpriteFrame,function (err, assets) {
                if(!err){
                    for(var i = 0;i < assets.length;i++){
                        window.AllCueRes.push(assets[i]);
                    }
                }
            });
        
            window.AllCueGrade = [];
            cc.loader.loadRes("UI/ModalLayer_1",cc.SpriteAtlas,function (err, assets) {
                if(!err){
                    for(var i = 0;i < 8;i++){
                        window.AllCueGrade.push(assets.getSpriteFrame('cue_grade_'+ i))
                    }
                }
            });
            
            window.AllRoomCard = [];
            cc.loader.loadResDir("OtherImage/GameTab/",cc.SpriteFrame,function (err, assets) {
                if(!err){
                    for(var i = 0;i < assets.length;i++){
                        window.AllRoomCard.push(assets[i]);
                    }
                }
            });

        }

        ComFunc.prototype.SpriteFrameUpdate=function(obj){   //普通精灵修改
            cc.loader.loadRes(obj.string,cc.SpriteFrame,function(err, spriteFrame){
                if (!err) {
                    // console.log('123');
                    obj.sprite.spriteFrame = spriteFrame;
                }
            });     
        }

        ComFunc.prototype.AddLayer=function(obj,scriptName,data){   //添加层

            cc.loader.loadRes(obj.string, (err, prefab)=>{
                if (!err) {
                    if(cc.director.getScene().getChildByName('Canvas').getChildByName(obj.name) == null){
                        var node = cc.instantiate(prefab);
                        node.setName(obj.name);
                        cc.director.getScene().getChildByName('Canvas').addChild(node);
                        node.setPosition(cc.p(0, 0)); 
                        if(scriptName && data){
                            node.getComponent(scriptName).init(data)                    
                        }
                    }
                }
            });  
        }

        ComFunc.prototype.TipLayer=function(string){   //通用提示框   

            cc.loader.loadRes("panel/TipModalLayer", (err, prefab)=>{
                if (!err) {
                    if(cc.director.getScene().getChildByName('Canvas').getChildByName("TipModalLayer") == null){
                        var node = cc.instantiate(prefab);
                        node.setName("TipModalLayer");
                        cc.director.getScene().getChildByName('Canvas').addChild(node);
                        node.setPosition(cc.p(0, 0)); 
                        node.getComponent('TipModalLayer').init(string)                    
                    }
                }
            });  
        }

        ComFunc.prototype.ShowPropName=function(propid){   //获取道具名称; 
            var strName = "KEY_PROP_" + propid + "_NAME";
            if(!PropItemPlist[strName]){
                var propInfo = UserData.GetPropInfo(propid);
                if(propInfo){
                    return propInfo.remark;
                }else{
                    return '未知物品';
                }
            }else{
                var name = PropItemPlist[strName]['zh-CN'];
                return name;
            }
        }

        ComFunc.prototype.ShowPropDec=function(propid){   //获取道具描述; 
            var strName = "KEY_PROP_" + propid + "_DEC";
            if(!PropItemPlist[strName]){
                return '';
            }else{
                var name = PropItemPlist[strName]['zh-CN'];
                return name;
            }
        }

        ComFunc.prototype.GetBatteryCellsByTime=function(timeValue){   //通用提示框   
            if (timeValue >= 0)
            {
                var cellCount = timeValue / (5 * 24 * 60 * 60);
                if (timeValue % (5 * 24 * 60 * 60) > 0)
                    cellCount++;
                return cellCount;
            }
            return 0;
        }

        ComFunc.prototype.GetBatteryCellsByEtc=function(etcCount)
        {
            if (etcCount >= 0)
            {
                var cellCount = etcCount / 20;
                if (etcCount % 20 > 0)
                    cellCount++;

                return cellCount;
            }

            return 0;
        }

        ComFunc.prototype.formatDate=function(date)      //格式化时间格式
        {
            date = new Date(date * 1000);
            var y=date.getFullYear();
            var m=date.getMonth()+1;
            var d=date.getDate();
            var h=date.getHours();
            var m1=date.getMinutes();
            var s=date.getSeconds();
            m = m<10?("0"+m):m;
            d = d<10?("0"+d):d;
            return y+"-"+m+"-"+d;
        }
        ComFunc.prototype.UserHead=function(obj){
            var resUrl=apiConfig.UserHead+UserData._curUserId;    //动态修改用户头像
                cc.loader.load({ url:resUrl, type: 'png' }, function (err, tex) {
                    cc.log('Should load a texture from RESTful API by specify the type: ' + (tex instanceof cc.Texture2D));
                    var frame = new cc.SpriteFrame(tex);
                    obj.sprite.spriteFrame= frame;
                });
        }
        ComFunc.prototype.addNewAnimation=function(cueId,skinId,parentNode){
            var that = this;
            var url = 'ainm/CueEffectDic/CueEffectDic_'+ cueId;
            var url2 = 'ainm/CueEffect/CueEffect_'+ cueId + '_' + skinId;
            console.log(url)
            var skinInfos;
            var skin;
            cc.loader.loadRes(url, function (err, altas) {
                if (err) {
                    //cc.error(err.message || err);
                    return;
                }
                skin = cueId + '_' + skinId;
                
                console.log(skin)
                var skins = Object.keys(altas);
                console.log('图集详细信息',altas)
                console.log('球杆皮肤信息',altas[skins[skinId]])
                skinInfos = altas[skins[skinId]];
                
            });
            cc.loader.loadRes(url2, cc.SpriteAtlas, function (err, altasObj) {
                if (err) {
                    //cc.error(err.message || err);
                    return;
                }
                console.log('皮肤对应的图集',altasObj)
                
                var effectCount = skinInfos.effectCount; //特效数量
                for(var i = 0; i < effectCount; i++ ){
                    console.log(skinInfos['effectFrameCount_' + i])
                    var lth = skinInfos['effectFrameCount_' + i];
                    var effect = skin + '_' + (i+1);
                    console.log(effect)
                    var imgs = [];
                    for(var j = 1; j <= lth; j++){
                        var str = 'CueEffect' + effect + ' (' + j + ')';
                        //console.log(str)
                        var a = altasObj.getSpriteFrame('CueEffect' + effect + ' (' + j + ')');               
                        imgs.push(a)
                    }
                    console.log('资源图片' + i,imgs)
                    var node = new cc.Node('effect');
                    var sp = node.addComponent(cc.Sprite);
                    sp.spriteFrame = imgs[0];
                
                    var animation = node.addComponent(cc.Animation);
                    
                    // frames 这是一个 SpriteFrame 的数组.
                    var clip = cc.AnimationClip.createWithSpriteFrames(imgs, 60);
                    clip.name = 'animate';
                    clip.speed = 0.5;
                    clip.wrapMode = cc.WrapMode.Loop;
                    clip.repeatCount = Infinity;
                    animation.addClip(clip);
                    animation.play('animate');
                    node.setPosition(skinInfos['effectPos_x_' + i], skinInfos['effectPos_y_' + i]);
                    //node.setContentSize(100, 100);
                    node.setScale(skinInfos['effectScale_' + i], skinInfos['effectScale_' + i]);
                    node.parent = parentNode;
                    console.log('结束',node)
                    
                } 
            })
        }
        var g_ComFunc= new ComFunc();
        window.ComFunc=g_ComFunc;
        window.CurrentLayerName = '';
