#### 主动拉起转发，进入选择通讯录界面。    
    
    ShareFriend: function () {
            var self=this;
            var userName = GameSocket._curUserInfo.username; //用户昵称
            var userId = GameSocket._curUserInfo.userid.toString(); //用户id
            var serverName = GameSocket._curServerInfo.servername; //房间名称
            var roomId = GameSocket._curMilinfo.m_uRoom; //房间id
            var tableId = GameSocket._curMilinfo.m_uTable; //桌子id
            var seatId = GameSocket._curUserSeat; //座位id

            //邀请好友进入房间
            var shareImgUrl = 'https://img.52mvp.com/shr_pool/wx_img/201805/share_friend.jpg';
            if (cc.sys.isMobile && typeof (wx) !== "undefined") { //小游戏移动设备环境下

                wx.shareAppMessage({
                    title: '我发现了一个很好玩的小游戏，赶紧一起来台球帝国打台球吧~',
                    imageUrl: shareImgUrl,
                    query: 'userId=' + userId + '&serverName=' + serverName + '&roomId=' + roomId + '&tableId=' + tableId + '&seatId=' + seatId,
                    success: function (res) {
                        console.log('分享成功', res)
                        // 转发成功
                        wx.showToast({
                            title: '分享成功',
                        })
                        self.node.getComponent("CloseModalLayer").animateAndDestroy();
                    },
                    fail: function (res) {
                        console.log('分享失败', res)
                        // 转发失败
                    }
                })
            }
        },



